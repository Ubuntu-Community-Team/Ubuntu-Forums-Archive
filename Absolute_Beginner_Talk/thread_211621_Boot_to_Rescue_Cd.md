---
title: "Boot to Rescue Cd"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by twistedchick on 2006-07-08
At bootup the system hangs for a bit prior to going to the login screen with a list of things that failed:

Starting PCMCIA Services...........Fail
Reading Desktop Files..............Fail

After putting in the rescue cd in the terminal I typed:

```
sudo reboot
```

however when it started up again the system specifies the same failures as listed above.  I'm trying to fix my lil blinky box w/the advice listed here:

[HTML]http://www.ubuntuforums.org/showthread.php?t=186964&highlight=reboot+rescue+cd[/HTML]

but I figure it's not automatically booting from the rescue c.d. because of the listed failures - if that is the case any advice as to how I can boot directly from the cd so I can take advantage of the PCMCIA workaround??

---

### Post by djsroknrol on 2006-07-08
Are you using a laptop?....Laptops have problems at times with pcmcia services..you can turn them off at boot from within GRUB and see if that doesn't help...I'm not at my home computer right now, but I'll post again with the directions in a while...

---

### Post by djsroknrol on 2006-07-08
Ok..try one of these in your menu.lst for GRUB..

nolapic (disables support for local apic) 
acpi=nopci (disables PCI resource control of the ACPI subsystem) 
acpi=off (completely disables ACPI, should always work) 

So, it should look something like this:


title  Ubuntu, kernel 2.6.15-25-386
root   (hd0,0)
kernel	/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1ro quiet splash *******
initrd	/boot/initrd.img-2.6.15-25-386
savedefault
boot

Where "*****" is one of the above....acpi=off works well on my laptop

---

