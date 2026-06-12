---
title: "backing up file system"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-08-12
Hi!

I am thinking of buying a USB HDD [external HDD], but I havnt found a single USB HDD where it says it works with Linux... it always says it works with Win98, WinXP, MacOSX and so on...

how do I knwo it works with Ubuntu?


and another question, if I back my whole system, how can I restore it? Should I install a clean system and restore on it? Wont I get an error when I restore files of the system, like "Cant write file it is in use" like what I get in Winxp?

thnx for your help :)

---

### Post by wieman01 on 2006-08-12
I don't know about your second question, but as for the USB HDD you can buy any external hard-drive you want. Normally the manufacturer don't bother highlighting that they run under Linux since Linux users don't seem to be their target customers.

So don't worry, any external HDD should be ok. I have one as well.

---

### Post by aysiu on 2006-08-12
I have a Lacie external drive, and it works perfectly with Linux.

As for backing up and restoring... it really depends on how you back it up. I would recommend for file backups *rsync*: ```
rsync -av /home/kuraboy /media/usb
``` There's also a graphical frontend for this called *grsync*.

For system backups, I'd recommend PartImage--you'll need a live CD for this. [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by Kuraboy on 2006-08-13
Hi!

thnx for your answers.

I have read the toturial about PartImage, but one thing I dont understand.

Sure I need a LiveCD to restore the files and possibly the MBR table, but why do I need it when I will backup? For example if I want to backup my current  ubuntu drive I dont need the LiveCD right? Or did I miss something?

And about the USB drive, do you recommend it be a Fat32? Beacuse I intend to share forlders with other PCs which have WinXP,and intend to make a system backup of WinXP. 

I am thinking of buying a 400GB external drive will Fat32 work with it?
And how much longer will NTFS be an experimental thing in Linux, do you know?

---

### Post by Tomosaur on 2006-08-13
FAT32 is your best bet for now, yes.

The state of NTFS support in Linux will probably not be regarded as 'full' for quite a while, since the devs are having to reverse engineer everything.

---

### Post by aysiu on 2006-08-13
*rsync* does not need a live CD--only PartImage does.

Oh, and *rsync* won't work with FAT32, only Ext3.

---

### Post by Kuraboy on 2006-08-13
thnx for your answers.

So can PartImage and SimpleBakcup in Ubuntu work with Fat32?!

so what should I do? I cant partion the USB drive... or can I?

---

### Post by aysiu on 2006-08-13
You can partition a USB drive. I think PartImage should work for FAT32--it's just one huge image file, after all.

---

