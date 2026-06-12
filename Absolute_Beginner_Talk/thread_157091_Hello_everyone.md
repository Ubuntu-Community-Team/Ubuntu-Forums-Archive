---
title: "Hello everyone"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by l0c0dantes on 2006-04-08
Is it possible to make a NFTS Harddrive writeable? I ask this because I have a HD that I use completley for music and what not, and I would like to be able to add to it in linux as well as in windows.

---

### Post by inhuman!!! on 2006-04-08
I afraid not!
Microsoft's NTFS is closed source and as far as I know you can only read, but writing is not possible

---

### Post by wolfee on 2006-04-08
you can do a duel boot with xp and ubuntu on 1 HD. 1st Install xp by deleting entire Hd. After that you want to change the size of the primary partition. Keep in mind you'll need at least 2-5 gigs for Ubuntu if you plan on downloading lots of musicand movies go with 5-10 gigs. Format with quick ntfs and install windows. When your done make sure cd rom is still 1st in boot sequence in your system bios. When Ubuntu asks what partition to format pick the empty one. Make a 2nd partition for the swap file about 512 mb in size. Make sure to load the grub in primary ubuntu partition. after installing ubuntu and rebooting you will see xp as one of the choices for boot os!!

---

### Post by l0c0dantes on 2006-04-08
Thanks for the input, but I'm Afraid I wasnt clear enough. The harddrive I am trying to write to has no OS, and Right now I am dual booting with windows 2k and Ubuntu.

But you menioned a sawp file. I have always made this a few gig big, currently it is 4 gig. Is that too much?

---

### Post by aysiu on 2006-04-08
4 GB of swap is way too much.
I'd think anything more than 1 GB is a waste.

Can't you reformat your NTFS drive as Ext3 or FAT32?

NTFS write support exists, but it's still experimental at this point.

---

