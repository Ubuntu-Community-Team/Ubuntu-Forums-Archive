---
title: "XP, Ubuntu and server 2003 make 3"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by bearglenn on 2006-09-21
Right now I have my computer dual booting, XP and ubuntu on two different hard drives.  It works fine.  What I'd like to do is install Server 2003 on a thrid hard drive (I'm working on a few certs, and would like some hands on) I know the suggested way is to install windows OS's frist and then install linux and all is well.  But I don't feel like redoing all that.  I just got ubuntu where I like it, but just installing server 2003 is going to kill the mbr.  

Is there a way to just add 2003 without it killing everything?
Can I disable hard drives 1 and 2 install server on hard drive 3.  Then re-enable the hard drives then edit grubb?

---

### Post by Totzo on 2006-09-21
yes just go into bios and make the drive you want to install to the first boot drive, then install ..2003. Once finished go back to bios and change it back to your original (grub) drive and then edit  your menu.lst file. remember to do the remap option or 2003 may not boot, good luck! :)

---

### Post by bearglenn on 2006-09-22
Yup,  worked just fine thanks

---

