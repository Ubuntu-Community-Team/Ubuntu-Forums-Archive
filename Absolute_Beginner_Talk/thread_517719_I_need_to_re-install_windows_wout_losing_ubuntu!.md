---
title: "I need to re-install windows w/out losing ubuntu!"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by myk.dinis on 2007-08-04
I need to re-install windows for one of my kids games to work right and I don't know how to do it without losing my ubuntu installation...

When I was installing ubuntu I didn't know how to make it not overwrite my MBR and now if I re-install win it'll hose the MBR again and I won't be able to boot into linux...what do I do?

HELP!! :)

PS...I'm not joking...I really have no idea what to do!

---

### Post by MQMike on 2007-08-04
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(This is the basic, general Post#1)
and see the posts following:
HOW To:  Change the Default Operating System (Also:  Changing the timeout, boot menu, and other tips)
April 21, 2007.

Install Windows XP *after* Kubuntu, and install XP to a non-first hard drive: map command
July 24, 2007


You will have to make a partition for Windows, install it, it WILL overwrite the MBR, so then use the methods of the How-To to re-install GRUB to the MBR and control the booting of both Ubuntu and Windows.  Take your time.  This is doable.  Use GParted to do the partitioning first.

---

### Post by Aurdal on 2007-08-04
[nevermind]

---

### Post by apswartz on 2007-08-04
You know, back when the only bootloader was lilo, it was pretty easy. I confess that I have never taken the time to understand grub, or many of the other new things.

---

### Post by myk.dinis on 2007-08-04
ok...the only problem is I looked at that post you sent me to...mere moments before getting back here and it showed me how to install xp on a different NON-first drive,...

Pretty much what I need to know is how can I write my boot stuff to a floppy so I can get back into ubuntu to overwrite the MBR after I re-install windows on sd0 where it currently resides (or hd0 depending on your viewpoint)...

I primarily don't want to lose my ability to get back into ubuntu...

But I NEED to reinstall windows...I kinda trashed it...it still works but it has problems that I can't repair ( I trashed the registry trying to offload all the %userprofile% settings to a separate drive after the installation was complete...I now have 4 diff logins for my one username in the registry and in the doc and settings folder...)  ...So I need to re-install and get back to having fun in linux...windows is on the smallest drive as a backup OS...but it needs to be first and default in case I'm not home and the computer restarts and one of the unenlightened decides to use my computer (already happened and they trashed my linux installation)

Thank you...

---

### Post by bodhi.zazen on 2007-08-04
You do not need to do that ... justinstall windows and restore grub :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

