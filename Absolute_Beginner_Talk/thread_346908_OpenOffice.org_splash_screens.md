---
title: "OpenOffice.org splash screens"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by goTUX! on 2007-01-26
Hi

Wondering if there is a solution to the below, or if its just something i have to put up with,

I have a dual monitor setup, I can move windows between monitors etc, stretch windows across 2 monitors all fine.

When I open Open Office apps the splash screen sits right in the middle across both screens. Is there a way to stop it doing that, and make the splash display in the middle of the screen that the program loads onto?

---

### Post by goTUX! on 2007-01-26
Anyone?

---

### Post by goTUX! on 2007-01-28
obviously not

---

### Post by lodravah on 2007-02-26
hey

I just saw your post. I was mostly annoyed by the giant splash-screen of open office, so i looked around and found this how - to get rid of the splash altogether.. Don't know if you're still bothered by it, but here it is anyways... 

[http://www.newsforge.com/software/03/04/22/1931223.shtml?tid=51](http://www.newsforge.com/software/03/04/22/1931223.shtml?tid=51)

Only one thing to change. The file you want to change is /etc/openoffice/sofficerc

But if you just follow the how - to and read everything carefully, you should be fine. I hope this is a solution to your problem, at least partly..

---

### Post by Quillz on 2007-02-27
Instead of removing the splash screen entirely, can I change it to something else? 7.04 Herd 4 appears to be using OOo 2.1, but the splash screen still says 2.0.

---

### Post by WishMaster on 2007-05-02
[SIZE=4][B]For Feisty:

[/B][/SIZE] 1) Download (or make your own) splash-screen in .bmp-format.

2) Backup the original splash:
```
sudo mv  /usr/lib/openoffice/program/openintro_ubuntu.bmp /usr/lib/openoffice/program/openintro_ubuntu.bmp_BAK
```

3) Set your own splash:
```
sudo cp <image>.bmp /usr/lib/openoffice/program/openintro_ubuntu.bmp
```

---

