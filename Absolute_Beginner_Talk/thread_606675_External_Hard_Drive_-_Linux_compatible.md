---
title: "External Hard Drive - Linux compatible?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-08
Am looking for a new external hard drive.
Interested in [this ]("http://www.amazon.co.uk/Seagate-FREEAGENT-DESKTOP-UK-VER-7200RPM/dp/tech-data/B000OT5IMW/ref=de_a_smtd/026-8524818-9663624?ie=UTF8&qid=1191927407&sr=8-4")one:

Question:

It doesn't mention Linux in OS list.
Will it work?

---

### Post by PmDematagoda on 2007-11-08
There is a very good chance the external HDD is compatible, but you cannot be 100% certain. But in my case, every external HDD I used worked on Ubuntu, and none of them were of a "significant" brand like Seagate, so most likely the external HDD would work on Ubuntu.

---

### Post by 01steven on 2007-11-08
What's generally the rule?

---

### Post by Schalken on 2007-11-08
It is my understanding that external hard drives appear to the Operating System (Linux) the exact same way as USB flash drives do, the only difference being they have a LOT more space.

If this is the case, then yes, like a USB flash drive, it should work just fine. :)

---

### Post by anaconda on 2007-11-08
Yes.. ofcource it will work!

I never had any problems with USB-memories or hd:s. They basically all use the same interface..

---

### Post by 01steven on 2007-11-08
I can confirm that a Maxtor 120GB Hard Drive I have owned for a while (and used with Windows) does work fine with Ubuntu.
But not sure if I was just lucky!

---

### Post by Kabamaru on 2008-01-03
This is a late reply - I apologize.

It's my understanding that Seagate's FreeAgent line of external hard drives are not linux friendly.  Something about being pre-formatted to NTFS and a power-saving feature that disconnects the unit.  Can anyone verify this?

---

### Post by frodon on 2008-01-03
As long as your external drives is formatted with a compatible file system you shouldn't have any problem as it is really common stuff.

---

### Post by laidback on 2008-01-03
I have used various external hdds including a 2.5" from a laptop. All read via USB, never had a problem. My main one is a 250Gb Western Digital partitioned for NTFS and Ext3. All have been of the IDE (ATA) variety, yet to purchase a Sata drive. I use Gparted for formatting etc.

---

### Post by Kabamaru on 2008-01-03
Thanks for the quick replies folks ^_^

I realize that the NTFS side of the issue is easily fixed.  I was just mentioning it.

In regards to the power-saving feature, this is what I was specifically referring to:
[http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent](http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent)

---

### Post by jacaronda on 2008-01-07
I purchased a Toshiba USB 2.0 portable external and it does not work with my Ubuntu 6.06. When plugged in, fdisk doesn't report it.  When I called Toshiba they said it is NOT Linux-compatible.

---

### Post by Kabamaru on 2008-01-08
> **jacaronda said:**
> I purchased a Toshiba USB 2.0 portable external and it does not work with my Ubuntu 6.06. When plugged in, fdisk doesn't report it.  When I called Toshiba they said it is NOT Linux-compatible.
I haven't had to deal with this sort of issue on Ubuntu before, so I can't say what may or may not work for you.  However, this [thread]("http://ubuntuforums.org/showthread.php?t=652601") looks like it might be useful.

Good luck, and let us know what happens.

---

### Post by bbqsandwich on 2008-01-08
**I have the exact same hard drive linked to in the original post** (although in the U.S.) and it works great. I just plugged it in and Ubuntu recognized it immediately.

Perhaps the reason it is listed only as PC and Mac compatible is because it comes with backup software, and that software might only be for those two OSes.

However, this is no big loss. I installed the software on the Windows side of my PC (I dual boot Vista and Ubuntu) and guess what - **it's only a trial version**! Didn't see that anywhere in the marketing.

So for now, I'm using the old-fashioned backup method -- Select All, Copy, Paste. :)

P.S. The glowing orange strip on the front of the Seagate looks really cool, by the way.

---

### Post by tigerplug on 2008-01-08
There shouldn't be any issues with any Mass Storage Device.
The only problem that I could possibly see is filesystem/ formatting.

---

### Post by Leo the Lion on 2008-01-08
I just bought a 250GB Seagate FreeAgent, and although Ubuntu 7.10 sees it, I can't access anything in it. I get a message saying "The folder contents could not be displayed". Any ideas?

---

### Post by SuperTeece on 2008-01-08
I have a Freeagent Pro 500GB and my stock installation of Feisty communicates perfectly. I haven't had to make any modifications or tweeks. I am using the USB connection. This is on a Gateway MX6123 laptop. My installation of Feisty is completly stock, mostly due to the fact that I have no way of connecting it to the internet while deployed.

---

### Post by whistlerspa on 2008-01-08
I have the 250Gb version of this drive.  It runs on Linux but I had problems with it going to 'sleep' and then not being able to wake it again. 

To overcome this I downloaded the management software to disable sleep mode from Seagate's web site.  This is only available for Windows so you'd need access to a Windows box to configure the settings. After this no problems should ensue

---

### Post by whistlerspa on 2008-01-08
> **Leo the Lion said:**
> I just bought a 250GB Seagate FreeAgent, and although Ubuntu 7.10 sees it, I can't access anything in it. I get a message saying "The folder contents could not be displayed". Any ideas?

See my earlier comment - this was partly the reason for the error message. Also make sure that ntfs-3G is installed (check using Synaptic).

---

### Post by pwnsaur on 2008-03-30
I bought a 500GB Seagate FreeAgent drive and i cannot delete files off it. It keeps saying that it is in 'read mode'. Any help with this? also from windows i cannot format it into something compatible with linux... need some help please... :confused:

---

### Post by JCM45 on 2008-03-30
that hard drive does work.  my roommate has the exact one and he boots linux off of it.  i also have a smaller version and it works with no problems.

---

### Post by pwnsaur on 2008-04-03
linux can read the drive, but when I try delete anything on it it just says "error this is a read only drive" any ideas??

---

