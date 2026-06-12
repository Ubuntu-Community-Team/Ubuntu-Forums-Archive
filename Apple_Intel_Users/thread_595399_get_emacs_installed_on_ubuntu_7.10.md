---
title: "get emacs installed on ubuntu 7.10"
date: 2007-10-28
forum: Apple Intel Users
---

### Post by xiongm on 2007-10-28
this might be a dumb question, but how can i install emacs on ubuntu 7.10 that i just installed on my mac box ?

apt-get install emacs doesn't give me anything.. 

i know i can always download the source from gnu and compile it. im just curious why ubuntu distro can't even come with a emacs pacakge.. maybe i need to set upt my apt-get config?

thanks

---

### Post by gnaunited on 2007-10-28
Try apt-cache search emacs


Also, don't assume anything.

---

### Post by xiongm on 2007-10-28
apt-cache only gives me a dictionaries-common which is irrelevant, i guess i'll just have to download the source..
thanks for the reply thou

---

### Post by vambo on 2007-10-28
Just go to Add/Remove Programs. There's about four different flavours there!!!

---

### Post by xiongm on 2007-10-28
yes, i tried that, here's what i got:

Emacs 22 (GTK) cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.(which is Macbook Pro + Parallels Desktop )

:-(

---

### Post by vambo on 2007-10-28
Feck! I'm not running on Apple h/w so didn't realise there was an issue. What about just emacs22. There's aslso Xemacs in the repos

---

### Post by meatpan on 2007-10-28
Debian has a nice package browser, which gives pkg names that will work from apt-get:
[http://www.us.debian.org/distrib/packages](http://www.us.debian.org/distrib/packages)

Searching the deb repository is useful for finding packages in repositories that you might not have enabled.

---

### Post by xiongm on 2007-10-28
thanks for the quick reply guys. i didn't find emacs22 in the repository other than the gtk version. i'll try searching the debian packages.

---

### Post by cyberdork33 on 2007-10-28
i just did ```
sudo aptitude search emacs
``` and got tons of matches. You might make sure to enable other software repositories:
System > Administration > Software Sources

Also, this should really have nothing to do with the fact that it is a Mac since it is on a VM. Are you running 64bit or something?

---

### Post by xiongm on 2007-10-28
Bingo!! That solved the problem. I thought it might have something to do with the software source, but just didnt' know where to set it up.. Thanks cyberdork and all the guys who have replied..

---

