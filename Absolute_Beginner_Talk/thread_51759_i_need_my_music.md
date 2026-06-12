---
title: "i need my music"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by maybevampires on 2005-07-25
after much deliberation and fore-thought i decided to take the plunge and completly move to linux from windows, the problem i am having is i have a secong hd i used mainly for storage its ntfs format and i cant seem to access it, i'm quite scared by the fact i might have completly wiped the drive but i cant get into i to see. any thoughts?

---

### Post by glandula on 2005-07-25
[QUOTE=][/QUOTE]
 look here [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) :)

---

### Post by odin on 2005-07-25
If I understood right you had ane hd with windows and the other one for storing thing and one you "saw the light" and move to Linux so you installed ubuntu in the hd whre you had windows.If that is your situation you should have acces to the other hd just by mounting it.

First you need to know what is the second hd "called".I supose you have ide hd so If it is pluged in the 1 channel as slave it should be /dev/hdb.If it the master of the second channel /dev/hdc and if it is slave in the second channel /dev/hdd.I guess /dev/hda is where you installed ubuntu.

So knowing this just :sudo mount /dev/hd? /where/ever/you/wanna/mount/it/to

and if you wanna mount it every time you boot just edit /etc/fstab and add this line:

/dev/hd?     /wherever/you/wanna/mount     ntfs  defaults 0 0

and that's what I can tell you. :grin:

---

### Post by maybevampires on 2005-07-25
thanks for the help i was frustrated and sleepy when i posted thank you

---

