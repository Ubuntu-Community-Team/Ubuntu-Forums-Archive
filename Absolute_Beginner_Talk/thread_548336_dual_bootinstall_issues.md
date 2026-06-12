---
title: "dual boot/install issues"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by andrewbadera on 2007-09-11
OK, I've now spent four days bouncing back and forth, trying to get Ubuntu and XP both dual booting, and XP running in VM from the physical disk. Despite various round tips of mixes of fixmbr and xp boot settings and grub setup and reinstallation of both OSes in various orders on various partitions, I have yet to succeed.

my current configuration, I ran the ubuntu livecd, used gparted to setup:

128mb unalloc
4gb swap
250gb ext3
125gb ntfs

I then ran an xp installation, which installed to /dev/sda3, the ntfs partition. previously I'd tried installing ubuntu with /boot on /dev/sda0 but then xp wouldn't install, so this time, no ubuntu yet.

do I need to take any particular steps at this point to avoid thrashing the xp install, getting xp and ubuntu dual booting, and getting vmware server running that same xp install?

---

### Post by mlentink on 2007-09-11
Always, always install Windows first. Then follow the [Wiki]("https://help.ubuntu.com/community/WindowsDualBoot") to install ubuntu. 
When both of them run and boot flawlessly, you can install VM and prceed form there

---

### Post by RonP on 2007-09-11
i installed xp after a ubuntu installation im a newb and the grub config was easy going

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by andrewbadera on 2007-09-11
thanks all, I'll take a look after work tonight.

---

### Post by logos34 on 2007-09-11
> **andrewbadera said:**
> I then ran an xp installation, which installed to /dev/sda3, the ntfs partition. previously I'd tried installing ubuntu with /boot on /dev/sda0 but then xp wouldn't install, so this time, no ubuntu yet.

do I need to take any particular steps at this point to avoid thrashing the xp install, getting xp and ubuntu dual booting, and getting vmware server running that same xp install?

Why a separate xp install on a partition if you're going to run it inside VMWare server?  You can't run it that way...you have to install it again* inside* vm server by creating a virtual machine.

---

### Post by mlentink on 2007-09-11
> **logos34 said:**
> You can't run it that way...you have to install it again* inside* vm server by creating a virtual machine.

Sure, which you can do with VM Convert. But that would still give the OP the original Windows partition to work with. Many people (I am one) need Windows at work.

---

### Post by andrewbadera on 2007-09-11
> **mlentink said:**
> Sure, which you can do with VM Convert. But that would still give the OP the original Windows partition to work with. Many people (I am one) need Windows at work.

EXACTLY.

I'm a .NET engineer and consultant. Day job, night job, .NET currently owns me. Which means Visual Studio has me by the short hairs. (Yes, I know there are alternatives, no, they're not a real option for me, neither is Mono.)

I don't care how good VMWare is ... I know how flakey Visual Studio is, and if I can't get my work done, I don't need the extra variable of VM possibly making troubleshooting difficult.

Plus there's an outside chance I might want to run a game on this box requiring XP.

---

### Post by andrewbadera on 2007-09-11
ok, both ubuntu and xp are happily dual booting ... now, how do I set up vmware server to utilize that existing ntfs partition and xp installation, while maintaining dual bootability?

thanks all for your input!

---

### Post by Jason.TJ.Johnson on 2007-09-11
[http://ubuntuforums.org/showthread.php?t=380699&highlight=howto+vmware](http://ubuntuforums.org/showthread.php?t=380699&highlight=howto+vmware)

---

### Post by armandh on 2007-09-11
rather than put in a partition(s) for ubuntu leave unallocated and select the "use unallocated space" setup option

I later resized and added a fat 32 partition for files to be used by either OS

---

