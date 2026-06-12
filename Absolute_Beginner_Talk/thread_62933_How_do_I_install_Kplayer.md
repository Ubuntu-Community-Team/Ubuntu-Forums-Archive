---
title: "How do I install Kplayer?"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-09-06
```
sudo apt-get install kplayer
```

says that kplayer package doesn't exist, I launched kynaptic and searched for it manually, but still no luck. :-?

Should I add something to sources.lst?

If yes, what and where?

---

### Post by KingBahamut on 2005-09-06
Taken from Kplayer.sourceforge.net 

> 
Set up the repositories unless you already have them in your sources.list.

   echo 'deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main'
        >> /etc/apt/sources.list

   echo 'deb [http://kplayer.sourceforge.net/](http://kplayer.sourceforge.net/) ./'
        >> /etc/apt/sources.list

Update the package list and install MPlayer and KPlayer.

   apt-get update

   apt-get install mplayer-k7 kplayer

Replace k7 with 386, 586, 686 or k6, according to your processor type.


Or just install mplayer, because all kplayer is , is a front end for mplayer Im assuming.

---

### Post by Muhammad on 2005-09-06
Thanks again KB. :)

---

### Post by KingBahamut on 2005-09-06
Its all good Muhammad.

---

