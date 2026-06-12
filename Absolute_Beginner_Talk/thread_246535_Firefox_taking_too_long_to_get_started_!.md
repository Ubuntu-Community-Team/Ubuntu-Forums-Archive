---
title: "Firefox taking too long to get started !"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by happyweb on 2006-08-29
hey guys i m back with a new query,
i have recently installed KDE onto my ubuntu 
and choose KDE to be my default session manager
and after some time i decided to revert back to Gnome
and for that i edited default-display-manager file to
" /usr/sbin/gdm "
from     
" usr/bin/kdm "

and since then although my session has changed back to gnome
however my boot screen and shutdown screen are still showing
KDE ( Kubuntu ) screens...

also since i have changed back to gnome as my default session
my firefox ( 1.5.0.5 ) is taking way too long to get started 
for the first time and then when it gets started then even if i
close firefox and restart it then it doesn't take much time and
gets started within seconds as it used to get started..
after i click it to open..
(it usually is taking 5
 to 10 min to get started )


please help regarding both the problems

thanks in advance

---

### Post by PPAAUULL on 2006-08-29
I installed KDE and GNOME as well athough my system is not showing any slow down. Could you tell me your computer specs?

Paul

---

### Post by happyweb on 2006-08-29
> **PPAAUULL said:**
> I installed KDE and GNOME as well athough my system is not showing any slow down. Could you tell me your computer specs?

Paul

well my box hasnt slowed down, please read my thread details again
i have explained every thing in that 

and please help
and you wanted my comp specs:
its

P IV , 1.7 GHz, 512 SD RAM , ubuntu installed on 20 GB (partition ) then installed KDE package....

---

### Post by PPAAUULL on 2006-08-29
Risky but posibly remove the KDE packedge. Might work but could break your system. I did it twice, once it worked the other I had to do a clean install to fix it. hope it helps a bit.

Paul

---

### Post by bruce89 on 2006-08-29
You can remove KDE by following this - [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by happyweb on 2006-08-29
> **bruce89 said:**
> You can remove KDE by following this - [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

are both of my problems due to kde package and
arent there any way to fix them both without re installing 
kde

---

### Post by bruce89 on 2006-08-29
You can change the splash screens thus:
```
sudo update-alternatives --config usplash-artwork.so
```
Is firefox slow in KDE or GNOME?

---

### Post by happyweb on 2006-08-29
> **bruce89 said:**
> You can change the splash screens thus:
```
sudo update-alternatives --config usplash-artwork.so
```
Is firefox slow in KDE or GNOME?

hey thanks dude for the code to change the boot screen
and regarding my second problem (firefox related)
well, in both KDE and GNOME this firefox problem is coming
and first time when i click to open firefox it opens in ( 5 to 10 min )
however when it gets started and i restart it the second time , then
then firefox gets started as it usually does in normal time...

please help in this problem ...

---

### Post by happyweb on 2006-08-29
> **bruce89 said:**
> You can change the splash screens thus:
```
sudo update-alternatives --config usplash-artwork.so
```
Is firefox slow in KDE or GNOME?

well your code to change default artwork worked partially,
when i changed it to default one then during shut down process
it is now showing ubuntu screen , however during the boot up process
it is still showing kubuntu screen
how to change this boot screen to ubuntu one 
plus
regarding my second problem (firefox related)
well, in both KDE and GNOME this firefox problem is coming
and first time when i click to open firefox it opens in ( 5 to 10 min )
however when it gets started and i restart it the second time , then
then firefox gets started as it usually does in normal time...

please help
thanks in advance

---

### Post by kronick on 2006-08-29
Hy, I've installed Ubuntu 6.06 LTS on my laptop few hours ago. The problem is everything is taking soooo long to get started, and i was wondering if anyone know what the problem could be?

System specifications:
HP Compaq nx6125
AMD Turion 1.8GHz
512M DDR RAM(384MB RAM, 128MB shared graphics)

Please help me.

---

