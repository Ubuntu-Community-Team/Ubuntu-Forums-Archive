---
title: "Error 17: grub 1.5"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by wtr_sprts4life on 2006-08-23
Im trying to dual boot windows xp (master), and ubuntu on a secondary harddrive. Help!!!

---

### Post by wtr_sprts4life on 2006-08-23
Sorry i was pretty discreet with my last message. Ive got 2 harddrives, 1 having windows etc on it, then a 2nd which has 3 partitions atm, 1 with alot of music (which i dont plan on losing), 1 with the ubuntu software, & 1 as a swap. when i rebooted after the installation, it says grub 1.5, loading please wait..error 17, and nothing else happens. How do i fix this?

Thanks.

---

### Post by distroman on 2006-08-23
How did you mess it? Did you just install ubuntu?
Anyway not sure, but this works for me, with dual boot as well.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If it's something else and you just want your windows back, you can always do it with your CD. Either with the fixmbr or fixboot commands.
[http://support.microsoft.com/kb/314058/EN-US/](http://support.microsoft.com/kb/314058/EN-US/)
You can find lots of info about it. 
If that do not help you, I am sure someone else can help you, so don't panic. I have messed up my mbr lots of time and as of yet, I have always recovered, by my self or with help.

---

### Post by distroman on 2006-08-23
Just saw your second post,,,
If you just install ubuntu, it could be due, to that you got, windows on one drive and ubuntu on another drive. However that I am not sure about, so if that's it, you should wait until someone else replies.

---

### Post by louieb on 2006-08-23
This is one of the better grub error threads I have found. It explains your error.[http://forums.gentoo.org/viewtopic.php?t=122656]("http://forums.gentoo.org/viewtopic.php?t=122656&highlight=grub+error+collection")
Hope this helps.

---

### Post by distroman on 2006-08-23
You might also want to take a look here -
[http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)
I do believe it's because you installed on separate harddrives. I can't be of much help if that's so.

edit
But you could always physically unplug the drive with the ubuntu install, if you can't fix it. That should give access to windows.
Just as well, as you can format the drive/partition with the ubuntu install. I would do it with fdisk, but maybe there's an easier way. 
Then you can fix windows mbr and get your files.

---

