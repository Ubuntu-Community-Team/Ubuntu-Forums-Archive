---
title: "How do I install fonts?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Magiclamp on 2006-08-14
Hey guys, I am loving gimp as a (free) photoshop alternative, but I wish I had more fonts. I am new to linux, so I don't know how to download/install them. Any suggestions? Thanks a lot!

---

### Post by bruce89 on 2006-08-14
If you are looking for things such as Times New Roman et. al, then
```
sudo aptitude install msttcorefonts
``` will install them, provided you have multiverse enabled.

If you want to install some manually, open nautilus (file manager), and press Control+L.  In the location bar that appears, type in fonts:/// .  You can now put new fonts in there to install them.

---

### Post by Magiclamp on 2006-08-14
thank you very much! I am going to check that out. Sorry to be such a newb! haha.

---

### Post by bruce89 on 2006-08-14
> **Magiclamp said:**
> Sorry to be such a newb! haha.

Everyone is at one point.

---

### Post by bensexson on 2006-08-14
Is anyone else seeing this problem anywhere:  When I try to install msttcorefonts at home it times out whenever it tries to download the font files.  When I try with another computer at work it works fine.

---

### Post by aeiah on 2006-08-14
> **bensexson said:**
> Is anyone else seeing this problem anywhere:  When I try to install msttcorefonts at home it times out whenever it tries to download the font files.  When I try with another computer at work it works fine.

first thing to have a look at is if your source url at work is the same as it is at home. perhaps you've got an old repository address on your home install.

---

### Post by Perfect Storm on 2006-08-14
If you downloaded a font(s) manually (can be found on diffrent font pages. Just put them in .fonts in your home folder. If it doesn't exist make that folder first. Then you can use it with gimp OO2 etc.

---

### Post by bruce89 on 2006-08-14
> **Artificial Intelligence said:**
> If you downloaded a font(s) manually (can be found on diffrent font pages. Just put them in .fonts in your home folder. If it doesn't exist make that folder first. Then you can use it with gimp OO2 etc.

That's just the same as putting them in fonts:///

---

### Post by Perfect Storm on 2006-08-14
Aye, I just found the other way easier (for me). There's alot of ways to do things ;)

---

### Post by Hg80 on 2006-08-14
> **Artificial Intelligence said:**
> If you downloaded a font(s) manually (can be found on diffrent font pages. Just put them in .fonts in your home folder. If it doesn't exist make that folder first. Then you can use it with gimp OO2 etc.


Magic now i can use the Ubuntu font in OO2

---

### Post by noynac on 2006-08-14
Posting deleted.

---

### Post by bensexson on 2006-08-14
It is hitting the same sources.  It seems to be a timeout issue.  It seems to take to long.

---

### Post by bensexson on 2006-08-14
I fixed it my resolv.conf was pointing to my router for DNS and this was taking too long resolve.

---

