---
title: "Show-stoppers? Tell me no!"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by hovmod on 2006-02-26
I have found two things that might put me off this delightful Ubuntu experiment altogether: 

1 - NTFS is read only. Is that really true? I can't have hundreds of gigabytes of files on display only. That's just not on. So help me: how do I make my ntfs-partitions r/w?

2 - I use my computer to make music. My Midisport 2x2 usb interface seems to be a bit of a riddle. So far I've found one driver that *might* work, but not without putting some new firmware in the unit - and nowhere does it say whether or not the Midi-interface will work in Windows after the upgrade, so that's a no go. Hasn't anyone made a Linux driver for it that doesn't require a firmware upgrade?  Or can anyone tell me whether it'll work in Windows?

Again, please guys, help me find a way to keep using Ubuntu. I really want to, but with readonly  access to my data and no MIDI input it would be for entertainment purposes only, and I don't have time for that...

Any tips and tricks?

---

### Post by Coelocanth on 2006-02-26
I believe there's a way to read and write to an NTFS partition, but I've read it's rather unreliable and runs a large risk of corrupting the data. One way to do it might be to create a FAT32 partition and copy your files there. Ubuntu can read and write to FAT32, as can Windows. Not an elegant solution, but it should work.

I've no idea on your second question.

---

### Post by hovmod on 2006-02-26
Thanks. Hm...

O..K..

Bit disappointed...

I'll google it up somewhere. Gotta be a way...

:)

---

### Post by rfruth on 2006-02-26
A driver that *might* work, but not without new firmware for the BIOS, video card, audio card, what ?  Sorry I don't have the answer but narrowing it down would help ...

---

### Post by aysiu on 2006-02-26
Unless you have files larger than 4 GB (say, DVD backups), then FAT32 should be a good filesystem to share between Ubuntu and Windows, something like:

Partition 1 Windows (NTFS)
Partition 2 Data (FAT32)
Partition 3 Ubuntu (Ext3)

---

### Post by hovmod on 2006-02-26
[QUOTE=rfruth]A driver that *might* work, but not without new firmware for the BIOS, video card, audio card, what ?  Sorry I don't have the answer but narrowing it down would help ...[/QUOTE]

Sorry - the Midisport 2x2 is a little box that has two midi ins and two midi outs, plus USB to the computer. This is the unit that apparently needs firmware.

---

### Post by az on 2006-02-26
NTFS is proprietary and closed source.  They actually change the specifications of it from time to time.  That's why you can't relicable write to it from linux.

---

### Post by Jucato on 2006-02-26
This NTFS-Read-only behavior is not unique to Ubuntu alone, but to all Linux distributions out there.

There reason behind this is that Microsoft doesn't want to share. The NTFS file system specification is known only to Microsoft, so other systems would not know how to write on them properly. That is why writing to NTFS directly is unsafe, unreliable, and not recommended. It isn't really Linux's (or Ubuntu's) fault, anyway. :D

EDIT: haha! azz beat me to it. :D

---

### Post by hovmod on 2006-02-27
OK, I appreciate your replies.

I'll convert my data-disk to FAT32. That'll give me an excuse to clean it up a little as well, I suppose.. :)

I appreciate your help.

---

### Post by newuser111 on 2006-02-27
you can try captive ntfs if you really want to write to ntfs, its supposed to be the safest way, but slow

---

