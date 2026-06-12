---
title: "Oopsie... :o."
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-27
I've just installed KDE (I've been running Gnome so far) but it looks like it's installed EVERY single possible application for it as well!!! :shock: I've got almost hundreds of applications in my menu... :? 

I only did ***sudo aptitude install kde***... Maybe I should have done ***sudo aptitude install kde-core*** instead? :-k

---

### Post by aysiu on 2006-07-27
In order by size (smallest to largest):
kdebase
kde-core
kubuntu-desktop
kde

---

### Post by ovimunt on 2006-07-27
Right... he he he.. :D So I got the biggest possible...

Well... at least I get to try all these applications now... :-\"

---

### Post by Metacarpal on 2006-07-27
Wow - so there are smaller installs available?  Wish I'd known that before I test-drove Kubuntu-desktop.  lol

---

### Post by aysiu on 2006-07-27
Well, if you did ```
sudo aptitude **update**
sudo aptitude install kubuntu-desktop
``` then it's pretty easy to remove: ```
sudo aptitude remove kubuntu-desktop
```

If you did just ```
sudo aptitude install kubuntu-desktop
``` I'm not sure it will be as easy to remove...

---

### Post by ovimunt on 2006-07-27
Fortunately, just in case something went terribly wrong, I first did an image of my linux partition using Norton Ghost. ;-) So it will be VERY easy to restore to the previous state. :D

Plus, now I have all the deb files so I don't need to download them again any time soon unless anything needs updating. I just need to put them somwhere safe before I restore the partition.

---

### Post by Metacarpal on 2006-07-27
> **aysiu said:**
> Well, if you did ```
sudo aptitude **update**
sudo aptitude install kubuntu-desktop
``` then it's pretty easy to remove: ```
sudo aptitude remove kubuntu-desktop
```

If you did just ```
sudo aptitude install kubuntu-desktop
``` I'm not sure it will be as easy to remove...

Luckily, I had seen your posts about using aptitude to install for easy removal later.  Saved a lot of trouble!

---

