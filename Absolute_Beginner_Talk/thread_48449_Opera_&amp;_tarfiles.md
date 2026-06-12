---
title: "Opera &amp; tarfiles"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-12
Hi 

i want to install Opera (browserclient)
i downloaded opera-static_8.01-20050615.1q_en_i386.deb its a tar.gz file

I looked in the ubuntu guide but i saw no instructions either on how to install opera or tar.gz files per se, although there must be instructions for newbies like me on how to do the latter.

Could someone either direct me where to look in ubuntu guide or just tell me how to proceed once i've downloaded the tar.gz from the opera website

many thx

sophtpaw

---

### Post by JaM on 2005-07-12
You should get the **.deb** file **not .tar.gz** file from the opera site (or did you ment that the .deb file was a .tar.gz file, that isn't true it is an .ar file). Then you open your terminal and do:

```
sudo dpkg --install opera-static_8.01-20050615.1-qt_en_i386.deb
```

And then you can launch opera from your terminal with ```
opera
```. You won't see it automatically in the menu because we used dpkq instead of apt-get, but that you can manually change. I don't know how, but searching in the forums for SMEG (Simple Menu Editor for Gnome) will help you further.

apt is the front-end for dpkg, apt retrieves dependencies and updates automatically and let dpkg do the installing removing.

---

### Post by odin on 2005-07-15
Dont know if what was in the previous post worked for you but I downloaded the tarball and did it in another way.

first type.

**tar -xvzf  operapackage.tar.gz**

then

**cd opera directory**
 (after tar you will see a new opera directory named as the tarball but without tar.gz)

and finally

**sh install.sh**


and that should be enough

---

