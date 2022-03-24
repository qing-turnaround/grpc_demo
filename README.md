## Grpc初探

1. 编写一个[proto文件](./grpc.proto)
2. 使用工具生成grpc代码 
3. protoc -I. --go_out=plugins=grpc:. ./*.proto
4. .pb.go里面的一个类型为byte数组的变量，是对proto文件的整体描述，包含proto文件名，引用内容，包名定义的服务等等内容。
> 比如var file_grpc_proto_rawDesc = []byte{
>0x0a, 0x0a, 0x67, 0x72, 0x70 ...
> }
5. 每一个`message`都有一个对应的Descriptor方法，用来寻找消息体定义的字段。因为服务端和客户端共用一份proto文件，
所以所生成的pb.go里面包含构建服务端和客户端的代码，以及所对应的rpc服务