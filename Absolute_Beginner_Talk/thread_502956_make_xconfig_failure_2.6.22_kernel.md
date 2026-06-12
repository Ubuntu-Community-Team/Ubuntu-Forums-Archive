---
title: "make xconfig failure 2.6.22 kernel"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by bountonw on 2007-07-17
I am trying to solve my sound problems on a [different thread.]("http://ubuntuforums.org/showthread.php?t=500680").  It was suggested there that

> Your sound chip the ALC861VD is supported in the 2.6.21 linux kernel 

My current kernel is
```
2.6.20-16-generic
```

I tried to install a new kernel following the directions [here.]("http://ubuntuforums.org/showthread.php?t=311158&")

I found the log [here]("http://l4x.org/k/?d=31810") very helpful in knowing how to answer each step of the kernel installation.

But, when I did a make xconfig I get the following message

```
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Then a qconf screen comes up. 

What do I do next?  I am afraid to shut the computer off.

---

### Post by AlexenderReez on 2007-07-17
if you just want to install kernel 2.6.22* ,i suggest you to install from gutsy repo....enable just to install kernel then disable back..it is even better than compile by your own,reduce a lot of risk...current kernel --->

> 2.6.22-8-generic (#1 SMP Thu Jul 12 15:59:45 GMT 2007)

---

### Post by bountonw on 2007-07-17
Sorry, I don't get it.  I don't see that kernel on the Synaptic Package Manager.  Anyway, I have done everything else on the installation instructions.  So if possible, I want to follow through with what I have done.  I just don't know where to go from here.

---

### Post by bountonw on 2007-07-17
I am trying the next two steps.  The installation guide says that it will take 1-3 hours.
Code:

```
make-kpkg clean
```


```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```

I'll come back in a few hours to see what happened.

---

### Post by bountonw on 2007-07-17
It failed.  I did the last step

```
cd .. && dpkg -i linux*.deb
```  There was an error message, but I didn't copy it.

I then rebooted and I still have the old kernel.  I need help ubgrading my kernel.  I will come back after work and try again.  Any suggestions would be helpful.  

1.  How to get the gutsy repository as suggested above, 
2.  Are there other pages that explain how to upgrade the kernel.

If not, I will try what I did last night, and try to be more careful.  I may have made a mistake somewhere.

---

### Post by bountonw on 2007-07-18
I tried to follow all of the steps.  I am quite sure that I didn't miss anything.  Took an hour to answer all of the y's and n's etc.

Anyway, I get the following error after make xconfig

```
make xconfig
  CHECK   qt
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Help would really be appreciated.  I need to upgrade the kernel so that I can get my sound to work.

---

### Post by Seisen on 2007-07-18
Have you tried using the "make menuconfig"? Also this appears in the thread.

> Q. When I 'make xconfig', this error appears, but it doesn't seem to harm the installation.
Quote:
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
A. This is harmless. It simply appears because you have your wacom devices enabled in xorg.conf. If you don't want to see that error see here.
--------------------------------------------------------------

---

### Post by bountonw on 2007-07-18
I tried menuconfig.  I didn't know what to do so I ran

```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```

After an hour or so I got the following error.

```
drivers/media/video/saa7114.c: In function ‘saa7114_detect_client’:
drivers/media/video/saa7114.c:827: internal compiler error: in calc_dfs_tree, at dominance.c:376
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[4]: *** [drivers/media/video/saa7114.o] Error 1
make[3]: *** [drivers/media/video] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22'
make: *** [debian/stamp-build-kernel] Error 2
root@eliyah01:/usr/src/linux# 

```

I then did

```
cd .. && dpkg -i linux*.deb
```

and got

```
Setting up linux-image-2.6.22.1 (686) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22.1
find: /lib/firmware/2.6.22.1: No such file or directory
find: /lib/firmware/2.6.22.1: No such file or directory
find: /lib/firmware/2.6.22.1: No such file or directory
find: /lib/firmware/2.6.22.1: No such file or directory
find: /lib/firmware/2.6.22.1: No such file or directory
find: /lib/firmware/2.6.22.1: No such file or directory
Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22.1
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

I will reboot and see if I have a new kernel or not.

---

### Post by bountonw on 2007-07-18
It works.  I have a new kernel now.  Thank you.

---

