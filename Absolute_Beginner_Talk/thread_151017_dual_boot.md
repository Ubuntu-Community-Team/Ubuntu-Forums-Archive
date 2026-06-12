---
title: "dual boot"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-27
at the moment I have a dual boot with xp but now I want to shrink windows to its smallest size what software is avaible to do this from within ubuntu.

thanks

;)

---

### Post by Sef on 2006-03-27
> at the moment I have a dual boot with xp but now I want to shrink windows to its smallest size what software is avaible to do this from within ubuntu.


The Live CD has gparted on it.  Use that to shrink Windows.  Applications > System Tools > gparted.

---

### Post by akiro.yamamoto on 2006-03-27
You can also use the gparted livecd or [System Rescue CD.](http://www.sysresccd.org/Main_Page)

---

### Post by Kapre on 2006-03-27
[QUOTE=lex1]at the moment I have a dual boot with xp but now I want to shrink windows to its smallest size what software is avaible to do this from within ubuntu.

thanks

;)[/QUOTE]

lex1 - all the info that was provided above, you can use. But please make sure that you back-up then defrag your HD before doing the resizing so that if you have some important data on your xp, you wont loose it.

Enjoy!

K

---

### Post by cls1chuck on 2006-03-27
I tried doing the above (using gparted to shrink my ntfs partition); it 'acted' like it was doing it, but only ran for about 2 seconds.  After it 'ran', the partition was still the same size.  Yes I did click the 'apply' button; FYI I'm booted from the Live CD version, and and my HD isn't currently accessible (I try enable, but it does nothing).  Do I have to mount it first?  If so, shouldn't I get an error?
Thanks in advance

---

### Post by OBnascar on 2006-03-27
[QUOTE=cls1chuck]it 'acted' like it was doing it, but only ran for about 2 seconds.  After it 'ran', the partition was still the same size.  Do I have to mount it first?[/QUOTE]

No you do not want to mount the drive.

I'm sure your other replies have had sucess using the ubuntu live cd, the gparted livecd and the SystemRescue CD and they have given you some good tips.

If you would want to try another tip, check out my signature below, using Disk Drake. I have down-sized Window partitions with it and have not had any problems. Disk Drake is known for one of the best partitioners that there is.

For using Disk Drake, you will need either a PCLinuxOS live CD, then when the live CD is loaded, choose install from the desktop, or use a Mandriva install disk. From either one of these methods just run the install until you get to the partitioner, then choose your Windows partition, pick your new size for it, and choose the file system. When it finishes that task, then cancel  before it actaully starts to install system files.

Your Windows partition should then be resized and in a very bootable and usable condition.

Good luck cls1chuck, try this if your other options don't work for you.

---

### Post by aysiu on 2006-03-27
I second the motion for [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by plors on 2006-03-28
[QUOTE=cls1chuck]I tried doing the above (using gparted to shrink my ntfs partition); it 'acted' like it was doing it, but only ran for about 2 seconds.  After it 'ran', the partition was still the same size.  Yes I did click the 'apply' button; FYI I'm booted from the Live CD version, and and my HD isn't currently accessible (I try enable, but it does nothing).  Do I have to mount it first?  If so, shouldn't I get an error?
Thanks in advance[/QUOTE]

Sounds like known issues with older versions of gparted. Try the latest gparted (prefferably on its own [livecd]("http://gparted.sourceforge.net/livecd.php")) and you should be fine.

---

### Post by IDipSkoalMint on 2006-03-28
I've had great success with PartitionMagic in the past (I've used it for about 8 years now). You have to log in under Windows to use it, but it's a great piece of software, and isn't too expensive.

---

### Post by Mustard on 2006-03-28
I just resized (shrunk) a ntfs partition yesterday with **qtparted** from the latest Kanotix live CD.  There are a lot of different options. :)

---

