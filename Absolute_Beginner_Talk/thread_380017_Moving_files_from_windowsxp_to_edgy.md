---
title: "Moving files from windowsxp to edgy"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-09
Hey!

Today is when I intend to become a ubuntu user, and fully fledged member of this community! I have bought a new hard drive for the occasion. 

My plan is to disconnect my old hard drive (IDE) with windows on, connect my new hard drive (IDE too) with nothing on, and boot ubuntu from a (previously prepared) cd onto the new hard drive. Will this work?

Also, I'm guessing that if I reconnect the old hard drive, the ubuntu os will be unable to read the files I had on my old (windows) hard drive. How do I get these files into ubuntu (docs, pdfs, media files mostly (getting ubuntu to support the formats is not a prority here, I'm fairly sure I can do that))?

Is there a better method altogether? 

Thanks in advance for any help

Griffiss

---

### Post by igknighted on 2007-03-09
Ubuntu ca read windows NTFS fine, and if you install ntfs-3g you write to it too.  Also if you plan to dual boot, theres a driver for windows that lets it read/write linux file systems.

---

### Post by NikoC on 2007-03-09
I really don't see any problems in your plans: when you have installed ubuntu on your new HD, then reconnect you old one you can access it via /media as it will be automounted. I myself have 2 partitions at the moment, one with XP pro and one with Ubuntu. Via /media I accessed the XP partition and copied all files to the ubuntu partition. Best of luck!

---

### Post by Griffiss on 2007-03-09
Ah ok, that's very cool thanks.

---

### Post by igknighted on 2007-03-09
> **Griffiss said:**
> Ah ok, that's very cool thanks.

If you leave the windows disk in at install it will mount it by default.  Otherwise you will have to do it manually later.

---

### Post by Crooksey on 2007-03-09
Yes, ^^ if you leave it plugged in for the Install, Ubuntu will also sort out the bootloader for you, or it will become hassle later.

---

### Post by Griffiss on 2007-03-09
ok, i was just cautious about complications (i've never installed an os before), such as wiping the files off the windows disk, but if it's clear how to prevent this during the install procedure then i guess i don't have to be worried.

thank you both for responding so quickly!

---

### Post by Griffiss on 2007-03-09
you mean dual boot? I'm not really bothered about that, although if it's going to be a lot of work later on and not complicate things now I might as well i suppose...

---

### Post by buuntuu! on 2007-03-09
welcome griffiss!
[Ext2 Installable File System for Windows]("http://www.fs-driver.org/") works fine for me.
read/write-access of my linux-partition (ext3-formatted) from window$. 

> **igknighted said:**
> Ubuntu ca read windows NTFS fine, and if you install ntfs-3g you write to it too. 

i heard, this was still quite experimental, is it stable now??

---

### Post by Crooksey on 2007-03-09
Maybe last year, it works fine on my brothers dual booting machine.

---

### Post by Hallvor on 2007-03-09
It is stable. Works very well.

---

### Post by igknighted on 2007-03-09
> **buuntuu! said:**
> welcome griffiss!
[Ext2 Installable File System for Windows]("http://www.fs-driver.org/") works fine for me.
read/write-access of my linux-partition (ext3-formatted) from window$. 



i heard, this was still quite experimental, is it stable now??

I believe last week the first non-beta release came out (1.0)

@ the OP: Leaving your windows disk attached will only add the complication of selecting the proper disk.  If you know which is which (by size or partition layout or master(hda)/slave(hdb)) you'll be fine.

---

### Post by buuntuu! on 2007-03-09
nice :)

---

### Post by Griffiss on 2007-03-09
right, it won't be difficult to distinguish them. can i clarify though: do i need to install additional software for ubuntu to read the files on the windows disk, or will it just go without me having to do anything?

---

### Post by buuntuu! on 2007-03-09
no extra install needed, read access works out of the box!

---

### Post by Griffiss on 2007-03-09
right that's great, thanks everybody!

---

