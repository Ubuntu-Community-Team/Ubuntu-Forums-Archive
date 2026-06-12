---
title: "Removing Feisty"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2008-03-29
I need to remove Feisty from my pc.  The short of it is that it doesn't like my new computer and it's taking up space....How do I safely remove it and get my mbr back to where it should be?

Thanks,
~* Ash

---

### Post by Aquaman420 on 2008-03-29
To remove an operating system you just install another one.  I hope that's what you meant.  Good luck.

---

### Post by .nedberg on 2008-03-29
I just did this on one of my computers. If you are dual-booting with Windows this is what you need to do:

Place the Windows CD in your drive and boot from it. (I used XP.) When given the option press R to enter recovery console (I hade to enter E since I use Norwegian XP, yours may differ). Select the number that corresponds to the Windows installation, probably 1. You will be prompted for admin password if there is one.

When you return to the console prompt just enter:
```

fixmbr

```
Press Y to allow it to rewrite the mbr

Reboot and you will now have just Windows and a spare partition. I used Windows to remove the partitions and then booted the live cd and used QTParted to resize the NTFS partition to span the whole disk.

And; remember to backup...

---

### Post by magnoliablossom on 2008-03-29
Thanks, but that's not what I mean.  I have Feisty on my hard drive along with Vista.  Feisty and my graphics (among other things) just will not work together.  Sometimes I can get it to load, most of the time though I can't.  I don't want to have to reformat my entire hard drive & partitions because I have important business documents, programs, records, etc. on it and I really don't want to have to spend a day copying everything over to dvds.  When I set up Feisty, I gave it much more hard drive space than I did Vista because I only intended to use Vista for business purposes.  But, since Feisty doesn't like my computer as much as it did my old one, everything is being done in Vista now and I need the space.  I know when I reformat the partition that Feisty is on that it's not going to boot to Vista correctly if I don't do something.  I need to know what that something is.

---

### Post by .nedberg on 2008-03-29
With Vista things seems to be a bit different that I first posted.

A quick google gives me [this page!]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html"). It tells you have to restore mbr with the Vista disk. It is what you need!

---

### Post by Duck2006 on 2008-03-29
To repair the MBR you can use the live cd of 7.04

[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)

Not sure to repairing the MBR from with in vista.(i don't use it)
the partition you can get back from with in vista with it's partitioning tool.

---

