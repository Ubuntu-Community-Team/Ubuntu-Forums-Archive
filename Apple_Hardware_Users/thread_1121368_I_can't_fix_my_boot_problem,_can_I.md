---
title: "I can't fix my boot problem, can I?"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by norma on 2009-04-10
Hey there... so I don't think there is a way to fix this is there?

Problem: I completely erased mac osx from my hd on my macbook 4,1 when I installed ubuntu. I did not install refit prior to doing this and presently it will not boot without the live cd in the disk drive - flashing gray folder otherwise -

I downloaded and installed gptsync to no avail, still get the gray folder when booting with no disk.

---

### Post by cyberdork33 on 2009-04-10
> **norma said:**
> I downloaded and installed gptsync to no avail, still get the gray folder when booting with no disk.
did you run gptsync? Any terminal output?

Also, please do not keep creating new topics. Please stick to one thread. It will help us better understand what you have or have not done, and what your current situation is.

For reference:
[http://ubuntuforums.org/showthread.php?t=1112200](http://ubuntuforums.org/showthread.php?t=1112200)
[http://ubuntuforums.org/showthread.php?t=1117240](http://ubuntuforums.org/showthread.php?t=1117240)

---

### Post by norma on 2009-04-10
Ahh, sorry about the new threads - i'll stick to this one.

Yes, i clicked on the link, downloaded gyptsync. and ran it in terminal with

sudo apt-get update
sudo apt-get install refit
sudo gptsync /dev/sda
exit

everything seemed to check out, the terminal indicated that the packages were found and properly installed.

However the problem still persists when I boot with no live cd - gray folder.

---

### Post by cyberdork33 on 2009-04-10
> **norma said:**
> Ahh, sorry about the new threads - i'll stick to this one.

Yes, i clicked on the link, downloaded gyptsync. and ran it in terminal with

sudo apt-get update
sudo apt-get install refit
sudo gptsync /dev/sda
exit

everything seemed to check out, the terminal indicated that the packages were found and properly installed.

However the problem still persists when I boot with no live cd - gray folder.
ok, next, reinstall grub as in this post:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

It should then be able to boot, but if not, then you may need to try blessing.

---

### Post by norma on 2009-04-11
> **cyberdork33 said:**
> ok, next, reinstall grub as in this post:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

It should then be able to boot, but if not, then you may need to try blessing.

Okay, I tried that - followed the input exactly only difference is that grub was located at (hd0,0).

Terminal spat out exact same response to the input, so everything seemed to check out on that end.

Still persists though gray folder until i insert the disk.

note: I'm doing all of this from my desktop terminal in applications - that's not a problem right?

Thanks,

Norm

---

### Post by cyberdork33 on 2009-04-11
> **norma said:**
> Okay, I tried that - followed the input exactly only difference is that grub was located at (hd0,0).

Terminal spat out exact same response to the input, so everything seemed to check out on that end.

Still persists though gray folder until i insert the disk.

note: I'm doing all of this from my desktop terminal in applications - that's not a problem right?

Thanks,

Norm
Well, then one last thing to try... Bless. You will need the OS X DVD for this one (or an install of OSX on a USB drive).

[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21)

---

### Post by bbarabas on 2009-04-14
Hi, 
So far I used Ubuntu 8.04 on my Mac laptop. I wanted to install Fedora using the partitioning option by which I created a smaller, new partition on the free space (this worked fine when I installed Fedora on a PC, along with XP). However, after reboot I could not access Ubuntu any more, it looks like the Ubuntu partition disappeared completely. At booting there is a list similar to the one that started when I booted Ubuntu, but when I press L only Fedora boots. How can I get back Ubuntu and my /home directory? I never had such problems with Ubuntu, please give me the steps as detailed as possible. Thanks a lot.

---

### Post by cyberdork33 on 2009-04-14
> **bbarabas said:**
> Hi, 
So far I used Ubuntu 8.04 on my Mac laptop. I wanted to install Fedora using the partitioning option by which I created a smaller, new partition on the free space (this worked fine when I installed Fedora on a PC, along with XP). However, after reboot I could not access Ubuntu any more, it looks like the Ubuntu partition disappeared completely. At booting there is a list similar to the one that started when I booted Ubuntu, but when I press L only Fedora boots. How can I get back Ubuntu and my /home directory? I never had such problems with Ubuntu, please give me the steps as detailed as possible. Thanks a lot.
Please start a new thread and give specific details about your hardware

---

### Post by norma on 2009-08-20
is there any way to bless without the osx cd? I don't have one, or is there anyway to acquire osx on a usb drive without footing a bill?

---

