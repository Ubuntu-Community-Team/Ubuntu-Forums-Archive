---
title: "Dual-booting:  Can I emulate my other Windows partition in Linux?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by sheilnaik on 2006-06-07
I know there are programs like Wine and VMWare that can emulate Windows programs in Linux, but since I'm dualbooting on my laptop (I have another 15GB Windows XP NTFS Partition), I figure it would make much more sense just to emulate that partition in Linux.

Is this possible?  It would prevent me from having to reinstall many of the programs that are already on my other partition.

Thanks for all your help Ubuntu Forum people.  You guys are great.

---

### Post by fluffington on 2006-06-07
I know VMWare is capable of booting an already installed operating system (I had an Ubuntu install that was bootable both on it's own and through VMWare a while back), but the configuration process was interesting to say the least.

I don't have that any more, though, and haven't for some time, so I can't really help with getting it set up.

---

### Post by sheilnaik on 2006-06-08
Thanks for your reply fluffington.  Anyone else with any ideas?

---

### Post by Mahmoud on 2006-06-08
[QUOTE=sheilnaik]I know there are programs like Wine and VMWare that can emulate Windows programs in Linux, but since I'm dualbooting on my laptop (I have another 15GB Windows XP NTFS Partition), I figure it would make much more sense just to emulate that partition in Linux.

Is this possible?  It would prevent me from having to reinstall many of the programs that are already on my other partition.

Thanks for all your help Ubuntu Forum people.  You guys are great.[/QUOTE]

what do you mean by "emulate a partition" ?
Do you want to mount this NTFS Partition and to be able to read/write files in Linux?

Reading NTFS is supported:
Tutorial to mount NTFS on boot:
[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28NTFS%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28NTFS%29)

Writing to NTFS partitions is still experimental, you can check this topic: [http://www.ubuntuforums.org/showthread.php?t=142481&highlight=NTFS+write](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=NTFS+write)

As for running these programs in Linux, you will either have to run them through WINE (and they might not work correctly) or Windows VM.

---

### Post by sheilnaik on 2006-06-08
Sorry, maybe I didn't make myself clear.  I want to be able to use Windows programs (the same way that Wine works), but I want to basically have it run the same Windows that's on my other Windows partition.  I don't just want to access the files on that partition...I want to actually run that Windows environment.

---

### Post by methosb on 2006-06-10
I would also like to know this. I just want to be able to run my windows that is already installed on a different partition in linux in the same way one runs a virtual machine in linux

---

### Post by Fred Doolie on 2006-06-10
VMware does let you assign a partition as the hard drive for the virtual system. You *might* be able to set up a virtual computer and tell it that your windows partition is the hard drive for that system but I don't think it will work right. It would be like removing your hard drive and plugging it into somebody else's computer. Different hardware and such. Would it boot up? I don't know. The VMware emulated "hardware" is very lame. Crap graphics card and sound. Your Win might boot but the plug-and-play might undo all your drivers and maybe bugger up your windows system.

EDIT: You've got me wondering. Rather than risk my Winblow partition I'm going to simulate it. When I installed my Winslows system I made a Ghost image for quick reinstalling (saved me a TON of time). I'm going to create a virtual system and restore my Ghosted Winpoop into it. In effect I will be booting my "real" Windoze system into VMWare's simulated computer. Stay tuned.

EDIT: Well, in the words of Big Jim McBob and BillySaul Huroc, "That blowed up REAL good!"
It started to boot and then CRASH Blue Screen Of Death. Guess you can't boot an established Windows system into VMWare.

---

### Post by jamesrw on 2006-06-16
hmmmmmm..... it'd really be nice, does it work the other way around? say im in windows and dont want to reboot???

---

### Post by firetux on 2006-06-16
Using google (what you probably didn't do) I found these:

[http://www.vmware.com/support/ws45/doc/disks_instraw_ws.html](http://www.vmware.com/support/ws45/doc/disks_instraw_ws.html)
[http://www.vmware.com/support/ws45/doc/disks_2kmultiboot_ws.html#1046341](http://www.vmware.com/support/ws45/doc/disks_2kmultiboot_ws.html#1046341)
[http://www.vmware.com/support/ws45/doc/disks_dualmult_ws.html#1046324](http://www.vmware.com/support/ws45/doc/disks_dualmult_ws.html#1046324)

(there are lots more of these but its your job to find them)(the basis of computer knowledge is searching, reading, googling, reading, searching, did I mention reading already?)

It appears to be possible but not recommended. You will be booting into windows both native and virtual. This way you will be using different hardware.(vmware emulates all hardware, it _doesn't_ use the real hardware in you box). You will be switching hardware all the time. Windows doesn't like this and will probably thow up a bsod.
In one of the links it is explained how to set up different hardware-profiles but its a pain.

---

