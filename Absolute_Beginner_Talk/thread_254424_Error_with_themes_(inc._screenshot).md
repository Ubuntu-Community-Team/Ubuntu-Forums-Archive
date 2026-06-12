---
title: "Error with themes (inc. screenshot)"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by BoyBlunder on 2006-09-09
whenever I click on a valid theme to use it (it's been installed correctly), I get the following error (see attachment)

it happens as soon as gnome starts changing things over to the new theme.

any idea what's up?

---

### Post by powder on 2006-09-09
Can't see sh*t, Captain!

---

### Post by BoyBlunder on 2006-09-09
hehe, just added the attachment :]

---

### Post by jordanmthomas on 2006-09-09
Have you set the GTK to QT in KDE / Kcontrol by any chance?  If so, change it back to the blank line at the top

**edit**
I see you got your XGL working since yesterday?

---

### Post by powder on 2006-09-09
Never seen that before.  What theme are you choosing?  Are you using XGL/Compiz?

---

### Post by BoyBlunder on 2006-09-09
yea, after some tweaking, I've gotten my nvidia drivers loaded so I'm using XGL. this happens with ANY theme, not just a new one that's been recentely installed.

---

### Post by jordanmthomas on 2006-09-09
...have you been using KDE?

---

### Post by powder on 2006-09-09
Not sure, but I think the default themes are not compatible with Compiz.

I would try installing a Compiz theme from [http://www.gnome-look.org](http://www.gnome-look.org) and see if that works.

---

### Post by jordanmthomas on 2006-09-10
I had this same problem for a while.
Powder, those are only for compiz installations from quinn that use cgwd.  His looks vanilla to me.  

Bah, who knows?

---

### Post by powder on 2006-09-10
Yeah, I don't run XGL/Compiz myself, but it sounds like a likely culprit here.

---

### Post by jordanmthomas on 2006-09-10
I really don't think it's an error with compiz
I am thinking it is a GTK / QT conflict

We'll just have to wait and see...

---

### Post by BoyBlunder on 2006-09-10
well, I downloaded a compiz theme and went I went to the theme manager to install it, and before the theme manager even came up, I got the following error: [http://img180.imageshack.us/my.php?image=screenshotwl8.png](http://img180.imageshack.us/my.php?image=screenshotwl8.png)

should I try to start the daemon from terminal?

edit:

did a reboot and the theme manager worked. however, I need to install:

gcompizthemer and cgwd, aiglx or xgl, compiz-quinn 

to get them to work. apt-get doesn't show anything so where can I get these?

---

### Post by BoyBlunder on 2006-09-10
found this: [https://launchpad.net/distros/ubuntu/+source/bonobo/+bug/56890](https://launchpad.net/distros/ubuntu/+source/bonobo/+bug/56890)

does this mean anything? sounds very similar to my problem.

---

### Post by jordanmthomas on 2006-09-10
Try deleting 
```

.gtk_qt_engine_rc
.gtkrc-1.2-gnome2
.gtkrc-2.0

```

from your home folder, logging out, and then logging back in.  
(Or maybe you have fixed this already??)


[http://xgl.compiz.info](http://xgl.compiz.info)
This is where you can get cgwd, etc.

---

### Post by aeon on 2006-09-10
i had the same problem a while back, what i did was reinstall compiz from quinnstorms repo's and installed cgwd, that fixed it for me atleast

oh, and i have a vanilla dapper install

---

### Post by BoyBlunder on 2006-09-10
what's a vanilla dapper install?

as for deleting the files, i'm gonna do that right now.

---

### Post by jordanmthomas on 2006-09-10
A vanilla dapper install would be one that is basically the same as when you install it from the CD.  Meaning, not much extra has been installed / tweaked.

---

### Post by BoyBlunder on 2006-09-10
Jordan,

I tried to delete those files, but the only one that was there was the 2nd one, .gtkrc-1.2-gnome2

I'm going to head over to the compiz site and install cgwd, etc.

I'll keep you guys updated.

---

### Post by BoyBlunder on 2006-09-10
this is what I get when I try to apt-get cgwd:

```
pat@xps:~$ sudo apt-get install cgwd
Reading package lists... Done
Building dependency tree... Done
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate

```

---

### Post by BoyBlunder on 2006-09-10
this is the error I get when trying to install compiz-core:

```

trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
dpkg-deb: subprocess past killed by signal (Broken pipe)

```

this issue is driving me up a wall!

---

### Post by jordanmthomas on 2006-09-10
I think the problem is that you have vanilla compiz installed so you need to remove it before you can install quinn's compiz.  (Though I'm sure it will break your heart)

I'm not certain, but cgwd may be part of compiz-core now and you may not need to explicitly install it.  I'm not sure...you may have better luck on the compiz forums
[http://compiz.net](http://compiz.net)

---

### Post by BoyBlunder on 2006-09-10
alright, after some googling, I've gotten rid of that error by using a:

apt-get install -f

it removed the initial compiz that was there, and i ran compiz-core_0.0.13.37-0ubuntu4_i386 and it installed.

*crosses fingers while installing all the other packages*

---

### Post by BoyBlunder on 2006-09-10
got everything working now! only one issue left: when I go into the CGWD Themer and I click on a theme, nothing happens. is there a startup script I should add somewhere?

---

### Post by jordanmthomas on 2006-09-10
try running 
```

cgwd --replace

```

---

