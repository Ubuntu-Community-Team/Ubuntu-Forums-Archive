---
title: "Please Help!!!"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Link360 on 2006-11-12
When I try to boot my computer this comes up:
"Gnu Grub version 0.97 (632k lower/1046080k upper memory)
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Any where else TAB lists the possible complettions of a device/filename.]
grub>"

if i press tab is it brings up a whole bunch of words that i dont know what to do with.Someone please help. Im in big trouble if I cant get the computer to boot and work properly.Thanks in advance.

---

### Post by Sef on 2006-11-12
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub") to get your computer to boot up again.  It seems as if your GRUB has been corrupted.

---

### Post by Link360 on 2006-11-12
Will this mess up Windows XP. It is my main operating system right now.

---

### Post by Sef on 2006-11-12
It should not mess up your XP; however, if you haven't **backed up** your files, you should do so first.  Nothing is ever 100% guaranteed.

---

### Post by Link360 on 2006-11-12
How am i supposed to back up my files if i cant even get to XP. Plus i dont know how anyway.

---

### Post by Sef on 2006-11-12
Download [Knoppix]("http://knoppix.com").  Plug in a usb pen drive and boot up Knoppix.  Open the hard drive and the usb drive, then drag the files from the hard drive to the usb pen drive.

Note:  If you follow the directions in Restore GRUB, the chance of something going wrong is very small.

---

### Post by kvonb on 2006-11-12
Did you remove the Linux partition?

If so (and you don't want the Linux partition anymore) you need to overwrite the MBR from the Windows boot CD.

---

### Post by Link360 on 2006-11-12
Sef, how do I mount the appropriate partions in the tutorial.

---

### Post by Link360 on 2006-11-12
bump, sorry but I really need some help.

---

