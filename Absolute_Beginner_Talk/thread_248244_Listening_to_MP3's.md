---
title: "Listening to MP3's"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-08-31
Hi, Im have a dual boot system with Windows XP  and Ubuntu. I am trying to listen to my MP3's that are saveed in the my music folder on my desktop in Windows XP. I can see this folder when I am logged in  Ubuntu but the folder is empty. Am I looking in the wrong spot , or is this just not possible with a dual boot system, do I just have to download music when im in Ubuntu for it to run when im in Linux?

---

### Post by %hMa@?b&lt;C on 2006-08-31
edit: forgot about NTFS driver need.

---

### Post by slibuntu on 2006-08-31
As a general rule, you can't use files from Windows from Ubuntu, or vice versa, the 2 OS's use different filesystems, NTFS for XP and Ect3 for Ubuntu. There are work-arounds, to use files from Ubuntu on XP look at [www.fs-driver.com](www.fs-driver.com) , and for using XP files on Ubuntu, which seems to be what you are attempting, try this thread : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by %hMa@?b&lt;C on 2006-08-31
> **slibuntu said:**
> As a general rule, you can't use files from Windows from Ubuntu, or vice versa, the 2 OS's use different filesystems, NTFS for XP and Ect3 for Ubuntu. There are work-arounds, to use files from Ubuntu on XP look at [www.fs-driver.com](www.fs-driver.com) , and for using XP files on Ubuntu, which seems to be what you are attempting, try this thread : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

do'h I forgot about that, last time I used windows, I had it Fat32 formatted. Sorry.

---

### Post by slibuntu on 2006-08-31
Yeah, I can report that fs-driver definitely works, and very well, i haven't tried Givré's howto yet though, so use at your own risk!

---

### Post by HdK on 2006-08-31
Ok sorry i meant mp4's is there any special codecs for  xmms player

---

### Post by HdK on 2006-08-31
For some reason I got the mp3's to play without even getting the fs driver.

when i type this gksu gedit /etc/apt/sources.list into the terminal I get this  GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by slibuntu on 2006-08-31
your hd might be fat32, anyway, for mp4, try using synaptic package manager to install "w32codecs"

EDIT Actually, just go onto this site [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by HdK on 2006-08-31
I can only see the files of my win xp partition when i sighn in with gnome not KDE :sad:

---

### Post by LKRaider on 2006-08-31
Ubuntu can access NTFS drives without problems (but in read-only mode), no need of external tools to read the drives.

You might be looking at the wrong folder there most probably.

---

### Post by slibuntu on 2006-09-01
Of course, that slipped my mind, sorry! You only need ntfs-3g to write to your Windows files

---

