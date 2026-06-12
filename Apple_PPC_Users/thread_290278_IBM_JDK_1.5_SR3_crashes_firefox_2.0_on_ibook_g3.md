---
title: "IBM JDK 1.5 SR3 crashes firefox 2.0 on ibook g3"
date: 2006-11-01
forum: Apple PPC Users
---

### Post by gerghk on 2006-11-01
Hi,

I've followed the instructions from the ubuntu wiki at:
[https://help.ubuntu.com/community/Java#head-0948e66f605ec3c2af4f264c5cfc56f4175659eb](https://help.ubuntu.com/community/Java#head-0948e66f605ec3c2af4f264c5cfc56f4175659eb)

to install java on my iBook G3 running edgy

I installed the 1.5.0 JDK only, not the 1.4.2, the version I got off the IBM site is SR3.

I had libstdc++5 and libgtk1.2 installed before running make-jpkg on the tgz file, and that went fine.

After installing the .deb package, I even tried running the tic tac toe example applet, and that was fine.

I've also added the JITC_PROCESSOR_TYPE=6 line to /etc/environments and added the symbolic link for the plugin in ~/.mozilla/plugins.

My about:plugins output indicates the java plugin is enabled correctly too.

HOWEVER, when I actually try to run any jre site, including sun's test site on java.com, firefox crashes.

I also notice that after every crash it leaves a .dmp, .txt and .trc file in my home directory.

Anyone have any luck with a similar config?  Would those files in my home directory help identify the problem?

Thanks,
Greg

---

### Post by gerghk on 2006-11-01
this is what firefox outputs before crashing:

Unhandled exception
Type=Segmentation error vmState=0x0005ff07
J9Generic_Signal_Number=00000004 Signal_Number=0000000b Error_Value=00000000 Signal_Code=00000001
Handler1=0FABDB80 Handler2=0FA1F9E0
R0=0007FFF8 R1=3D0D4D40 R2=3D0DD950 R3=0F93E36A
R4=0F93E368 R5=00000010 R6=3D0D4F88 R7=7F7F0000
R8=FFFFFFC0 R9=FFFFFFE0 R10=00000004 R11=3D0D4B10
R12=28204422 R13=10027D5C R14=0FBDBD68 R15=1002F6D0
R16=2D587373 R17=10027824 R18=100275F8 R19=0FB58B20
R20=100EA128 R21=00000000 R22=0FBDBD68 R23=0F844990
R24=0F8BE370 R25=0F86D500 R26=00000000 R27=0F93E36A
R28=0F848344 R29=00000000 R30=3D0D4EF0 R31=0F8BCFBC
NIP=0FE84FEC MSR=0000D032 ORIG_GPR3=108AC000 CTR=00000000
LINK=0F751654 XER=20000000 CCR=2820446C MQ=00000000
TRAP=00000300 DAR=0F93E368 dsisr=40000000 RESULT=00000000
Module=/lib/libc.so.6
Module_base_address=0FE03000 Symbol=strlen
Symbol_address=0FE84FE0

Method_being_compiled=com/ibm/oti/vm/BootstrapClassLoader.loadClass(Ljava/lang/String;)Ljava/lang/Class;
Target=2_30_20060915_08260_bHdSMR (Linux 2.6.17-10-powerpc)
CPU=ppc (1 logical CPUs) (0x17836000 RAM)
JVMDUMP006I Processing Dump Event "gpf", detail "" - Please Wait.
JVMDUMP007I JVM Requesting System Dump using '/home/gerghk/core.20061031.221949.4248.dmp'
JVMDUMP010I System Dump written to /home/gerghk/core.20061031.221949.4248.dmp
JVMDUMP007I JVM Requesting Snap Dump using '/home/gerghk/Snap0001.20061031.221949.4248.trc'
JVMDUMP010I Snap Dump written to /home/gerghk/Snap0001.20061031.221949.4248.trc
JVMDUMP007I JVM Requesting Java Dump using '/home/gerghk/javacore.20061031.221949.4248.txt'
JVMDUMP010I Java Dump written to /home/gerghk/javacore.20061031.221949.4248.txt
JVMDUMP013I Processed Dump Event "gpf", detail "".
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success

---

