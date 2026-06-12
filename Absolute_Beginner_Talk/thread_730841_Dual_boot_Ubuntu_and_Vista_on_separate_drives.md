---
title: "Dual boot Ubuntu and Vista on separate drives"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by mundo on 2008-03-21
Hi,  I would like to try out Ubuntu and want to create a dual boot for Ubuntu and Vista. I have 2 separate hard drives (C: and F:), is it adviseable to use one for each operating system? If so then how do I go about doing this?  By the way Vista is already installed and I have Ubunto 7.1 iso on CD ready to go.

---

### Post by mundo on 2008-03-21
I think I have found what I was looking for:

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

### Post by markjensen on 2008-03-21
Well, "C:" and "F:" aren't necessarily separate drives in Windows.   They can easily be partitions on the same physical drive.   Linux can be installed on a separate drive, or just a different partition on the same drive.   It doesn't matter how you install it - it works either way.

If you already have a totally separate drive installed, just for Linux, that is fine, and we might as well use that.

Boot the Ubuntu CD, and start the install process.  If you are not sure which drive is which (by total volume size or what not) when it comes to selecting a destination, post back here, and we can help sort that out.

Then let Ubuntu install GRUB to your Windows drive.  This will replace the Vista boot loader with GRUB, and allow you to select your OS at boot time.   If you change it and set it to install GRUB to your Linux drive, you will end up with a PC that still can only boot Windows after all that work. :P

---

### Post by Sef on 2008-03-21
> Hi, I would like to try out Ubuntu and want to create a dual boot for Ubuntu and Vista. I have 2 separate disk drives, is it adviseable to use one for each operating system? If so then how do I go about doing this? By the way Vista is already installed and I have Ubunto 7.1 iso on CD ready to go.

Installing on two separate drives is a good way to go.  Please read this [thread]("http://ubuntuforums.org/showthread.php?t=179902") for more information.

---

### Post by bumanie on 2008-03-21
If there is something on f:/ transfer it to c:/ 
As you have vista on the first hard drive, the install of ubuntu should be straight forward.
Let the live ubuntu cd to boot up  click install and answer the questions (Language, location etc). At the partitioning stage, I would suggest choosing manual and setting up the mandatory / and swap partitions and in addition also a separate /home partition. Your f:/ should be deignated sdb in ubuntu. 
Give 5-6 gb for / 1-2 gb for swap and as much as you like to /home. The advantage of setting up a separate /home, is that if anything goes wrong with the file system and ubuntu becomes corrupted, you only have to reinstall to / and all your saved data in  /home will be safe.
Hope this helps.

---

### Post by bumanie on 2008-03-21
> I think I have found what I was looking for:

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

That is a site about booting with esybcd bootloader. Some use that if grub won't work for some reason, but in your case, there is no reason why grub won't work, so there is no reason to use easybcd bootloader. Grub will recognise your vista installation during  its installation process and give you the option of which OS to boot into.

---

