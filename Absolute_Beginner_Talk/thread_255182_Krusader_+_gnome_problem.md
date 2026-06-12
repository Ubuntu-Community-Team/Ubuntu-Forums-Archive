---
title: "Krusader + gnome problem"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by boban on 2006-09-11
Hi!

I've got a problem with bookmarks in krusader (in gnome). When I clik on "Manage Bookmarks" from the bookmarks menu nothing happens. I can add directories to bookmarks from that menu, but I've found no way to delete bookmark other then editing krbookmarks.xml file manualy](*,) ...

---

### Post by Najand on 2006-09-11
krusader is a KDE package, why you want to use it in gnome? KDE packages are usable at gnome but sometimes conflict with Gnome Libraries. Anyway, Gnome has its own file manager called:
gnome-commander

The powerful midnight commander (If you are familiar with norton commander during old days of MS-DOS, it is very useful) is also usable at gnome too.

---

### Post by boban on 2006-09-11
> **Najand said:**
> krusader is a KDE package, why you want to use it in gnome? KDE packages are usable at gnome but sometimes conflict with Gnome Libraries. Anyway, Gnome has its own file manager called:
gnome-commander

The powerful midnight commander (If you are familiar with norton commander during old days of MS-DOS, it is very useful) is also usable at gnome too.

Thanks for your anwser... I use krusader, becouse it is somehow similar to total commander... I've tried gnome commander and mc and I don't like any of them...

---

### Post by Blyzzard on 2006-09-13
I also using Krusader becuase I'm used to Total Commander (Windows Commander) and I have the same problem, I can't manage my bookmarks - I can ADD a bookmark (Ctrl+D) but not manage.

Additionally, the Krusader website indicates Samba support, but when I try access a server on a win network, lets call it "bob" by using smb://bob/public/ then I get a "Protocol not supported bu Krusader"

(and yes, //bob/public/ is shared as other people in my office (who have windows) can access it (oh and i can access it through the "places" menu on my main panel.

Please be gentle, I'm a complete ubuntu n00b and I'm probably messing with stuff that I shouldn't be messing with. :)

---

### Post by boban on 2006-09-19
> **Blyzzard said:**
> 
Please be gentle, I'm a complete ubuntu n00b and I'm probably messing with stuff that I shouldn't be messing with. :)

I think we are getting no answers here - becouse nobody knows what is going on :(. For now - we have to stick with manual edition of bookmarks file...

---

### Post by Books on 2006-09-22
> **boban said:**
> I think we are getting no answers here - becouse nobody knows what is going on :(. For now - we have to stick with manual edition of bookmarks file...

I might have an answer. I just found Krusader and was checking it out before installing. The current version is 1.70.1, and the version in the repositories is 1.70.0. Krusader 1.70.1 was released July 17. Their homepage at [http://krusader.sourceforge.net/]("http://krusader.sourceforge.net/") says that the new version has "A fix for a nasty bug that was plagueing people with gcc 4.x", which is current for our distro.

I'm wondering if this is the reason for your problems?

Books

---

### Post by boban on 2006-09-22
> **Books said:**
> I might have an answer. I just found Krusader and was checking it out before installing. The current version is 1.70.1, and the version in the repositories is 1.70.0. Krusader 1.70.1 was released July 17. Their homepage at [http://krusader.sourceforge.net/]("http://krusader.sourceforge.net/") says that the new version has "A fix for a nasty bug that was plagueing people with gcc 4.x", which is current for our distro.

I'm wondering if this is the reason for your problems?

Books

Thanks! It seems that I have 1.60.1 installed... I didn't noticed it before... Ubuntu repositories contains only 1.60.1... or mayby I just don't know the right repositry for krusader?

I'll check version from sourceforge...

---

### Post by boban on 2006-09-22
> **boban said:**
> Ubuntu repositories contains only 1.60.1... or mayby I just don't know the right repositry for krusader?



Ok... I found another repository for, that has krusader: [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/). I've installed 1.70.1... But the problem is still unsolved - nothing happens when I clik on "Manage Bookmarks" :(

---

### Post by sup on 2006-10-29
you need to install konquror for bookmarks to work and kdebase-kio-plugins for samba etc.
I filed a bug about it:
[https://launchpad.net/distros/ubuntu/+source/krusader/+bug/69016](https://launchpad.net/distros/ubuntu/+source/krusader/+bug/69016)

so add your comments so that developers see that this is bugging people

---

### Post by boban on 2006-10-29
> **sup said:**
> you need to install konquror for bookmarks to work and kdebase-kio-plugins for samba etc.
I filed a bug about it:
[https://launchpad.net/distros/ubuntu/+source/krusader/+bug/69016](https://launchpad.net/distros/ubuntu/+source/krusader/+bug/69016)

so add your comments so that developers see that this is bugging people

Thanks for your help. Bookmarks manager works now :) I thought that I had to work without kruader... I've already commented bug on launchpad...

---

