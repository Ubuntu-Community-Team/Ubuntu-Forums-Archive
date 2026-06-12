---
title: "Default file system browser"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by wireless on 2007-05-11
Hi all
Im running ubuntu 7.04 + kde (working on kde most of the time) 
Wondering which is the compnent that decides which browser will fire up when automount occours. becouse when automount for my external harddrive occours it fires up both nautilus and konqueror.. very confusing
any hint?
thnx :)

UPDATE:
ok so i updated hal and now it dosnt open up nautilus, instead it took me back to my original issue which i allready posted and still no FIX.. my usb devices doesnt automount:| except the sd slot i have in the thinkpad x60 laptop.. 
Dudes I love ubuntu and wouldnt replace it even if i had to mount everything manually but still .. wtf with this automount issue! :)

---

### Post by Martin on 2007-05-11
There's a lot of stuff about the automount problems. I guess when you say "..my usb devices..." you mean drives, not cameras and stuff? The problem I had with automount was down to an incorrect entry in the fstab file (/etc/fstab). I did fdisk -l both with a drive connected and without.
When I connected a drive and did fdisk -l I noticed that the drive was being referred to a ....sdb3... and I could mount it manualy using the mount command. I then took a look in the fstab file and found a line referring to sdb3. I figured that an explicit entry in the fstab would contradict what automount was doing so I commented it out. Since then automount has worked fine. Hope this helps. If you are using ntfs usb drives be sure to install the NTFS Configuration Tool as without it you'll battle to have write access to the drives.

---

