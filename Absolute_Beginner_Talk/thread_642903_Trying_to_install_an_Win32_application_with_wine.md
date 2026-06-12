---
title: "Trying to install an Win32 application with wine"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Liquidfire- on 2007-12-17
Hey guys,

Thanks in advance for helping me, and solving the problem.


I've been playing along with some stuff in linux, and I succeeded in my first ever bash mount huurai.

anyways, The mount was an windows application. 

I tried installing it through wine [name of application]

It starts the install shield wizard, and then crashes with the following error.
[[IMG]http://img409.imageshack.us/img409/5931/screenshotue6.th.png[/IMG]](http://img409.imageshack.us/my.php?image=screenshotue6.png)



When I look at the terminal it gives the following output

> 
liquidfire@liquidfire-laptop:~/Azureus Downloads/EyeQ$ man -k wine
widl (1)             - Wine Interface Definition Language (IDL) compiler
wine (1)             - run Windows programs on Unix
winebuild (1)        - Wine dll builder
winedbg (1)          - Wine's debugger
winedump (1)         - A Wine DLL tool
wineg++ (1)          - Wine C and C++ MinGW Compatible Compiler
winegcc (1)          - Wine C and C++ MinGW Compatible Compiler
winemaker (1)        - generate a build infrastructure for compiling Windows programs on Unix
wineprefixcreate (1) - create or update the Wine configuration
wineserver (1)       - the Wine server
wmc (1)              - Wine Message Compiler
wrc (1)              - Wine Resource Compiler
liquidfire@liquidfire-laptop:~/Azureus Downloads/EyeQ$ dir
EYEQ.sfv
EYEQ.SPEED.READING.AND.BRAIN.ENHANCEMENT.TECHNOLOGY-JGTiSO.BIN
EYEQ.SPEED.READING.AND.BRAIN.ENHANCEMENT.TECHNOLOGY-JGTiSO.cue
EyeQ_v3.3_Speed_Reading_BETA_11B_&_serial.ISo-JGT.nfo
foo01.iso
liquidfire@liquidfire-laptop:~/Azureus Downloads/EyeQ$ cd /mnt/eyeQ/
liquidfire@liquidfire-laptop:/mnt/eyeQ$ dir
autorun.exe  data1.cab  data2.cab  ikernel.ex_  Multimedia  Setup.ini
autorun.inf  data1.hdr  eyeQ.ico   layout.bin   Setup.exe   Setup.inx
liquidfire@liquidfire-laptop:/mnt/eyeQ$ wine autorun.exe 
liquidfire@liquidfire-laptop:/mnt/eyeQ$ err:ole:CoGetClassObject no class object {91814ec0-b5f0-11d2-80b9-00104b1f6cea} could be created for context 0x4
wine setup.exe
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:ServerRpcChannelBuffer_GetDestCtx (0x34f5b0,0x34f5b4), stub!
err:ole:CoMarshalInterface Failed to write OBJREF header to stream, 0x80030070
err:rpc:I_RpcReceive we got fault packet with status 0x80030070
fixme:ole:NdrClearOutParameters (0x34eedc,0x10004212,0x34f160): stub
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004005
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004005
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004005
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004005
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004005
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
liquidfire@liquidfire-laptop:/mnt/eyeQ$ 



Any idea's thanks in advance :)

---

### Post by CatKiller on 2007-12-17
Not all applications work in Wine. Check the AppDB at [www.winehq.com](www.winehq.com) to see if your program is listed.

---

