---
title: "I've killed my Windows install (installing Ubuntu)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ol_smokey on 2007-06-13
Hi Guys,

Well that didn't go to plan.
I did a guided install after I partitioned my hard drive due to a previous problem I was having in XP. The XP install was fine after the re-partitioning and so I continued with a Guided install on the new partition.
Ubuntu install completed within 25 mins and all appeared to go OK so I re-booted to make sure everything was ok.

It wasn't - I got a "no system error" before I got to GRUB.
I'm in a Live CD session now and can see all of the windows files are still there and intact and I can see all of the new Ubuntu files.

Is there any way of getting this back?

Any help appreciated

smokey

---

### Post by burnt water on 2007-06-13
> **ol_smokey said:**
> Hi Guys,

Well that didn't go to plan.
I did a guided install after I partitioned my hard drive due to a previous problem I was having in XP. The XP install was fine after the re-partitioning and so I continued with a Guided install on the new partition.
Ubuntu install completed within 25 mins and all appeared to go OK so I re-booted to make sure everything was ok.

It wasn't - I got a "no system error" before I got to GRUB.
I'm in a Live CD session now and can see all of the windows files are still there and intact and I can see all of the new Ubuntu files.

Is there any way of getting this back?

Any help appreciated

smokey


The problem may lie in your boot.ini/GRUB or your system 32(though that might bring up a more specific error)

---

### Post by ol_smokey on 2007-06-13
Thanks for the quick reply but could you give me some more details of where and what I'm looking for, I'm probably going to need a bit of hand-holding with this.

Ta
smokey

---

### Post by ol_smokey on 2007-06-13
OK found my Boot.ini and it looks like this:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Does that look right?

---

### Post by Fidelio on 2007-06-13
I could be wrong, but I'd say that if you get a 'no system' error you have a problem with your mbr. I had a similar thing when I was mucking about with ubuntu, and I used my windows XP CD to repair the mbr. I can't remember the exact command. I think it was fixmbr. Anyway, It worked for me getting windows up again, but I still had to reinstall ubuntu. It's worth trying if nothing else works.

---

### Post by ol_smokey on 2007-06-13
Just been having a browse through the archives and for boot problems people have been recommending SuperGrub - could this be my salvation?

---

### Post by STREETURCHINE on 2007-06-13
super grub is pretty good i would give it a go .i have used it in the past.

---

### Post by gauravp55 on 2007-06-13
If you wanna fix your mbr and u don't have the xp cd u could use a windows 98 boot disk. Go to [http://www.bootdisk.com]("http://www.bootdisk.com") and download Windows 98 SE OEM Bootdisk. Install it on a formatted floppy disk and boot using that disk.

You'll get 3 options. Choose Option 2 (without CD support) and then you'll get the prompt

A:>

You need to type

A:>fdisk /mbr

And that should do it for you.. Reboot your pc and you'll boot into windows right away.. But then you'll lose GRUB of course and you'll need to re-install in case you still wish to access your ubuntu partitions.

---

### Post by ol_smokey on 2007-06-17
OK guys, I've managed to fix this now. I erased the partition that I'd try to install Ubuntu on and resized the XP partition to extend to the whole drive and then all I had to do was go in to GPARTED and reset the BOOT flag.
No FIXMBR required at all.
When I rebooted it didn't throw me into GRUB which makes me think that the original problem lies there rather than with UBUNTU.

Thanks for all the replies and advice.

---

