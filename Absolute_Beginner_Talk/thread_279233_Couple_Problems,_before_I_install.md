---
title: "Couple Problems, before I install"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Snorglorf on 2006-10-17
I've decided that I'm switching from Windows XP to Ubuntu, after much though. I downloaded the .iso for the Ubuntu Desktop version, and am currently booting off the disc. I've got two problems. First, when I boot in normal mode (as opposed to safe graphics) my mouse doesn't move. I have a Logitech MX310, if it matters. Second of all, how can I get the OS in a widescreen resolution? I can't live without 1440x900. 8)

---

### Post by bulldog on 2006-10-17
Your mouse should work right out the box,and your wide screen is only an option when you have installed drivers for your graphic's.

This can be done after the install.

---

### Post by Snorglorf on 2006-10-17
> **bulldog said:**
> Your mouse should work right out the box

Yes, but it doesn't. Any idea how to fix it? Keep in mind that I'm COMPLETELY new to Linux.

EDIT: It works fine in the safe graphics mode, it's plugged in through a USB port, and the light doesn't come on in normal mode, in case any of this information helps.

---

### Post by monktbd on 2006-10-17
is it connected via USB?
if so maybe try with a ps2 converter to put it on the ps2 mouse port. or the other way round.

---

### Post by taurus on 2006-10-17
You have already installed Ubuntu on your machine!!!  What video card do you have in your machine anyway?

---

### Post by Snorglorf on 2006-10-17
> **taurus said:**
> You have already installed Ubuntu on your machine!!!  What video card do you have in your machine anyway?

I haven't installed Ubuntu, I'm previewing off the disc. And I've got some integrated HP thing.. Nvidia GeForce 6150LE.


EDIT: I don't have a PS2 Converter thing at hand, there's no way to fix it without it?

---

### Post by TrendyDark on 2006-10-17
> **Snorglorf said:**
> I've decided that I'm switching from Windows XP to Ubuntu, after much though. I downloaded the .iso for the Ubuntu Desktop version, and am currently booting off the disc. I've got two problems. First, when I boot in normal mode (as opposed to safe graphics) my mouse doesn't move. I have a Logitech MX310, if it matters. Second of all, how can I get the OS in a widescreen resolution? I can't live without 1440x900. 8)

The resolution can be set after install, that's no big deal.

The mouse problem could be related to your motherboard. Try switching the USB port you have your mouse plugged into, or getting a PS/2 convertor (like $2 I would think).

---

### Post by Snorglorf on 2006-10-17
> **TrendyDark said:**
> The resolution can be set after install, that's no big deal.

The mouse problem could be related to your motherboard. Try switching the USB port you have your mouse plugged into, or getting a PS/2 convertor (like $2 I would think).

I'll plug my mouse into a USB port in the back of the computer, I don't know if it'll make a difference though. It could, I'll report back as soon as I get rebooted in normal mode.

---

### Post by bulldog on 2006-10-17
Or just install in safe mode and pray it works after the install :D

---

### Post by taurus on 2006-10-17
The easiest way is to install Ubuntu on your machine first and see what you have to fix.  Chances are maybe you don't have to fix anything except some real minor stuff.

---

### Post by TrendyDark on 2006-10-17
> **Snorglorf said:**
> I'll plug my mouse into a USB port in the back of the computer, I don't know if it'll make a difference though. It could, I'll report back as soon as I get rebooted in normal mode.

If you had it plugged into the front USB panel, that might have been the problem. Sometimes things like are weird and don't like to work, not only on Linux though. I have problems with almost everything USB on Windows until I get the drivers for my mobo installed.:-D

---

### Post by Snorglorf on 2006-10-17
> **TrendyDark said:**
> If you had it plugged into the front USB panel, that might have been the problem. Sometimes things like are weird and don't like to work, not only on Linux though. I have problems with almost everything USB on Windows until I get the drivers for my mobo installed.:-D

Yeah.. It's working fine now. Anything else I need to know before I install?

---

### Post by pbaehr on 2006-10-17
> **Snorglorf said:**
> Yeah.. It's working fine now. Anything else I need to know before I install?

I will give you the obligatory "Don't forget to back up your files!" warning.

---

### Post by Snorglorf on 2006-10-17
> **pbaehr said:**
> I will give you the obligatory "Don't forget to back up your files!" warning.

I don't really have anything worth backing up. I have music, but that's easily re-obtainable.


EDIT: Anything that might confuse me DURING the install? Me being new to Linux and Ubuntu in general and all.. That goes for advice for right after too. I know enough about pre=install, because you do the exact same thing as if I were just reinstalling Windows. Where it gets hard for me is switching into the Linux stuff.

---

### Post by Scunizi on 2006-10-17
If you're running any SATA drives or your motherboard has the capability, please go to the Ubuntu download page and read the release notes for Dapper.  It will give you a 3 line command to do from the terminal to disable RAID.  I found this neccessary even though I don't run a RAID setup.  Also if you have multiple drives or a mix of IDE & SATA things can get funky.  I installed Dapper on my secondary SATA with WinXP on my primary and I had an IDE for data.  I had to unplug the IDE for Dapper to set up GRUB correctly (that's Ubuntu's boot loader).

---

### Post by Snorglorf on 2006-10-17
> **Scunizi said:**
> If you're running any SATA drives or your motherboard has the capability, please go to the Ubuntu download page and read the release notes for Dapper.  It will give you a 3 line command to do from the terminal to disable RAID.  I found this neccessary even though I don't run a RAID setup.  Also if you have multiple drives or a mix of IDE & SATA things can get funky.  I installed Dapper on my secondary SATA with WinXP on my primary and I had an IDE for data.  I had to unplug the IDE for Dapper to set up GRUB correctly (that's Ubuntu's boot loader).

Thanks.. You guys are great. Your responses are helpful and speedy.

EDIT: Any recommended reading of things I'll need to know?

---

### Post by aktiwers on 2006-10-17
I will recommend you to try out Automatix. Its a really easy way to get the basic stuff installed.

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by TrendyDark on 2006-10-17
A good thing to check out would be Automatix or EasyUbuntu. Automatix does more, [http://www.getautomatix.com](http://www.getautomatix.com) 

It will install somethings like media players, browser plugins, etc.

EDIT:

> **aktiwers said:**
> I will recommend you to try out Automatix. Its a really easy way to get the basic stuff installed.

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

LOL, looks like we had the same idea around the same time 8)

---

### Post by Jukey on 2006-10-17
you also might want to check out [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
as well as
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

