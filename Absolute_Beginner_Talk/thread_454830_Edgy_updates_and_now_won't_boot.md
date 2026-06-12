---
title: "Edgy updates and now won't boot?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by holmb101 on 2007-05-25
I just did some updates to edgy which asked me to reboot after installing them.  So I installed and rebooted.   Now when I choose linux at the boot menu (dual boot XP and Ubuntu with windows controlling boot), the only thing that shows up is some text saying Grub in the top left corner of the screeen.  

The only thing I noticed about the updates is that their was four downloads, and one of them was 21 mb.  

What happened, and how can I get Ubuntu back?  

Thanks

---

### Post by wgw on 2007-05-25
I think I might have the same problem. I noticed that there were header files in the update. Could that be an issue? 

My book goes to the the point where U. shows a progress bar and then hangs. (whether in regular or recovery mode)

I can boot into a lower kernel version (version 10 generic) but there is a x.conf error.  (I get as well a ndiswrapper error, but I don't  think that would prevent the boot -- maybe it would??? I think that would mean just that then network adapter would not work.)

I can't say I'm sure the update caused the problem, but I definitely did an update and then a hibernate. (Hibernate has always worked correctly before.) Now I'm stuck!

---

### Post by wgw on 2007-05-25
I seem to have resolved my problem. I read this post: [https://answers.launchpad.net/ubuntu/+question/3548](https://answers.launchpad.net/ubuntu/+question/3548)

And then by chance u. ran fsck when I was trying again to boot into my machine. That was it. Of course, I'm not sure what fsck did -- the results scrolled by too quickly. But it would seem that the first thing to try for boot problems is fsck. 

My problem may well have be a glitchy hibernate... still a mystery, but after some anguishing 2 hours, it seems to be back among the living. 

Good luck!

---

### Post by holmb101 on 2007-05-26
So I booted from the live cd and typed  "sudo fsck /dev/sda3" and it said my partition was clean.  This did not fix my problem.  From the live cd, I was able to mount my linux partition and view the menu.lst file.  Everything appears correct in the menu.lst file.  

After I select Ubuntu from the boot list, a black screen with the grub text comes up.  When this happens, I can't  do anything but shutdown.  

Any Ideas?

---

### Post by holmb101 on 2007-05-27
I tried re-installing grub with no luck.  

Another thing is that the grub text freezes before reaching the grub menu.

---

### Post by wgw on 2007-05-27
If you are not able to get to the grub menu, I'm not sure what to do. I think one thing to do once you start the boot process is to look at the log files. But I don't think there are grub log files. Here is what I found in the forum: 

Using Ubuntu Dapper 6.06.
There are several log files in /var/log:
1) /var/log/messages (shows activities over a longer period of days)
2) /var/log/dmesg (is the log file from booting the system)
3) /var/log/syslog (in my case it showed today's activities)
__________________

I'm new to linux, so I'm not the best person to resolve this problem. This is a stab in the dark.

---

### Post by zero244 on 2007-05-27
I for one am going to stop doing any kernel header updates or anything that isnt related to a paticular piece of software. Ive seen too many posts where people did updates then found something was broke.
If its not broke dont fix it........is sometimes hard to follow but it is good advice.

---

### Post by holmb101 on 2007-05-27
FIXED

I made a new ubuntu.bin file to be placed in "C:\" on my Windows partition.  After I did this, ubuntu started right up!!  So the updates must have changed the first 512 bits of the boot sector on my lnux partition.  This is why grub wouldn't fully load.

---

