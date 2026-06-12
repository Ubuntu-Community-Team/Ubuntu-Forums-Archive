---
title: "Help - huge problem!"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by ADH on 2006-09-13
I am an absolute novice with Linux - I run eComStation (OEM OS/2).  I was told I could install Ubuntu 5.10 on my second (empty) drive without bothering the data on my main drive (which has eComStation and Win98SE boot partitions), plus all my data.  So, I did the install, and told Ubuntu to install on the second disk.  All seemed well, when suddenly I saw the screen saying grub was being installed on the first drive, and I had no way to stop it.  So, here I sit with Ubuntu, which I don't know how to use - not even to install stuff I download) on my second drive, and I can't get to eCS and my data on the main drive!  Why did this happen?  A friend just told me Linux has done this to him a few times, but he runs Windows and knows how to fix it.

Linux Disks Manager reports that the main drive has partition 1, 243 meg Extended 3, and partition 5, 114 gig unformatted free space (so Ubuntu apparently didn't format that drive, just screwed up my partition table.)  Drive two is formatted, partition 1 18 gig Extended 3, swap partition 870 meg.  How can I get my main drive back?  I have the shareware hard drive utility DFSEE ([www.dfsee.com](www.dfsee.com)) on CD - it comes in a Linux version, if anyone wants to look at it.  Can anyone help me here?  Apparently, I need my old partition table back, and to move Linux's boot partitition to the second drive.  I'm desperate.

---

### Post by kuja on 2006-09-13
The last time I mutilated my partition setup, I had luck restoring it with a great and simple to use tool called test-disk. Maybe it'll work for you too.

---

### Post by ADH on 2006-09-14
Thanks.  Where do I find this utility, and what do I do with it once I find it (to install it, etc?)

It would seem to me that if I could just copy Ubuntu's boot partition to drive 2, and unformat it on drive 1, my old partition table and data would still be on drive 1 (formatting doesn't destroy data, it seems.  I'm hoping that's the case.)  I've e-mailed the author of DFSEE, who says Linux has been doing this to a lot of people (recently, more than before), and DFSEE may be able to help.  I wish I knew Linux did this before my install - I wouldn't have done it.  :(  I had asked in os/2 and linux echoes before even considering trying linux, and I was told it would recognize other OSes, and I'd have no problem if I installed to drive 2.  

Question on other topics - I'm using Thunderbird for Linux.  I've never used Thundrbird, as I have an OS/2 e-mail/news utility I've used for years.  How can I deleted lines in T-bird, other than by holding the delete key down.  I try to select text with my trackball button, but it doesn't get marked,  Do I have to set something in Linux to tell it how to handle the trackball?

Also, how do I install software I download, in both zip and tar formats?  I am so confused.  I downloaded DFSEE for Linux in zip - can I install it?

---

### Post by bodhi.zazen on 2006-09-14
Don't panic.

Ubuntu just had to modify the MBR so it could boot. You should be able to boot either OS.

What happens when you re-boot? You should get a boot screen where you get an option of what OS to boot.

If not let me know what happens when you re-boot and we can fix.

---

### Post by jester805 on 2006-09-14
I have a similar problem.  I am dual-booting between Ubuntu and XP.  I just did a check for system updates and it found a Linux Kernal update.  It installed and rebooted.  After the reboot, Windows XP is not an option on the grub boot menu!  ](*,)

---

### Post by bodhi.zazen on 2006-09-14
> **jester805 said:**
> I have a similar problem.  I am dual-booting between Ubuntu and XP.  I just did a check for system updates and it found a Linux Kernal update.  It installed and rebooted.  After the reboot, Windows XP is not an option on the grub boot menu!  ](*,)

In a terminal:
```
sudo nano /boot/grub/menu.lst
```

Add this:
> Title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

Ctrl-X to exit, "Y" to save.

Re-boot

---

### Post by ADH on 2006-09-14
When I reboot, the system just boots up Linux - no other options. The Linux boot sector apparently overwrote the first 243 meg of my eCS C drive, rather than being placed on drive 2, where I wanted it to be (and thought I told it to go.)  I had a boot manager called airboot handling bootup before - I had boot partitions of eCS 1.2, eCs 1.1, and Win98SE on drive one, plus all the data for eCS in other partitions.

The DFSEE author told me how to install DFSEE in Linux, and I've done it, but when I try to run dfsee, Ubuntu tells me "Permission denied."  He wants me to run dfsee to create some files to send to him, after which he can hopefully tell me how to get my system back.  So, how do I get permission to run dfsee?

A Firefox question - how do I upgrade from 1.0.8 to 1.5.0.6?

I really miss my eCS.  <sniff>

---

### Post by kuja on 2006-09-14
You need to run the program with root privileges. to do so you should use sudo. Easiest to do so from a terminal. Something like: sudo dfsee
It'll ask for your password, then it'll let you run the program.

Also, about the program I recommended, if you're still interested in trying test-disk. I would recommend you run it from a livecd. Ubuntu's should do, though it doesn't include testdisk.

From the ubuntu live cd (which you undoubtedly have if you installed it, unless you used the alternate cd), just copy and paste the following into a terminal while using the live cd.
```
sudo -s
echo "deb http://archive.ubuntu.com/ubuntu dapper main restricted universe" >> /etc/apt/sources.list
apt-get update
apt-get install testdisk

```

You'll need to know the device name of your hard drive. If it's an ide drive it's probably /dev/hda,(hda = primary master ide, hdb = primary slave ide, hdc = secondary master ide, hdd = secondary slave hdd) else if it's sata then probably /dev/sda (sda = first sata, sdb = second sata, etc). 

Assuming it is /dev/hda
run testdisk this way:
```

sudo testdisk /dev/hda

```
If it gives a warning about not having enough lines, maximize the window and try again. It should be pretty straightforward what to do from thereon.

---

### Post by ADH on 2006-09-14
I just got a message from the dfsee author via the dfsee Yahoo group - Comcast is now blocking his e-mails, for some reason.  Anyway, he told me to run ./setup in /dfsee, and that got things working.  Dfsee is now running, so I'm going to see if I can get it to do what he told me to do.

---

### Post by ADH on 2006-09-14
Dfsee is telling me it can't see any disks.  :(  I told the author.  It saw them when I booted the dfsee cd, so it should see from inside Linux.  I've made no changes to the drives sincce the install - I've only looked at them with Linux's disks report.

---

### Post by bulldog on 2006-09-14
Try to use the Escape button before booting in Ubuntu.
The default setting of GRUB is hiddenmenu.

With escape you see maybe a menu with your other OS's.

Hope so anyway.

---

### Post by ADH on 2006-09-16
Sorry I haven't replied the past couple of days.  On top of Ubuntu overwriting my main drive with it's Grub, one of my fans died, and the computer shut off due to heat.  I'm disabled, plus I wouldn't know how to fix the innards of a computer if I wasn't, so I had to wait for my computer-knowledgeable friend to come over (he found the dead fan.)  Right now, I'm running with the case cover off until we get a replacement fan.  He also took my main drive along - we ran the DFSEE script the author needed from the DFSEE boot CD, and e-mailed him the files it output.  When the author replies with what to do to restore my main drive (hopefully - I'm praying to the computer gods), he'll stick it into one of his systems and follow the instructions, then bring the drive and a new fan back.

With the main drive out, I just reinstalled Ubuntu 5.10 to the second drive, and, as it was the only drive, everything (including Grub) was placed on that drive, where I wanted it all in the first place!

I guess now I should upgrage to Ubuntu 6.06?  How would I do that?

Thanks again for all the advise.  I will let you know when I get my old system back.

---

### Post by bulldog on 2006-09-16
You simply could have use the windows system disk to put your original windows boot back.
The other program I do not know,can't say anything about that.
But GRUB is a very tiny prog written in MBR and it sure won't overwritten anything else but your previous boot program.

---

### Post by ADH on 2006-09-16
I don't use Windows, so that wouldn't have worked for me.  It sounds like a good tip for Windows users, though.

---

### Post by ADH on 2006-09-20
Well, the repair script didn't work.  My partition table is restored, but apparently Linux destroyed some data on other partitions on my master drive beyond where Grub was placed, despite Linux saying all but 243 meg of 120 gig was unformatted.  I couldn't boot from my second boot partition on that drive.  I'm really screwed.

How do I access a floppy drive and create directories in Ubuntu?

---

### Post by bodhi.zazen on 2006-09-20
I agree you have a huge problem...

---

### Post by kuja on 2006-09-20
At this point, I certainly hope you have backups. It'd be easier at this point to do the whole reinstall, rather than play with this.

---

### Post by ADH on 2006-09-20
I'm trying to get my crash recovery to work, but it isn't, so I guess reinstall iis my last chance.  I don't understand why Linux messed with drive 0 when I told it not to, and why, even though it did, it messed with that entire drive and not just where it stuck Grub.

---

### Post by catlett on 2006-09-20
Are you still able to boot to ubuntu? If so, did your other partitions get mounted? Did you try to mount the partitions to access your data?
Have you attempted to editr the grub menu to boot your other OS? Or have you taken another path?

---

### Post by ADH on 2006-09-20
We tried to undo what Linux did.  Don't ask me how - the DFSEE author sent a dfsee sript restoreed my old partition table, but apparently the first four (three bootable) were hosed by Linux, and don't have all the files needed to boot.

---

