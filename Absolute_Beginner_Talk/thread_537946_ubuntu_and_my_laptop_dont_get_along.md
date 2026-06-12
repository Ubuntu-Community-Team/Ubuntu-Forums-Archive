---
title: "ubuntu and my laptop dont get along"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-08-29
This problem was persistent while i had it installed on my top, after about 32 mounts, it would freak out and go on a loop while booting about a "logical block" and stuff i could not understand, now i got a new HDD which i thought was the issue, since it was refurbished. I put windows back on and its drving me nuts so i decided to dual boot, while trying to load of the live cd, its doing it againg, i dont understand what the issue could be..  I HATE MY laptop so much, its a toshiba sattellite M55, centrino. and i have no idea of what else to say or doo.:confused:

---

### Post by Hmarroqu on 2007-08-29
heres basically what damn thing says over and over. 

"[########] buffer I/O error on device sr0, logical block ###### "


WHY! i love ubuntu and i NEED it on my laptop for skool! wtf.

---

### Post by oilchangeguy on 2007-08-29
please advise your computers specs. i've got a 5  year old toshiba satellite 1805-s177 that runs an intel cent. 800mhz. cpu, 512mb of ram, and a 40 gb hd with ubuntu 6.06lts, and so far no problems. i also have two other hard drives, and i swap out as needed. one of the drives has a factory fresh (restore cd) install of win me. the other has a fresh install of xp pro (legal copy). and this computer is also a refurb. so make sure that you've burned the ubuntu cd correctly.

---

### Post by DM was on fire! on 2007-08-29
The only thing I can think is a compatibility issue with some type of hardware in your computer. Unfortunately, I'm not sure what. 
Your harddrive (as far as I know) is hda1, with other partitions listed as hda2, hda3 and so on. So...whatever sd0 is might be the problem. 

I didj ust find this article. Maybe it'll give you some ideas?
[http://www.daniweb.com/forums/post401946.html](http://www.daniweb.com/forums/post401946.html)

---

### Post by cubeist on 2007-08-29
I haven't had this problem, but I have had other problems booting linux on may laptop.  I know how extremely frustrating it can be!

The best place to start is boot via the live cd, then run fsck which does a file system consistency check.  This should discover if you have a problem somewhere on the hard drive.

I can't find the tutorial link for fsck (or e2fsck) in my bookmarks, but there are numerous available on the web and these forums.  Just don't run fsck from a mounted file system!!! Make sure to boot from the live cd first!

---

### Post by notwen on 2007-08-29
Are you simply referring to the file system check(fsck) that occurs after 30ish reboots?  If so, that is normal for any machine running a *nix based OS.  This is very similar to scandisk on Windows.  There is a application for Linux, I believe there is a .deb file for it as well, called Bonager that will allow you to postpone your fsck should it be time for one upon next reboot. This process can take a very long time depending on how large your HDD is.  I also think there is a method to change the number of reboots is needed before fsck is invoked.

[FSCK info]("http://en.wikipedia.org/wiki/Fsck")

[Bonager Thread]("http://ubuntuforums.org/showthread.php?t=295262") here on ubuntuforums

If it is something else, good luck w/ it. =]

---

### Post by Hmarroqu on 2007-08-29
As far as hardware, its "INTEL PENTIUM M @ 1.73ghz, 1gb ram, 113gb hdd, and whatever other dandy stuff a 1 year old laptop comes with., according to the site DM showed me my HDD appears as SD0 meaning its  a serial (SATA or SCSI) drive, which i have no idea how to interpret that.  And i am using a CD that was shipped to me by ubuntu.

---

### Post by Hmarroqu on 2007-08-29
Also i would like to mention that i cannot boot from the live CD because of this issue. it just goes to a terminal looking thing, like "safe mode" im guessing.

---

### Post by peebly on 2007-08-29
Ubuntu fiesty works great on my Toshiba satellite A60, saying that I only have ubuntu on it.

Even manages to recognize that the laptop model actually has two separate processors (2 x mobile P4) which I did not think it would for some reason but it did.

---

### Post by schorsch on 2007-08-29
> **Hmarroqu said:**
> heres basically what damn thing says over and over. 

"[########] buffer I/O error on device sr0, logical block ###### "


WHY! i love ubuntu and i NEED it on my laptop for skool! wtf.
As far as I know "/dev/sr0" is used by SCSI CD/DVD ROM drives and not by HDDs. So I would remove the CD/DVD from the laptop, reboot and check if the error is still there. Or just put an ordinary CD in the drive, reboot and check again.
> Also i would like to mention that i cannot boot from the live CD because of this issue. it just goes to a terminal looking thing, like "safe mode" im guessing.
... another hint to a defective CD-ROM drive ....

---

### Post by Hmarroqu on 2007-08-29
well this thing is under a 3 year protection plan, is there any way i can prove its a defective drive? it works fine on windows.  besides, i used to boot off the cd flawlessly before i went for a new (refurbished ) hdd.  now the CD Drive is acting up.

---

### Post by schorsch on 2007-08-30
Apologies that I perhaps led you  on the wrong way .... Have you already started up the computer with a non-bootable data CD in the drive and is the error still there? The drive does not have to be defective but perhaps the error message is misleading you and us ...

---

### Post by Hmarroqu on 2007-09-01
yea, ive booted on windows with a cd in the drive plenty of times.  and i cant boot ubuntu because i cant install it of course :)

---

### Post by schorsch on 2007-09-01
I'd suggest you get the alternate CD and install via the text installer. Get the ISO-image, burn it as an ISO and not faster than 4x speed and try this one.

---

### Post by Hmarroqu on 2007-09-01
well i took it today to the dealer to run a diagnostic, one other thing that may be relevant is that my hdd gets super hot.  im pretty sure its were my touchpad is and that area gets extremely hot, enough to get my hand sweaty. so i took it in to see what they had to say about that. the damn thing is a lemon, its the 3rd time i had to take it in for hdd repair.  are there lemon laws regarding comps?

---

### Post by ramjet_1953 on 2007-09-01
[COLOR="Blue"]schorsch[/COLOR], for your information, the later Linux kernels treat all non-ide HDD's as SCSI devices.

Most HDD's for laptops are not IDE, but SATA, so they are treated as SCSI, hence the sd naming.

Regards,
Roger 8)

---

### Post by Hmarroqu on 2007-09-05
Well, to keep this updated, i took the lap back to the dealer and they "diagnosed" it and will be shipping it to find out whats wrong with it, once again robbing my of my mobile computing.  If there is a problem with the HDD i will most likely get a new one from them since this is the 3rd time and i will also post what the issue was.  if not, i will get a new one cause i will yell and curse on the phone with them.  hopefuily things will work out beautifully.

---

