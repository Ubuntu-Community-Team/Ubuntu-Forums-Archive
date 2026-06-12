---
title: "Copying mp3's from XP, to Ubuntu, back to XP = incorrect file amounts?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-03-31
Hi,

I asked this a little earlier but I am still confused.  

In windows XP Pro I have a music directory (3000 songs in various subfolders).  

While in Ubuntu, (on a different partition), I copied all 3000 songs, converted them from m4a to mp3.  If I do a folder properties search in Ubuntu, it shows all 3000.  

I then copy the converted folder/files (3000) back to windows.  

Heres where it gets strange.  If I check the folder properties, it only shows 1250 MP3's, however, if I do a search of *.* on the folder, it finds all 3000 mp3's.  

What is going on?  Any ideas?  

Should I be converting the songs in ubuntu or should a Fat32 partition work on a USB drive?  

I am very confused.

Thanks,
Rich

---

### Post by Inxsible on 2008-03-31
Do you get any errors during the transfer from Ubuntu to XP ?

does your usb drive have enough space on it to hold 3000 songs? maybe thats why it takes 1250 and discards the rest (although this should give you a warning that the disk is full):confused:

---

### Post by RichTJ99 on 2008-04-01
No I had no errors.  The soundconverter was set to delete the original.  Actually I had a few errors but the original m4a files werent deleted (as the mp3 wasnt written).

I have not used the USB disk yet.  I started all on the same computer with two different partitions.  The other partition has 50 gigs free, so there is plenty of space.

I just used Gparted to format my ext usb drive into a Fat32 drive.  Hopefully that will work.  I will keep you informed.

---

### Post by RichTJ99 on 2008-04-01
That did the trick.  There must be some file issue but easytag + coping to a Fat32 drive (not all the files made it to that drive) fixed the issue.

---

