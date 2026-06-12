---
title: "totem and codecs"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-07
ok where do i get codecs such as
#

gstreamer0.10-ffmpeg
#

gstreamer0.10-pitfdll
#

gstreamer0.10-plugins-bad
#

gstreamer0.10-plugins-bad-multiverse
#

gstreamer0.10-plugins-ugly
#

gstreamer0.10-plugins-ugly-multiverse

and how do i install them... I've read all kiinds of stuff but i just don't get it... thanks

---

### Post by taurus on 2006-09-07
Use BUMPS to install them...

[http://www.ubuntuforums.org/showthread.php?t=181248](http://www.ubuntuforums.org/showthread.php?t=181248)

---

### Post by harlan on 2006-09-07
Do this: $ sudo gedit /etc/apt/sources.list
Then delete the # before the lines starting #deb... and save the changes.After that $ sudo aptitude update 
and install all those codecs
$ sudo aptitude install nameofthecodec

---

### Post by Devile on 2006-09-07
Ok i kind of get it, but i will jsut donwload bumps and install it but i can't figure out how to install it

---

### Post by Dinerty on 2006-09-07
Could use "Synaptic Package Manager"  :)

---

### Post by Devile on 2006-09-07
ok well i downloaded the BUMPS fodler then opened it and ran the BUMPS file exe type file in there and it seemed to run but i don't know if it finished or if it worked...

but totem still won't play .mov

---

