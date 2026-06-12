---
title: "dvd rip"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-08-01
I want to make copys of my dvds is there a player that will play.vob file or do i have to convert to avi 
and if so whats a good program for that

---

### Post by tylerjroach on 2007-08-01
VLC media player should play your .vob files

---

### Post by C.S.Cameron on 2007-08-02
What about DVD Decrypter (3.5.4.0), followed by DVD Shrink 3.2 (if the decrypted stuff is too large to fit a DVD).

---

### Post by tylerjroach on 2007-08-02
Are you using Windows or Linux. If you are in Windows I would use dvd shrink to shrink the dvd. I think it is easier to find the files you want to shrink. I would use dvd decrytptor as a second option. Are you wanting to keep them on your computer or burn another disk. If you plan on burning another disk save the file as an iso instead of .vob files. VLC can also play .iso files if you just want to use that. If you want one big .vob file make sure you tell dvd shrink not to split the vob files so you have a continuous movie

---

### Post by ramjet_1953 on 2007-08-02
Provided you have the proper codecs installed, a good combo to install is

1.[COLOR="Blue"] k9copy[/COLOR]
This allows you to compress DVD9's to DVD5, with no noticible loss of quality.

[COLOR="Red"]sudo apt-get install k9copy[/COLOR]

2. [COLOR="Blue"]k3b[/COLOR]
This is a great burning application for CD's and DVD's.

[COLOR="Red"]sudo apt-get install k3b[/COLOR]

Both are KDE applications, but work well under GNOME.

It is best to just use k9copy to create an iso, and then use k3b to burn it, as many people have problems with its auto-burn function.

Regards,
Roger :cool:

---

### Post by tylerjroach on 2007-08-02
O sorry I understand what you want now. Use a program like DVD shrink and then shrink the disk into an .iso format instead of .vob. Then you can use dvd decrytor to burn the disk

---

