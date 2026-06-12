---
title: "Permissions problem (i Think)"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by anabelle on 2007-03-26
Hi, i just installed a new harddrive to manage downloads, since they are getting big, and i have it mounted on /media/downloads

ive granted acces to all users and groups ( sudo chmod 777 /media/downloads )

And its working almost fine, but when i try to start a new download in ktorrent i get 

"No se puede crear el enlace simbólico de /media/downloads/tor0/cache a /media/Downloads-Temp/Ktorrent/Waking.Life.LiMITED.DVDivX-QiX.avi: OperaciÃ³n no permitida" 

I can't guess what is wrong can somebody help me?

---

### Post by cowlip on 2007-03-26
Can you try to chown /media/downloads?  /media/downloads might be owned by root (which you can check by doing 'ls /media/downloads')

chown putyourusernamehere:users /media/downloads

or,

chown putyourusernamehere:putyourusernamehere /media/downloads

I'm not very good with permissions but maybe someon else can help..

---

### Post by aysiu on 2007-03-26
One of these should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by anabelle on 2007-03-26
Thankyou i've done the changes in fstab and now my partitions are totally writable but Ktorent is still unable to create the simbolic link (enlace simbolico).

What else may be wrong?

It says operation forbidden (operacion no permitida)

---

