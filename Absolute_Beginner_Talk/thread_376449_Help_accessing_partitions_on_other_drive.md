---
title: "Help accessing partitions on other drive"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Yellohead on 2007-03-04
Hi there, new to Linux and Ubuntu.

I just made a fat32 partition on a second drive, so that I can share files with XP.  

I can't seem to get any sort of access to this new partition in Ubuntu.  No problems getting to it XP.

In windows terms, I just go to My Computer, click on the drive, it opens up, and I'm off to the races.  

In ubuntu, when I try to do the equivalent, go to devices>drives, I can't get in!

ubuntu says I am not the owner of the partitions.  WTF?  I *made* those patitions!

how do I get in?

BTW, I am at these forums through XP, because I can't get Ubuntu to use my wireless usb device to connect....  That's where being able to look at a Wireless troubleshooting guide while tinkering would be helpful....which I could put on a fat32 partition for example.

Help!

---

### Post by taurus on 2007-03-04
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Yellohead on 2007-03-04
perhaps I am a bit too nooby.

when I try to follow the command sudo cp /etc/fstab/etc/fstab_backup, I get an error along the lines of 

invalid destination opperand

or something to that effect

---

### Post by Patrick K on 2007-03-04
> sudo cp /etc/fstab/etc/fstab_backupYou need a space between the first fstab and /etc. Like this:
> sudo cp /etc/fstab /etc/fstab_backup

---

### Post by Yellohead on 2007-03-04
> **Patrick K said:**
> You need a space between the first fstab and /etc. Like this:

thanks.  I'll give it a try

---

### Post by rccharles on 2007-03-05
> **Yellohead said:**
> Hi there, new to Linux and Ubuntu.

I just made a fat32 partition on a second drive, so that I can share files with XP.  

I can't seem to get any sort of access to this new partition in Ubuntu.  No problems getting to it XP.



To avoid a lot of hassles, most people run as administrator in XP.  Running as administrator defeats a lot of Windows security as witnessed by lots of Window's Malware.  

Ubuntu is set up so you run as a normal user.  When you want to do administration stuff, you need to enter your password.

To do a bunch of command line administrative stuff you can do:
sudo bash
  #enter your logon password.


# When done, enter:
exit


Robert

---

### Post by Amenemhet on 2007-03-05
Ahhh, sure, but me thinks he still needs to mount it, yet again Taurus beat me too it...
To Taurus > I bet you have that link memorized by now!

---

