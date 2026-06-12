---
title: "Hard Drive Mount Problem"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by ChristophorusX on 2005-08-10
Here's the deal ; I have two Hard Drives , on the first one (200GB) I have Windows installed and on the second one (20GB) I have Ubuntu. The thing is is that I want to read a lot of files from Windows via Linux ; but I can't copy them or move them , can someone tell me how to mount the Windows partitions so that become visible in Linux ? I have tried to follow what they said in the UbuntuGuide but it didn't work , so please help guys :D

---

### Post by Lord Illidan on 2005-08-10
The Ubuntu Guide worked for me...

What is the Hard Drive? NTFS or FAT32? Also, it could be that it is not /dev/hda, for example, my windows was in /dev/hdc.

Is the Windows Hard Drive in the primary or in the secondary IDE channel? You can find out by viewing the POST when you bootup..

IDE1
IDE2..etc...

---

### Post by ChristophorusX on 2005-08-10
Both are in NTFS format 

Hehe does WarCraft 3 work on Linux btw ?  :razz:

---

### Post by TristanMike on 2005-08-10
You DO NOT want to write to NTFS. That's DO NOT want to write to NTFS.

Warcraft 3 - Wine, Cedega(emulators). Most commercial games do not have naitive linux installers.

---

### Post by ChristophorusX on 2005-08-10
OK OK I do not want to write to NTFS ...
Yeah I have Wine installed for sometime now I'm gonna try WC3 on it...

---

### Post by tonysathre on 2005-08-10
[QUOTE=ChristophorusX]OK OK I do not want to write to NTFS ...
Yeah I have Wine installed for sometime now I'm gonna try WC3 on it...[/QUOTE]
 to share files between linux and windows create a FAT32 partition

---

### Post by andlinux21 on 2005-08-19
I just want to see the windows drive and play my mp3s from it is that at all possible? :)

---

