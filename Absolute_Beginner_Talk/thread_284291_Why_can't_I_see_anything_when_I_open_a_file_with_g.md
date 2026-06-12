---
title: "Why can't I see anything when I open a file with gedit"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by langhi on 2006-10-25
I am trying to make so adjustments to my graphics drivers and I am following the steps in Ubuntu Unleashed 

sudo gedit /ect/x11/xorg.conf

but when this file opens up or any other file I open up in a terminal windows for that matter comes up blank.  Yet I can check the file to make sure that it has content using file manager and see that it does.  What simple steps am I missing?

Thanks in advance.

---

### Post by TitusDalwards on 2006-10-25
becauae you wrote wrong, true path is /etc/X11/xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Bachstelze on 2006-10-25
Please use gksudo instead of sudo to run GUI apps as root. Or even better, don't run GUI apps as root at all when you can avoid it. You have plenty of nice command-line based text editors like vim or nano.

---

### Post by Henry Rayker on 2006-10-25
Just to chime in...the reason you got a blank file is because Linux is case sensitive... x11 isn't the same as X11

---

### Post by langhi on 2006-10-25
Thanks for all the prompt answers, the case sensitive one is the one that will help me the most while I will definetely use the advice you other provided as well. Thanks

---

### Post by TitusDalwards on 2006-10-25
> **HymnToLife said:**
> Please use gksudo instead of sudo to run GUI apps as root. Or even better, don't run GUI apps as root at all when you can avoid it. You have plenty of nice command-line based text editors like vim or nano.

cuold you please explain the diffrence between sudo and gksudo i looked it up [here]("https://wiki.ubuntu.com/DesktopTeam/GksudoChanges?highlight=%28gksudo%29")but  i didn't understand anything

---

### Post by CatKiller on 2006-10-25
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by TitusDalwards on 2006-10-25
thanks lot CatKiller

---

