---
title: "Booting into OS X automatically?"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by lightningchaser on 2010-01-25
Hello,

I apologize if this problem has already been posted; I've spent some time on the forums looking for it but the closest I could find was people that had the opposite problem.

I'm running a Power Mac G5 Quad on PPC architecture (Mac OS 10.5.8 ) with Ubuntu installed on a separate partition.  Ubuntu works great and it comes in handy quite often, but I still do a majority of my work on OS X.  The problem I'm running into involves the first stage boot prompt, when I restart the computer and it asks me what I want to boot to (Mac or Linux).  I can, of course, just hit "x" to boot to my Mac system but if I do nothing it boots Ubuntu.

I need to know if there's any way to change this so that it automatically boots into my Mac system like it used to do (it started acting this way following a trip to the repair shop).  I prefer to use the old "hold down the option key on startup" thing if I need to boot Ubuntu.

And for some odd reason Ubuntu is not showing as an option under my Startup Disk control panel like it used to either... but my Ubuntu system is very much still present on my second partition.

Any thoughts would be greatly appreciated.

Thanks,
Dan

---

### Post by drs305 on 2010-01-25
Are you running Grub legacy or Grub 2 (or something else)? If Grub, you can tell on the grub menu - Grub 2 will be version 1.96 or higher.

If you are using Grub 2, you can use the guidance in this link to set the default OS: [Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

I believe StartUp-Manager is still capable of setting the default OS in G2, and definitely can in Grub legacy. There is a link on installing and using SUM in my signature line.

---

### Post by linuxopjemac on 2010-01-25
Dear Dan,

this is indeed possible and very easy to. You have to add **defaultos=macosx** to your /etc/yaboot.conf file.

```
sudo nano /etc/yaboot.conf
```

add the line to the file, ctrl-X to exit the editor and say "y" to save.

To make the changes take effect issue a :

```
sudo ybin -v
```

now restart and you should automatically boot into OSX.

---

### Post by lightningchaser on 2010-01-25
Thanks!!  Totally got it working... I did the yaboot edit and that fixed it.  Plus I don't have to hold down the option key on startup if I want to boot to Ubuntu now.

Thanks again to both of you for your advice; I've spent some time looking through the Grub info, drs305... I'll keep that on hand for reference! :)

---

