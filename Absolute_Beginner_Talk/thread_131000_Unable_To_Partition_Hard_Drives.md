---
title: "Unable To Partition Hard Drives"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by comu00 on 2006-02-15
So, I have heard the "good news"; Linux is the way forward. I agree, our school is moving over to "the new way". As if by an act of the Linux gods, at the same time as realising this, my laptop tells me that after running an impromptu "ScanDisk" on windows XP, it informs me that the "system" file had deleted itself. No worries, remember, linux is "the truth". So, I get my mits on the live CD of Ubuntu, very good. Now, follow the screenshots for installing Breezy Badger and I need to sort out my hard drive in order to access my windows files  (music, photos, school work, &c) trough linux which I belive is doable (?). Problem, I can't. 
At the end of the day, it doesn't matter a great deal if I loose it all, I could just delete everything but it would be nice not to.
Any help offered would be greatly received.

Cheers.

---

### Post by alamba on 2006-02-15
Use the live CD to boot, mount your current partitions and copy your data into an external HDD or CD. Post that install ubuntu.

A

---

### Post by kaamos on 2006-02-15
That needs translation..
> Use the live CD to boot
1) burn the iso as an image [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
2) set your computer to boot from cd (press del/f1/f2.. on startup) and boot
> mount your current partitions
Once you have the desktop:
System -> Administration -> Discs
> and copy your data into an external HDD or CD.
If you plug in a usb device, it should show up on the desktop.

Hope this helps.

---

### Post by TrendyDark on 2006-02-15
I'm going to assume that you're running Windows XP, meaning you have an NTFS file system. Linux hates NTFS, fer why? I don't know, but you wont be able to move your files. You might as well pirate a copy of Windows 2000 or XP and make a small, temporary partition to move your files to (FAT32 of coarse).

---

### Post by gord on 2006-02-15
linux can **read** ntfs, so you can copy the data over, but it just can't write in any way that won't mess the partition.

---

### Post by Vengeful Cynic on 2006-02-15
[QUOTE=TrendyDark]I'm going to assume that you're running Windows XP, meaning you have an NTFS file system. Linux hates NTFS, fer why? I don't know, but you wont be able to move your files. You might as well pirate a copy of Windows 2000 or XP and make a small, temporary partition to move your files to (FAT32 of coarse).[/QUOTE]

Trendy, it's very possible to read from NTFS using Ubuntu using native mounting in Ubuntu...  it's the writing part that gets messy.  As to why Linux hates NTFS, let's not go into that, except to say for simplicity's sake that it does not play well with others due to the way MS doesn't like to play nicely with other children.

---

