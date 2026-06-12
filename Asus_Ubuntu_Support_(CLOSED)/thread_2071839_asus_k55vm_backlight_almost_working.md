---
title: "asus k55vm backlight almost working"
date: 2012-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by zezadas on 2012-10-16
So my problem is Fn keys and back-light.
I already search and tried allot of fixes, but none solved the problem entirely.

I got asus-wmi/ asus-nb-wmi , module loaded and that creates a /sys/class/backlight/asus-nb-wmi/ and all those files inside

editing brightness file don't take effect on that session, but if i reboot my laptop it loads with the value of brightness file. (i'm thinking, maybe when i change brightness file value it stores on bios, then when i reboot it loads bios values, and then it load the modules and create the files...)

xev is not reporting fnkeys
running ubuntu 10.04 (backtrack 5 r3 64bits) kernel 3.6.1
asus k55vm sx045v intel hd 4000 / nvidia geforce gt 630 -> bumblebee installed
also modprobe asus-laptop, no such device

```
grub:
linux	/boot/vmlinuz-3.6.1 root=UUID=d1dff2b9-4f52-4db4-a351-f55bdba1b159 ro   text splash acpi_osi=Linux acpi_backlight=vendor nomodeset=1 nouveau.modeset=0
```

```
dmesg:(too long)
http://pastebin.com/ReMUX4Zd
```

```
ls /sys/class/backlight/asus-nb-wmi:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

```

as seen in dmesg when i press fn+f5/f6 i get :
```
[ 3738.958302] ACPI Error: Result stack is empty! State=ffff88018ed74000 (20120711/dswstate-98)
[ 3738.958313] ACPI Exception: AE_AML_NO_RETURN_VALUE, Missing or null operand (20120711/dsutils-646)
[ 3738.958318] ACPI Exception: AE_AML_NO_RETURN_VALUE, While creating Arg 0 (20120711/dsutils-763)
[ 3738.958324] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0.GCBL] (Node ffff8801a7461578), AE_AML_NO_RETURN_VALUE (20120711/psparse-536)
[ 3738.958334] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.SBRN] (Node ffff8801a74723e8), AE_AML_NO_RETURN_VALUE (20120711/psparse-536)
[ 3738.958342] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q0E] (Node ffff8801a7472410), AE_AML_NO_RETURN_VALUE (20120711/psparse-536)
[ 3740.471398] ACPI Error: Result stack is empty! State=ffff88018ed77000 (20120711/dswstate-98)
[ 3740.471408] ACPI Exception: AE_AML_NO_RETURN_VALUE, Missing or null operand (20120711/dsutils-646)
[ 3740.471414] ACPI Exception: AE_AML_NO_RETURN_VALUE, While creating Arg 0 (20120711/dsutils-763)
[ 3740.471419] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0.GCBL] (Node ffff8801a7461578), AE_AML_NO_RETURN_VALUE (20120711/psparse-536)
[ 3740.471430] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.SBRN] (Node ffff8801a74723e8), AE_AML_NO_RETURN_VALUE (20120711/psparse-536)
[ 3740.471438] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q0F] (Node ffff8801a7472438), AE_AML_NO_RETURN_VALUE (20120711/psparse-536)
```


I'm not a total noob so feel free to reply, so any idea how to fix? 
maybe copying and editing the init function that enables the brightness and paste in the  drivers...

---

### Post by yetiboy on 2012-10-17
Exactly the same problem with the same Asus k55vm laotop. I have googled the fix all day long and didn't find any working fix yet.

---

### Post by yetiboy on 2012-10-17
It seems that this thread is very close to our problem and to summarize, the fix is merged into Linux kernel 3.7-rc1 already. The thread mentioned some workarounds, but I haven't tried it yet. See more info:

[https://bbs.archlinux.org/viewtopic.php?id=147804](https://bbs.archlinux.org/viewtopic.php?id=147804)

---

### Post by zezadas on 2012-10-17
> **yetiboy said:**
> It seems that this thread is very close to our problem and to summarize, the fix is merged into Linux kernel 3.7-rc1 already. The thread mentioned some workarounds, but I haven't tried it yet. See more info:

[https://bbs.archlinux.org/viewtopic.php?id=147804](https://bbs.archlinux.org/viewtopic.php?id=147804)

 yesterday I installed 3.7, and backlight is working, but now is the nvidia drivers and the bumblebee, they do not work

---

### Post by yetiboy on 2012-10-17
> **zezadas said:**
> yesterday I installed 3.7, and backlight is working, but now is the nvidia drivers and the bumblebee, they do not work

Humm, looks weird, I too have bumbebee enabled and experience the same problem. By bmblebee design, nvidia driver will be disabled if we don't optirun applications.

By the way, is your touchpad right click working? I have to insmod as 'psmouse proto=imps' to get it working in a generic driver sense then lose the other functionalities without proto=imps, for e.g, I can't disable it by fn+f9 for now.

---

### Post by zezadas on 2012-10-18
> **yetiboy said:**
> Humm, looks weird, I too have bumbebee enabled and experience the same problem. By bmblebee design, nvidia driver will be disabled if we don't optirun applications.

By the way, is your touchpad right click working? I have to insmod as 'psmouse proto=imps' to get it working in a generic driver sense then lose the other functionalities without proto=imps, for e.g, I can't disable it by fn+f9 for now.



it doesnt work so good, you have to touch with two fingers at the same time. sometimes i click with to fingers and then i press down(phisical button)

i'm thinking in install touchegg or get something like the mac touchpad, disable the phisical button and the click's only work on that area, i dont know how to explain very well, but if you know mac, you know what i'm talking.


about bumblebee, i installed bumblebee on kold kernel (3.2.6) and then booted on 3.7, and reinstalled again on 3.7, what i'm getting... bbswitch is working and loading, nvidia is disabled, optirun gives me somthing like 
```

[  982.976363] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[  982.976419] [ERROR]Could not connect to bumblebee daemon - is it running?

```

bumblebee is not loading,

command bumblebeed start
```
[ 1043.103145] [ERROR]Module 'nvidia-current' is not found.
```

installing official nvidia( usr/src/nvidia-curretn-304.51 running command make module
```
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (	\
	echo >&2;							\
	echo >&2 "  ERROR: Kernel configuration is invalid.";		\
	echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\


and some error compiling with nv-linux.h

```

also already blacklist nouveau in modprobe and on grub nouveau.modeset=0 (that step on grub was important, kernel was rebooting on boot without this)-> some nouveau bug

---

### Post by yetiboy on 2012-10-19
well, I have manually complied kernel 3.6.2 from vanilla kernel.org, then I installed bumblebee, so far so good, all works well except backlight function keys. But when I compiled 3.7-rc1, my fn+f5,f6 doesn't work either. I guess I am waiting release of kernel 3.7 to see if backlight function keys is working.

---

### Post by zezadas on 2012-10-20
> **yetiboy said:**
> well, I have manually complied kernel 3.6.2 from vanilla kernel.org, then I installed bumblebee, so far so good, all works well except backlight function keys. But when I compiled 3.7-rc1, my fn+f5,f6 doesn't work either. I guess I am waiting release of kernel 3.7 to see if backlight function keys is working.

  mine are working check all asus modules, you have to enable acpi4asus, asus_wmi, etc... also disable nouveau, and enable intel graphics blablah HD  backlight is supported by nvidia drivers, the configs will be unde /sys/class/backligh/intel_SomethingIdontRemenber

---

### Post by yetiboy on 2012-10-22
I can't insmod asus-laptop, get a 'No such device' error. Maybe this cause the problem.  I also tried compile acpi4asus git repo and compile it locally, couldn't insmod asus-laptop either. Other modules are inserted successfully though.

---

### Post by zezadas on 2012-10-22
> **yetiboy said:**
> I can't insmod asus-laptop, get a 'No such device' error. Maybe this cause the problem.  I also tried compile acpi4asus git repo and compile it locally, couldn't insmod asus-laptop either. Other modules are inserted successfully though.

  compile kernel 3.7 with this config, put this under your kernel source path in file ".config"  [http://pastebin.com/XXz4U1uB](http://pastebin.com/XXz4U1uB)  this is my config for my k55vm  maybe nvidia/nouveau drivers are messing with it...

---

