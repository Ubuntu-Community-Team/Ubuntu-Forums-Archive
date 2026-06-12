---
title: "aMSN problem can you Help me?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2008-03-18
A problem occured lately with aMSN software 
This Image==1000 words (Greek expression) above
[[IMG]http://img291.imageshack.us/img291/5458/screenshot1bg7.th.png[/IMG]](http://img291.imageshack.us/my.php?image=screenshot1bg7.png)

---

### Post by Achtung on 2008-03-18
What's the problem? It won't connect?
'Cause, it sure looks fine on that picture.

---

### Post by bilal.17 on 2008-03-18
yeah i dont see the problem either

---

### Post by bilal.17 on 2008-03-18
maybe its the size of the font... because if it is you can change it in the preferences of amsn

---

### Post by crjackson on 2008-03-18
> **chemicalgr said:**
> A problem occured lately with aMSN software 
This Image==1000 words (Greek expression) above
[[IMG]http://img291.imageshack.us/img291/5458/screenshot1bg7.th.png[/IMG]](http://img291.imageshack.us/my.php?image=screenshot1bg7.png)

I had the same issue myself a short while back.  I think it was caused when I installed a new video card.  I never did get an answer on how to fix the problem.  Nothing worked. Then one day after installing a bunch of updates, it fixed it's self.  I wish I could be more help, but that's all I got...

---

### Post by chemicalgr on 2008-03-18
Well  it  looks like nvidia is just calculating it worng
so i have to configure by console ,i'm looking for the xorg.conf but i can't find it.

bilal.17 this is an option but not the solution ,i mean this you've said it fixes but not entirely,thanks viva Real MAdrid(lol!)

---

### Post by Claus7 on 2008-03-20
Hello chemicalgr or &#967;&#945;&#943;&#961;&#949;&#964;&#949;!

I do not understand the problem you are facing, because the picture you attach is not clear to me. Yet, as far as the xorg,conf file is concerned do the following:

```
cd /
```

```
find -name "xorg.conf"
```

then you will get probably these (among others):
/usr/share/xresprobe/xorg.conf
/etc/X11/xorg.conf

In case you want to modify something also the command :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
will be of use.

Best of luck with amsn,
Regards or &#967;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by suffice on 2008-03-20
im betting its the font problem....

the desktop fonts look fine butamsn looks like garbage right?

install tcl8,5 and tk8.5  then it will look perfect....

.....

---

