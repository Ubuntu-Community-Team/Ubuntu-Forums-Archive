---
title: "Problem burning live ISO to CD"
date: 2005-05-10
forum: Apple PPC Users
---

### Post by dr_gonzo on 2005-05-10
Hey!

I thought I'd try out Ubuntu because I've heard such great things about it :)

Anyway, I'm falling at the first hurdle. I have downloaded the ISO from [http://mirror.switch.ch/ftp/mirror/ubuntu-cdimage/hoary/ubuntu-5.04-live-powerpc.iso](http://mirror.switch.ch/ftp/mirror/ubuntu-cdimage/hoary/ubuntu-5.04-live-powerpc.iso) and when I try to burn it to a CD, hdiutil seg faults. This is strange because I can successfully burn other ISOs from the internet. I have downloaded the ISO from other sources too but I keep on getting the same results.

The output from "hdiutil burn -verbose ubuntu-5.04-live-powerpc.iso" is the following. I'd really appreciate it if someone would tell me what I'm doing wrong. Thanks :)

burn: processing "ubuntu-5.04-live-powerpc.iso"
DIBackingStoreInstantiatorProbe: interface  0, score      100, CBSDBackingStore
DIBackingStoreInstantiatorProbe: interface  1, score    -1000, CHTTPBackingStore
DIBackingStoreInstantiatorProbe: interface  2, score    -1000, CRAMBackingStore
DIBackingStoreInstantiatorProbe: interface  3, score      100, CCarbonBackingStore
DIBackingStoreInstantiatorProbe: interface  4, score    -1000, CDevBackingStore
DIBackingStoreInstantiatorProbe: interface  5, score    -1000, CCURLBackingStore
DIBackingStoreInstantiatorProbe: selecting CBSDBackingStore
DIFileEncodingInstantiatorProbe: interface  0, score    -1000, CMacBinaryEncoding
DIFileEncodingInstantiatorProbe: interface  1, score    -1000, CAppleSingleEncoding
DIFileEncodingInstantiatorProbe: interface  2, score    -1000, CEncryptedEncoding
DIFileEncodingInstantiatorProbe: nothing to select.
DIFileEncodingInstantiatorProbe: interface  0, score    -1000, CUDIFEncoding
DIFileEncodingInstantiatorProbe: nothing to select.
DIFileEncodingInstantiatorProbe: interface  0, score    -1000, CSegmentedNDIFEncoding
DIFileEncodingInstantiatorProbe: interface  1, score    -1000, CSegmentedUDIFEncoding
DIFileEncodingInstantiatorProbe: interface  2, score    -1000, CSegmentedUDIFRawEncoding
DIFileEncodingInstantiatorProbe: nothing to select.
DIDiskImageInstantiatorProbe: interface  0, score        0, CDARTDiskImage
DIDiskImageInstantiatorProbe: interface  1, score        0, CDiskCopy42DiskImage
DIDiskImageInstantiatorProbe: interface  2, score    -1000, CNDIFDiskImage
DIDiskImageInstantiatorProbe: interface  3, score      100, CUDIFDiskImage
DIDiskImageInstantiatorProbe: interface  4, score      100, CRawDiskImage
DIDiskImageInstantiatorProbe: interface  5, score     -100, CShadowedDiskImage
DIDiskImageInstantiatorProbe: interface  6, score        0, CSparseDiskImage
DIDiskImageInstantiatorProbe: interface  7, score    -1000, CCFPlugInDiskImage
DIDiskImageInstantiatorProbe: selecting CUDIFDiskImage
DIDiskImageNewWithBackingStore: CUDIFDiskImage
hdiutil: DIDiskImageNewWithBackingStore: instantiator returned 0

*** malloc[438]: error for object 0x180ca00: Incorrect checksum for freed object - object was probably modified after being freed; break at szone_error
Bus error

---

### Post by dr_gonzo on 2005-05-10
Silly me. I read an other thread and I'm now burning the CD with FireStarter FX. So far so good!

BTW, why does hdiutil crash?

---

### Post by DJ_Max on 2005-05-10
[http://forums.macosxhints.com/showthread.php?t=38056&highlight=Disk+Utility+crash](http://forums.macosxhints.com/showthread.php?t=38056&highlight=Disk+Utility+crash)

---

