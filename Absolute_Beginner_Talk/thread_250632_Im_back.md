---
title: "Im back"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by bigstick on 2006-09-04
OK Guys Im Sorry!!
It was unfair of me to expect everybody just to drop everything and help me,can we be friends?

Here is a knew developement,I wiped both hard drives and reinstalled Windows xp home sp2 got all systems up and running.
Went out and bought the Linux Mag and guess what?? Ubuntu on DVD.
I ran the live cd and formated the empty drive on ext2 I then installed the system and rebooted.
It went straight into windows and checking to see if Ubuntu installed Ive lost a hd,now ether windows does not recognise ext2 or I have a problem? any help!!

Thanks

---

### Post by meng on 2006-09-04
Don't worry, Windows just doesn't recognize ext2 unless you install an extra program. But there's still the problem of why it goes straight to Windows. Does a GRUB message pop up for a couple of seconds at boot, giving you a brief opportunity to press ESC? Watch the boot process carefully from the beginning, and take note of exactly what you see.

---

### Post by Klaidas on 2006-09-04
Your're sorry for what?

---

### Post by Turgon on 2006-09-04
You can find ext2 windows drivers here:

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

and here:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Im not sure which is better, but they will at least work (i hope).

---

### Post by Dinerty on 2006-09-04
Would'nt ext3 be better?, or does winodws not read ext3?

---

### Post by xhaan on 2006-09-04
With the proper drivers Windows can read both ext2 and 3
ext3 is basically ext2, except ext3 has journaling.
You can even mount ext3 as ext2.

---

### Post by monktbd on 2006-09-04
> **Dinerty said:**
> Would'nt ext3 be better?, or does winodws not read ext3?

ext3 is only an extension to ext2.
there is only the journaling that is different (ext2 doesnt have journaling).
so you can read an ext3 filesystem with ext2. i wouldnt dare writing on it though.

edit: someone beat me to it :).

---

### Post by bigstick on 2006-09-04
There is no boot up message straight to windows, and ext2 was the preferance of Ubuntu when formating the drive and installing.
Now how do I get the hd back? In windows device manager the hd is there and working correctly, but does not show as a drive in my computor. Has Ubuntu installed or has the drive just been formated?

Ps I had to use the IRQPOLL switch to install the live cd as an error of drive confused keeps repeating on both hda and hdb. 

Thanks

---

### Post by whizbaby on 2006-09-04
To check whether or not ubuntu is installed, boot from live cd and check with either terminal or graphical directory tool (thunar, nautilus, don't know which dvd you have but they should be on it).
If it's there we should be able to help you debugging your boot sequence.

---

