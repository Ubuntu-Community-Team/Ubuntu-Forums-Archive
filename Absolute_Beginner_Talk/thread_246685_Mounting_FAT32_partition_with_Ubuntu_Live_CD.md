---
title: "Mounting FAT32 partition with Ubuntu Live CD?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Noutro on 2006-08-29
Hello!

Can you help me?

I got into trouble when I tried to install Ubuntu 6.06.1 (Desktop CD). In order to recover my system I need to know:

****************************************
* How can I mount a (FAT32) partition  *
* when running Ubuntu Live CD?         *
****************************************

What happend:
-------------
I successfully started Ubuntu Live CD 6.06.1 and wanted to install Ubuntu to my system. During installation the installer crashed (bug in ubiquity).
Now XP doesn't start anymore. During startup I get the message "Error loading operating system". I already read a lot about this failure and try now to recover the system by using an image file of my C:\ drive which I had made before the system crashed.
The image of the C:\ drive is on a notebook which I already can access via FTP using Ubuntu's gFTP. So, left for me to know is how to mount my D:\ drive (FAT32) to the running Unbuntu Life system. The crashed computer has access to the internet via Ubuntu Live CD.

Thank you in advance for your effort.

Martin

---

### Post by PPAAUULL on 2006-08-29
I had the same problem. What I did to fix it was try to install Ubuntu again. After it installed flawlessly I was able to get back into windows XP with nothing lost. Gave me a real scare though.

Paul

---

### Post by Noutro on 2006-08-29
Thank you Paul, that gives me a hope.
So I will try to install Ubuntu with the help of Ubuntu Launchpad.

---

### Post by PPAAUULL on 2006-08-29
I hope it works out for you and doesn't turn you off of Ubuntu.

Paul

---

### Post by Toxicity999 on 2006-08-29
Read up with:
man mount

See if you can't piece together the line yourself, the Filesystem is vfat I believe. That is if you still want to go this route, discovery is the best form of learning after all.

---

### Post by Noutro on 2006-09-04
Pauls advice has been successful!!
I could install Ubuntu when I switched from Live CD to Alternate CD. I had no problem at all during installation and after successful installation also XP can be started as usual. There are no problems left. Thank you Paul, you told me the right way!

---

