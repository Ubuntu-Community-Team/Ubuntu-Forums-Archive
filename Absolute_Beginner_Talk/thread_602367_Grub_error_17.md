---
title: "Grub error 17"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-11-04
Today I was in for a bit of a shock when my computer stopped booting with the message 'Grub error 17'. I hadn't seen that before, but deciding not to panic, I put the live-cd in the CDROM drive and booted. After browsing the internet a bit, I did the following:

opened a terminal.
sudo grub
find /boot/grub/stage1
root (hd0,5)  (because the previous line gave me this as a response).
setup (hd0)
quit

At this point I restarted. And with a little more joy in my heart than before I observed the grub startup menu (I run a dual boot system). I selected the ubuntu option and got another error 17. I selected the windows option and it booted fine. I therefore rebooted the live-cd again. I noticed in /boot/grub/menu.lst that all linux options said (hd0, 6) instead of (hd0, 5). I changed this on one entry and rebooted.

The grub menu appeared, I selected ubuntu and it started. However during the 'disk check' (something like 'fsck', but I always forget what it really is...) it said it needed to restart and it did. The second time it booted completely and normally. 

At this point it seems like I've fixed the setup. However, I am left with a couple of questions.

1. Yesterday, the last thing I did was use windows xp to play a game. I have however opened Partition magic at one point during that session. I didn't change anything so that shouldn't matter (imo). However, seeing my troubles this morning, I am wondering whether Partition magic did secretly do something. Does anyone happen to know this?

2. Even if partition magic did change something, how was it able to affect /boot/grub/menu.lst?

3. Is there any check I can do to see if my troubles in this area are really over?

---

### Post by forestpixie on 2007-11-04
have you checked out hermans [grub]("http://users.bigpond.net.au/hermanzone/") pages - there is one for [error]("http://users.bigpond.net.au/hermanzone/p15.htm#17") 17, but the whole things worth knowing about

---

### Post by meierfra on 2007-11-05
I would guess  partition magic deleted or moved a partition.  I don't think partition magic  could effect your "menu.lst". So I would  assume that before the incident ubuntu  was (hd0,6) ( that is the 7th partition on the first hard drive). Now it is (hd0,5), the sixth partition on the first hard drive. So something got moved or deleted.

Type  "sudo fdisk -l"   in a terminal. That will  list all your partition. It might help you to figure out what really happend.

---

