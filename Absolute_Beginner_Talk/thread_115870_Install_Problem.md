---
title: "Install Problem"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by Uncle Spellbinder on 2006-01-11
Hi, all. I hope you can help. I'm on my wife's computer right now so I can post here.  I used Fedor Core 4 several months ago and didn't really like it. On recommendations from a couple friends at work, and another forum, I thought I'd install Ubuntu 5.10 after using it at a friend's house for a couple weeks. I just tried to install Ubuntu 5.10. I've gone through the installation to the point where  the install disc ejected and the cpu rebooted. Using Gateway DX200 S, Intel Pentium 4. This was on the screen after the reboot, and I could go no further....

[i]Bootimg 'ubuntu, kernel 2.6.12.9.380
root (hd1,0)
File system type is ext2fs, partition type 0x83
kernel  /boot/vmlinvz-1.6.19-9-386 root= /dev/sdb1 ro quiet splash
[linux-intro A )x1f194000, 0x46561c bytes]
savedefault 
boot
incompressing linux... ok, booting the kernel
loading, please wait...
ALERT! /dev/sdb1 does not exist, dropping to a shell!

BusyBox v1.00-pre10 (Debian 20040623-1ununtu22 built in shell (ash)

Enter 'help' for a list of built in commands.

/bin/sh: can't access tty: job control turned off
# [4294683.97900] sdb: assuming drive cache: write through
[4294683.98000] sdb: assuming drive cache: write through

# _[/i]

Thanks in advance!

---

### Post by Uncle Spellbinder on 2006-01-11
Anyone? :confused:

---

### Post by jorn on 2006-01-11
Hello!
I'm not a big troubleshooter, but maybe I can give you some hints.
It says it cannot find /dev/sdb1 and it's booting from (hd1,0).
What drive and partition did you install on?
Regards - Jorn

---

### Post by Nightwind on 2006-01-11
[QUOTE=Uncle Spellbinder]Anyone? :confused:[/QUOTE]
Did you have an option to format and partition the hard drive or had you already done that?

---

### Post by Uncle Spellbinder on 2006-01-11
I've come to the assumption that I'm not that bright. :rolleyes: 

I revently purchased an externat hard drive. part of the Ubuntu install occurred there. I've reformatted and disconnected the external hard drive. I've got 18 gigs of unallocated space on my CPU. I'll try again. Sorry. We'll see what happens now! ;)

---

### Post by Nightwind on 2006-01-11
[QUOTE=Uncle Spellbinder]I've come to the assumption that I'm not that bright. :rolleyes: 

I revently purchased an externat hard drive. part of the Ubuntu install occurred there. I've reformatted and disconnected the external hard drive. I've got 18 gigs of unallocated space on my CPU. I'll try again. Sorry. We'll see what happens now! ;)[/QUOTE]
Hi
It's not a matter of you not being bright, lots of folks don't know exactly how to do things on computers as well as other things. There is nothing wrong with that! :o)
I would disconnect the external hard drive, put the Ubuntu CD in reboot the computer and follow the on screen instructions. I, personally fdisk and reformat all hard drives before I do any type of installation.

---

### Post by Uncle Spellbinder on 2006-01-11
OK, so I got it past the reboot. But now, while loading during second part of install, it stops at "Starting Hotplug Subsystem".

---

### Post by GreyFox503 on 2006-01-11
As a temporary fix, you can press Ctrl + C during boot to cancel an action if it gets stuck there.

I think hotplug detects and mounts external drives like USB flash memory.

Once you've gotten it to boot, then you can work on fixing it.

EDIT:  I just thought you might try booting w/o the external drive plugged in.

---

### Post by Uncle Spellbinder on 2006-01-11
[QUOTE=GreyFox503]As a temporary fix, you can press Ctrl + C during boot to cancel an action if it gets stuck there.

I think hotplug detects and mounts external drives like USB flash memory.

Once you've gotten it to boot, then you can work on fixing it.

EDIT:  I just thought you might try booting w/o the external drive plugged in.[/QUOTE]


Thanks! I'l give your second suggestion a try first. I'm currently stuck in the middle of a  Window$ update I shouldn't disturb. Thanks again. :smile:

---

### Post by Uncle Spellbinder on 2006-01-11
No luck. I tried booting with the external hard drive unplugged, then tried again (external hard drive still unplugged) and pressed  *ctrl - c* at the point when it got "stuck". It still went to the black screen with everything listed that loaded to that point stopping at "Starting Hotplug Subsystem". All said *[OK]* except the hotplug entry. It was blank with a blinking underscore.

---

### Post by Uncle Spellbinder on 2006-01-11
I just tried unplugging *everything* usb. Still no luck

---

