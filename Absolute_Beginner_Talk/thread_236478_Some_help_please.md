---
title: "Some help please"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by oldun on 2006-08-14
I am an absolute newcomer to Ubuntu Linux,
I have received the disk with both installation and "run from cd" versions. I need to know the followingto assist my decision to install this software:
[1]Can I run my present Xp from the same HD.
[2]Will the install program set the HD up so that I can run  either Windows Xp or Linux by selecting the one desired at boot time?.
[3] If at some time in the future I wished to revert to Windows only how easy is it to revert back?
[4] I use "Acronis tru image to image the entire C: drive as a backup routine, will I still be able to do this for both the partitions which will be created if I install Linux.
[5]Is there an equvialent Open souce program for linux to the microsoft "Front Page"?
I will appreciate any help you can give me.

---

### Post by xpod on 2006-08-14
1....YES
2....YES
3.....YES...not sure how easy
4.....Not sure but probably....it`s got everything else AND more.

DEFRAG DEFRAG DEFRAG your xp first and just follow the prompts and you should be fine once you start the install procedure.

Someone else can give you more detailed help if you get stuck...Good night and good luck

---

### Post by durableapostle on 2006-08-14
yes
yes
yes
not sure--but almost assuredly yes
yes--NVU

---

### Post by goatflyer on 2006-08-14
1. yes, its called dual booting.  there is a howto written about it, but you can probably succeed without reading it, since the install grub will automatically detect the windows os and ask if you want to keep it.


2. yes, grub will start up with a menu that lets you pick either.

3. to revert back, you run fixmbr from windows. this will overwrite the grub bootloader mbr.  You will then have to use something like partition magic to reclaim/readjust your partition space.


4. if you like, during install create more than 1 partition.  Keep one for /home, another of equal size for backup purposes.  You can do a sector-by-sector copy using dd  (a command line utility).  there may exist a gui-way of doing it too, I don't know.

5. a good list of 'windows equivalent' linux programs is here:

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)


PS. sometime soon after installing, I would heartily recommend following the instructions to install and run the automatix script - it automatically sets up all the codecs, adobe, flash, etc.

---

