---
title: "Unable to access the cd/dvd-rom"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by sweettea on 2006-09-16
I recently upgraded to Dapper and in the process, can not access the cd/dvd-rom. Ultimately I'd like to read a dvd disk from my handycam as well as cds (music and otherwise).

I've tried:
 (1) clicking on the CD-RW/DVD-ROM Drive and the mount option.
 (2) sudo mount /media/cdrom0/ -o unhide

The result is... nothing. Well, with (2) a password is asked for and then nothing happens and the command prompt is gone. Same thing with (1) but no password request.

Here is the fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0      1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


Much obliged for any suggestions.

---

### Post by sweettea on 2006-09-18
I'm able to access music cds. They just pop-up. Just the dvd that is giving me problems. To clarify, this is not a commercial movie dvd it is a dvd from a handycam that plays just fine in my dvd player. Help?

---

### Post by Brunellus on 2006-09-18
do you have the DVD codecs installed?

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by sweettea on 2006-09-18
Thank-you for your help Brunellus... to answer your question... 

Heavens! No, I don't think so. That is, If it isn't default Dapper then I've not installed it. Am I understanding correctly,  all the packages listed under the "How to Make Things Work in a Hurry", must be installed to get the dvd to work?

---

### Post by xyz on 2006-09-18
I'm not sure the "in a hurry" method is the best. Better take some time to go throug the list as you'll probably need those sooner or later!
Good luck and let us know how it all went!!

---

### Post by sweettea on 2006-09-19
Well I'll be a monkey's uncle - I installed the dvd stuff (as suggested) and it worked! It is all working just fine. Going to tackle the mp3 stuff later. Thanks so much for y'alls help. (Good karma heading your way!)

---

