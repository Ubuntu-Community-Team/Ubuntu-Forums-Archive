---
title: "replace XORG from Live CD"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by galego on 2006-08-14
trying to get xgl-compiz i jacked xorg, now i cant boot into X console. can i replace my xorg file from the live cd? and do i need to have root previledge, and if so how do i get that while using live cd?

thanks for any insight!

---

### Post by sean_ on 2006-08-14
AFAIK, You had to backup your xorg file, If I remember correctly when I installed XGL.

---

### Post by galego on 2006-08-14
yes, however im not sure how to reactivate it. i need to do this from command line since gui will not start.

---

### Post by PriceChild on 2006-08-14
Try to find the backup file:
```
cd /etc/X11
ls
``` This shows me all the files in that folder... including my backup file: xorg.conf.backup Yours may be called something different.

To restore the backup:
```
sudo cp /etc/X11/<<name of backup file>> /etc/X11/xorg.conf
``` 
Which will restore the file. Then xtrl+alt+backspace to try and restart x

((If you can't find your backup file in /etc/X11 then try a "locate xorg.conf"))

---

### Post by sean_ on 2006-08-14
Alright, one sec.

/etc/X11/xorg.conf_backup is the path. Try to type sudo mv /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf

---

### Post by galego on 2006-08-14
thnaks sean and pricechild, that was exactly what i needed. one last question sean, did you use the wiki to install xgl?

---

