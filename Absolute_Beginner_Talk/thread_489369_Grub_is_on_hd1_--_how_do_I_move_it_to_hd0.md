---
title: "Grub is on hd1 -- how do I move it to hd0?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-07-01
Grub is on hd1 -- how do I move it to hd0?

I have 2 sata hard drives (hd0 and hd1).

Ubuntu Feisty Fawn is on /dev/sda5 and Windows XP is on /dev/sda1.

When I tried to remove hd1, Ubuntu would no longer boot -- all that appeared on the screen was "GRUB".
So, I think the issue is that Grub is on hd1 from an previous Ubuntu install.

I want to replace hd1 but since Grub is on it my system won't boot if removed.

How do I install Grub on hd0 and keep my Ubuntu on /dev/sda6 and Windows XP on /dev/sda1?

Thanks

Carl

---

### Post by overdrank on 2007-07-01
> **cwmoser said:**
> Grub is on hd1 -- how do I move it to hd0?

I have 2 sata hard drives (hd0 and hd1).

Ubuntu Feisty Fawn is on /dev/sda5 and Windows XP is on /dev/sda1.

When I tried to remove hd1, Ubuntu would no longer boot -- all that appeared on the screen was "GRUB".
So, I think the issue is that Grub is on hd1 from an previous Ubuntu install.

I want to replace hd1 but since Grub is on it my system won't boot if removed.

How do I install Grub on hd0 and keep my Ubuntu on /dev/sda6 and Windows XP on /dev/sda1?

Thanks

Carl

Hi I  did a quick search in the threads and found this link that may help you 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck! :popcorn:

---

### Post by bodhi.zazen on 2007-07-01
First physically mover your hard drives. Then:

1. Supergrub : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

2. Boot the live CD and either :

A. Re-install GRUB : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[indent]Same instructions even though you did not install windows ^^^ [/indent]

B. Edit /boot/grub/menu.lst manually. This last method is harder if you do not know grub. You will need to set configuration headers at the top.

---

### Post by cwmoser on 2007-07-02
Whew, this was a job -- but this is basically how I moved Grub to HD0.....

The grub-install resulted in my PC not being able to boot - all I got was "GRUB" on the screen.

What I did to recover was:

- boot using an MSDOS disk and issued:  FDISK /MBR
  This gave me back my Windows XP -- still no Ubuntu but I could boot up XP.

- used the Ubuntu install live CDROM to boot to a command prompt.
  sudo grub
  grub>  find  /boot/grub/stage1
  grub>  root  (hd0,2)
  grub>  setup  (hd0)
  grub>  quit

I had two linux partitions on hd0 -- /dev/sda3 and /dev/sda6.  For some reason, you cannot point grub to /dev/sda6 via root (hd0,5) -- that just does not work.  On partition /dev/sda3, I modified the /boot/grub/stage1 menu to boot the kernel in partition /dev/sda6.

Grub is an area that I would like to know more about.  But, now I can replace hd1 without it interfering with booting operating systems.


Carl

---

