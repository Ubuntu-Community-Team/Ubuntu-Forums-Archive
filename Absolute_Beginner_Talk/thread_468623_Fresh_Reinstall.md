---
title: "Fresh Reinstall?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by phollos on 2007-06-09
After getting my first taste of linux I've realized that I've really mucked up my install with tons of useless apps when I was first trying things out.

I'd really like to do a fresh reinstall and start back from scratch now that I'm more familiar but I'm a bit stumped. I originally installed ubuntu using a burned Live CD, but when I pop it in and boot from it it loads up but... no install button on the desktop like there used to be.

I've looked around but every guide just says "click the install button" (which worked great the first time when it was actually there). I figured maybe I had to log in as root to install but when I type "root" it doesn't give me a prompt for a password... is there perhaps a command I can use from the terminal to start a clean installation?

---

### Post by dacookiemonn on 2007-06-09
at cd boot, hit f6 for extra options and then type "live" without quotes for live cd boot

---

### Post by dacookiemonn on 2007-06-09
You may also if you have not done so, go to System>Administration>Gnome partitioner to prep the drives, but be careful.  I acceidently deleted my vista backup from HP. lol

---

### Post by phollos on 2007-06-09
When exactly is "cd boot"? What am I looking for when I should press F6?

Also I don't have Gnome Partitioner it seems and I can't find it in synaptic =/

---

### Post by zvacet on 2007-06-09
Tha apps you found useless can be removed with synaptic or by command

```
sudo apt-get --purge remove file_name
```

 file_name = name of app you want to remove.

Maybe you don´t need to reinstall.Just delete apps you don´t want.

---

### Post by xthund3rh3adx on 2007-06-09
or you could do 

sudo apt-get remove APPLICATION_NAME

---

### Post by durrell on 2007-06-09
If you can't get the Live CD to boot so that you can use Gparted, you can always download and burn the Linux Rescue CD. You can launch Gparted from there and do a fresh install if you want to take that route.

[www.sysresccd.org/Download](www.sysresccd.org/Download)

---

### Post by phollos on 2007-06-09
Up and running again, thanks for the support guys =)

---

