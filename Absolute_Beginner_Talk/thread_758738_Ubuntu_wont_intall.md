---
title: "Ubuntu wont intall"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by bb12489 on 2008-04-18
Im completely new to ubuntu.....we just started using it in class the other day. we have it loaded up on some older computers, but i wanted to install it on my laptop. when i pop the live cd in, it loads up to where i can start or install ubuntu or press F6 for more options and such, then it acts like its loading the live desktop, but after the loading screen it says that the X server cant start and is not configured. so how can i fix this problem?

my laptop specs are....

Asus C90s
Core 2 duo E4300
2gb ram
160gb hdd
8600m 512mb

---

### Post by Tatty on 2008-04-18
Do you end up at a command line after the message?  If so try...

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bb12489 on 2008-04-18
ok, i'll try it. be back soon!

---

### Post by borobudur on 2008-04-18
- check your CD
- check your computers architectur
- try the alternate ubuntu version

---

### Post by bb12489 on 2008-04-18
yea, that didnt work....after it said x server cant start it brought me to a command line, but when i type in the command it doesnt do anything

---

### Post by Sef on 2008-04-18
> yea, that didnt work....after it said x server cant start it brought me to a command line, but when i type in the command it doesnt do anything

Did you type "startx" (without the quotes)?   That will get you to a gui if all is well.

---

### Post by OffAxis on 2008-04-18
you can also check the log files to see what the error is, and what aspect of the x-server is not being configured correctly.

```
dmesg | tail

```
is a good place to start. There's also a specific log for the xserver here:
/var/log/Xorg.log

you can view it with 
```
less /var/log/Xorg.log
```


and since you're completely new it bears mentioning that you don't need to restart the computer to reload the x-server. 
After running the 
```
sudo dpkg-reconfigure xserver-xorg
```

just reload the x-server with CTRL+ALT+Backspace 
or startx
or /etc/init.d/gdm start
or /etc/init.d/gdm restart

at a minimum an error should be generated to the terminal that'll give you a clue as to what's wrong.

---

### Post by xeth_delta on 2008-04-18
The first thing you should check is the integrity of the downloaded ISO image. There are instructions in [this link]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28").

After makeing sure the ISO image is right, burn it at a low speed, say 4x, if possible.

If after this it still does not work, I suggest you try the alternate installation CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). Check the box with the "alternate desktop CD" just below the green download button.

---

### Post by bb12489 on 2008-04-18
well i figured that since its the cd that came with our linux book, that it should work no prob

---

### Post by xeth_delta on 2008-04-18
> **bb12489 said:**
> well i figured that since its the cd that came with our linux book, that it should work no prob

Ah, I see. In that case there might be some incompatibility between the installer and your system.

My advice would be to perform an advanced search in the forum (ordering by relevancy instead of date) and if you don't find anything download the alternate CD from the link I mentioned. In many cases where the regular CD fails, it will work.

---

### Post by Paqman on 2008-04-18
What version of Ubuntu is the disk? Simply grabbing a more up to date version might solve your problem.

---

### Post by NateMan on 2008-04-28
I have an asus c90s and the live cd will not install on the system. Its something about the videocard. However the alt disc works perfectly. The copy of ubuntu that came with your linux book was probably a live disc of an older version. I am positive that the 8.04 or 7.10 alternative install discs will work. If they still do not work, I would imagine the issue is with your hardware. If you have any problems with the c90s in linux feel free to message me, I've gotten almost everything to work on mine.

---

