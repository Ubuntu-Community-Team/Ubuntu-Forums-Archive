---
title: "cant get into ubuntu!"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-01-09
I got some updates today and after a reboot I cant get in anymore!

I have tried to reconfigure xserver several times but with no luck.   I also did an aptitude update, but again no sucess!  I just get a black screen to log into.  

Any ideas what else I can try?

Russty

---

### Post by peebly on 2007-01-09
Hi

Had the same problem today, luckily I installed my nvidia driver using envy, so I just ran the script again and it fixed the problem.

---

### Post by Russty of Oz on 2007-01-09
I tried reinstalling nvidia using aptitude but it said I already have it installed??

---

### Post by %hMa@?b&lt;C on 2007-01-09
> **Russty of Oz said:**
> I tried reinstalling nvidia using aptitude but it said I already have it installed??
what error does "startx" give you?

---

### Post by Blondie on 2007-01-09
Need more information.

If you login then type "startx" what errors do you get?

---

### Post by Russty of Oz on 2007-01-09
these are the errors:

[B]NV(0): failed to open framebuffer device

screen found, but none have usable configuration

XIO: IO error 104 (connection reset by peer) on X server "0.0" after 0 requests (0 known processed) with 0 events remaining[/B]

Does that help?

---

### Post by Russty of Oz on 2007-01-09
Anyone?

---

### Post by Russty of Oz on 2007-01-09
I keep doing the xserver reconfiguration but it still wont work.

**I DESPERATELY NEED HELP!!!! **:-?

---

### Post by tonyr1988 on 2007-01-09
Not sure, but it may have changed your nVidia driver on your (I've had problems with it before). Maybe this will help (maybe not, but whatcha got to lose?):

1) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo nano /etc/X11/xorg.conf
3) scroll down and find:

> Section "Device"
     Identifier "NVIDIA [blah blah blah blah - name of card]"
     Driver "nv"
EndSection

4) Change **Driver "nv"** to **Driver "nvidia"** and save / exit
5) startx
6) If it doesn't work, try:

> sudo rmmod nvidia && sudo modprobe nvidia

7) startx
8) If it doesn't work, restore old xorg.conf:

[quote]sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

That's all I got...oh yeah - if it does work, it may not be permanent, but we can worry about that later...

---

### Post by MkfIbK7a on 2007-01-09
i think i understand your problem

do 

sudo dpkg-reconfigure xserver-xorg

when it asks about framebuffering say NO
then finish and reboot

hope this helps

---

### Post by Russty of Oz on 2007-01-09
I followed your directions and now I got this error

[B]Failed to load module "wfb" (module does not exist, 0)
ERROR: API mismatch:  the NVIDIA kernel module has the version 1.0.8776, but this x module has the version 1.0.9746[/B]

SIGH!:(

---

### Post by Russty of Oz on 2007-01-09
> **wert613 said:**
> i think i understand your problem

do 

sudo dpkg-reconfigure xserver-xorg

when it asks about framebuffering say NO
then finish and reboot

hope this helps

Did that, still nothing!:(

---

### Post by MkfIbK7a on 2007-01-09
ok so
do 
sudo dpkg-reconfigure xserver-xorg
and change your graphics card driver to nv
finsh and do
ctrl+alt+backspace
this should enable you to start the xserver you can configure your driver from there...

---

### Post by Russty of Oz on 2007-01-09
YES!  AT LAST!!! I am back in!  What a relief!

Now what should I do now about the driver?

---

### Post by MkfIbK7a on 2007-01-09
glad to be of help:D:D
what graphics card do you have?

---

### Post by Russty of Oz on 2007-01-09
Geforce 6200 turbo cache 128mb

---

### Post by tonyr1988 on 2007-01-09
> **wert613 said:**
> ok so
do 
sudo dpkg-reconfigure xserver-xorg
and change your graphics card driver to nv
finsh and do
ctrl+alt+backspace
this should enable you to start the xserver you can configure your driver from there...
Oops - I told him to switch from the right one to the wrong one.

My bad...I use nvidia instead of nv - hope I didn't mess you up.

---

### Post by Russty of Oz on 2007-01-09
> **tonyr1988 said:**
> Oops - I told him to switch from the right one to the wrong one.

My bad...I use nvidia instead of nv - hope I didn't mess you up.

No, it was really messed up to start with, so any suggestion were very welcome!

---

### Post by Russty of Oz on 2007-01-10
I have installed the nvidia drivers using this method [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

It all looks OK at the moment.

---

### Post by Russty of Oz on 2007-01-10
Hmmm, I am sure wert613's cat looked clear before, now is is out of focus!  I wonder if that is the driver I have installed?  All the others look clear.

---

### Post by tonyr1988 on 2007-01-10
Looks blurry to me, too. I wouldn't worry about it.

...unless my new 512MB GeForce is going out, then I'm ticked! :P

Congrats on getting everything up and running - hope it all goes well for you.

---

### Post by MkfIbK7a on 2007-01-10
no i changed it sorry:D

---

### Post by MkfIbK7a on 2007-01-10
this is the original image
[http://www.acclaimimages.com/_gallery/_pages/0028-0608-0110-1124.html](http://www.acclaimimages.com/_gallery/_pages/0028-0608-0110-1124.html)

---

### Post by MkfIbK7a on 2007-01-10
well actually it was the low quality thumbnail from the page before it...
The free one:rolleyes:

---

### Post by Russty of Oz on 2007-01-10
Ah, thats better!  After seeing the blurry one I tried different screensavers to see if the drivers were doing anything weird, but they were all OK.

Thank very much for all your help guys! 

Much appreciated.  I have got so used to Ubuntu that when I am "locked out" so to speak I have withdrawal symptoms,  using windows again is SOOOOOO UNCOOL!

Russty :D

---

### Post by MkfIbK7a on 2007-01-10
lol so true!

---

### Post by syxbit on 2007-01-10
i had the same problem
i think it was because of a compiz update (that's the last thing that happened before the reboot that locked me out)
i formatted, and used envy, but i'm still locked out
i wonder if it's 0.7.5, as 0.7.4 worked for me last time.
is there a way to manually run the official nvidia installer?

this is why ubuntu will never be as popular as windows.
it's simply unacceptable that when ubuntu does AUTO UPDATES, it breaks!

---

### Post by MkfIbK7a on 2007-01-10
> **syxbit said:**
> i had the same problem
i think it was because of a compiz update (that's the last thing that happened before the reboot that locked me out)
i formatted, and used envy, but i'm still locked out
i wonder if it's 0.7.5, as 0.7.4 worked for me last time.
is there a way to manually run the official nvidia installer?

this is why ubuntu will never be as popular as windows.
it's simply unacceptable that when ubuntu does AUTO UPDATES, it breaks!

ubuntu probably will not break from updates in a few years, obviously if its a problem it will be fixed:mrgreen:

---

### Post by Russty of Oz on 2007-01-11
It wouldn't be quite so bad if Ubuntu had a way of going back to the last configuration that worked.  If you could at a terminal, tell it to go back to yesterdays config, that would help a lot.

PS That avatar  looks better wert613. So cute!

---

### Post by MkfIbK7a on 2007-01-11
> **Russty of Oz said:**
> 
PS That avatar  looks better wert613. So cute!

lol thx!:mrgreen:

---

### Post by tchoklat on 2007-01-14
I have a smiliar problem after an aptitude upgrade.

When booting I get 
Failed to load module "wfb" (module does not exist, 0)
Error, API mismatch; NVIDIA 1.0-8776, this X module 1.0-9746
No Screens Found

Any help would be appreciated. I have checked the xorg.conf it seems OK

tchoklat

---

