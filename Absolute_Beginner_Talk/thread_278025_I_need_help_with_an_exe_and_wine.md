---
title: "I need help with an exe and wine"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-15
Ok so I opened a .zip with the archive manager and now I have an exe. Only, I dont know what todo with this exe now. Im trying to get this:
[http://www.snapfiles.com/download/dlstickfigure.html](http://www.snapfiles.com/download/dlstickfigure.html)

I have wine, and I understand that I need to get it into there, but couild someone help me out with getting it into there please. Thanks.

---

### Post by taurus on 2006-10-15
From a terminal, 

```
wine <filename>.exe
```

---

### Post by theturtlemoves on 2006-10-15
Wine should have come configured with your Ubuntu install already. If not, type:

```
sudo apt-get install wine
```

Then unzip the file into a directory (such as /home/yourusername/) and open up a terminal and change to that directory.

Then type:
```
wine applicationname.exe
```

With any luck, it should work.

---

### Post by markg729 on 2006-10-15
i also just installed wine, but when i open an exe using the terminal with "wine <name>.exe it shows an error message that says 
"The X11 driver is missing.  Check your build!"
how would i go about getting this driver?

---

### Post by voodoonirvana on 2006-10-15
> **taurus said:**
> From a terminal, 

```
wine <filename>.exe
```

I thought that was only if you already have it in wine. I dont even have it in wine yet.

---

### Post by taurus on 2006-10-15
> **voodoonirvana said:**
> I thought that was only if you already have it in wine. I dont even have it in wine yet.
:confused:  :confused:  :confused: 

If you want to run some Windows apps in Ubuntu, .exe, you first need to install wine which is a emulator.  Then, you run those apps, .exe, with wine...  I am not sure what you mean when you said "I don't even have it in wine yet!"

---

### Post by voodoonirvana on 2006-10-15
> **taurus said:**
> :confused:  :confused:  :confused: 

If you want to run some Windows apps in Ubuntu, .exe, you first need to install wine which is a emulator.  Then, you run those apps, .exe, with wine...  I am not sure what you mean when you said "I don't even have it in wine yet!"

Well I have wine, and I am positive of that. And what I meant by already having it in wine was that I thought wine was basically a fake C drive. Dont you have to have an exe in this fake C drive in order to run it? Or am I just missing/overlooking something really stupid.

---

### Post by taurus on 2006-10-15
Maybe this link helps...

[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)

---

### Post by voodoonirvana on 2006-10-15
Hey I got it figured out! It was just a really stupid mistake like usual:rolleyes: 

Thanks though!

---

### Post by SuperGrover21 on 2006-10-15
Hey, no mistakes! This here newbie learned a lot from your tread! Thanks all.

---

### Post by tparker on 2006-10-15
Hey, don't feel bad, you aren't alone! I just figured this out myself about an hour ago.

I found lots of pages and posts letting me know that the windows programs needed to be run in wine, but nothing explaining that all I needed to do for that to happen was type 'wine' before the file name. I spent better than three hours today trying to figure out how to move the .exe file I was working with into a wine folder or directory or something so that I could try to use it -in- wine. I felt like an idiot at first when a friend told me what my problem was, but I guess that's just part of the learning process. :)

---

