---
title: "New Install"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-01-20
Im new to ubuntu and  im thinking of intsalling it on a new SATA hard drive im getting this week.
I was just wondering if its possible to clean install ubuntu to the new SATA and set that to boot first and run that as my pirmary OS and use my old IDE that still has windows on it as a slave so i can still listen to MP3 files etc off that?

---

### Post by lizzard on 2008-01-20
You can! During Ubuntu installation a bootmanager called "GRUB" will be installed which gives you the choice what OS will be booted on start up.

---

### Post by Malta paul on 2008-01-20
Hi, I have both a ATA and a SATA HD drive fitted and they both work great:guitar:

---

### Post by Tek-Noir on 2008-01-20
Cool, so it wouldnt mess up any of my windows files and id be able to acccess them from ubuntu then?

---

### Post by Malta paul on 2008-01-20
Correct it will not damage your MS files and you will be able to access them, but do back up your files as a precaution :)

---

### Post by Tek-Noir on 2008-01-20
Excellent, thanks very much. Really looking forward to using ubuntu.

---

### Post by traderpats on 2008-01-20
Definitely do the backup.  That's computer 101 that too many ignore and it comes to bite them.  The only thing is if you uninstall Ubuntu you'll have to boot with the Windows disk and restore the MBR to be able to boot into a Windows only machine.  I've done this plenty of times without any problems.  However, just to be on the really safe side I dual boot using Linux on an external hdd.  That is, if the external drive is on when the computer boots GRUB will load.  You'll still have access to the ntfs partitions on the internal drives and you don't have to mess around with your MBR.  Just another way of doing things.

---

### Post by Tek-Noir on 2008-01-20
Would it be ok to disconect the IDE with windows on it before i install ubuntu to the SATA, then after its all installed connect the IDE so i could use ubuntu without changing the MBR and not bother about dual booting for the time being?

---

### Post by Malta paul on 2008-01-20
Hi, Yes you can disconnect your HD drive as you said.(I did that the first time) When connected up again you will then have to configure Grub if you want to duel boot to Windows, and you will have to configure Ubuntu to mount the other drive.
Either way will work, the first post is perhaps the simplest.
Heres a reference you may like:[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Post if you need more help  :)

---

### Post by emarkd on 2008-01-20
Having Windows and Ubuntu on different drives or partitions gives you lots of flexibility.  After you get Ubuntu installed, you could look into booting your Windows drive in VMWare, allowing you to run Ubuntu and Windows at the same time!  Then, you have access to all of your windows software (except maybe full-screen games) while Ubuntu is running.  I have this setup on my laptop and can boot into windows from VMWare and then maximize it on one side of my Compiz cube, so my cube has Ubuntu on three faces and Windows on the other.  Flicking back and forth is as simple as scrolling the mouse wheel.  Watching my friend's faces is the best part!

After you get your Ubuntu installed, a google search for booting a partition in VMWare will net you lots of good information if you're interested in this.

PS.  This doesn't work well at all for most games.  You'd still have to shut down and reboot directly into Windows to play games.

---

### Post by Tek-Noir on 2008-01-20
Nice one ill give that a go.

So is it possible to access your own windows partition through VMWare and use apps off that if you need to? I thought you had to install windows on to it.

---

### Post by Tek-Noir on 2008-01-20
anyone?

---

### Post by emarkd on 2008-01-20
absolutely.  you don't have to reinstall windows inside vmware.  vmware is quite capable of booting a partition or drive instead of a "virtual drive".  you can boot your existing windows installation from vmware running inside ubuntu.

NOTE:  before you just install vmware-player and boot your existing windows installation, do a google search and read a bit.  you'll have to set up two hardware profiles in your existing windows because vmware emulates very different hardware than your computer actually contains.  booting that existing windows partition without prepping it first will confuse it mightily.

---

### Post by Tek-Noir on 2008-01-21
Brilliant, ill give that a go. Thanks again for all the help :)

---

