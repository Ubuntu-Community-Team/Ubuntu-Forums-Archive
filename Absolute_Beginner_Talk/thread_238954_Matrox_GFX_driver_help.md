---
title: "Matrox GFX driver help"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by mgscox on 2006-08-18
Please help a linux n00b :)

I have a matrox 128Mb Parhelia PCI card in this box. Followed the instructions from "Help" to enable the 3D processing, which didn't work (tried both the ATI and NVIDA drivers as I'm not sure what Matrox is based on). Downloaded and subo'd the v1.4.4 Matrox Linux drivers from their support site, which fell over in compilation as the "/lib/modules/2.6.15-26-386/build" directory didn't exist even though I didn't spot any other errors in the log file.

Any pointers on what to try appreciated! Many thanx, build log file follows....

```
Using kernel headers in /lib/modules/2.6.15-26-386/build/include for kernel version 2.6.x
making all in /parhelia...
make[1]: Entering directory `/home/user/matrox/matroxdriver-/kernel/src/parhelia'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/user/matrox/matroxdriver-/kernel/src/parhelia'
making all in /mtxvxd...
make[1]: Entering directory `/home/user/matrox/matroxdriver-/kernel/src/mtxvxd'
gcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxCpu.c -o MtxCpu.ogcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxCs.c -o MtxCs.o
gcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxIo.c -o MtxIo.o
gcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxMem.c -o MtxMem.oMtxMem.c: In function ‘memFileAlloc’:
MtxMem.c:79: warning: passing argument 2 of ‘ClientMemAlloc’ makes integer from pointer without a cast
gcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxPci.c -o MtxPci.ogcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxMap.c -o MtxMap.ogcc   -DMEMORY_STATS=0  -DOS_LINUX -D__KERNEL__  -O2 -fomit-frame-pointer -finline-functions  -DMODULE -I/home/user/matrox/matroxdriver-/kernel/src/../include -I/home/user/matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/user/matrox/matroxdriver-/kernel/src -I/home/user/matrox/matroxdriver-/kernel/src/parhelia -I/home/user/matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.15-26-386/build/include -I/lib/modules/2.6.15-26-386/build/include/asm/mach-default  -D__NO_VERSION__ -c MtxDbg.c -o MtxDbg.old -r MtxCpu.o MtxCs.o MtxIo.o MtxMem.o MtxPci.o MtxMap.o MtxDbg.o -o mtxvxd.o
make[1]: Leaving directory `/home/user/matrox/matroxdriver-/kernel/src/mtxvxd'
make -C /lib/modules/2.6.15-26-386/build M=/home/user/matrox/matroxdriver-/kernel/src modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

---

