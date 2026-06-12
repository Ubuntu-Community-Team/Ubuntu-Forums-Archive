---
title: "20&quot; Cinema Display does not work"
date: 2005-04-06
forum: Apple PPC Users
---

### Post by chrizel on 2005-04-06
hi,

I've downloaded the current PowerPC Live CD of Hoary to test whether Ubuntu/Linux works on my system at all (before I install it on hard disk). It's a standard PowerMac G5 2,5 Ghz dual with a 20" Apple Cinema Display (the new silver one) and ATI Radeon 9600 XT.

I booted with the power4 profile and it boots fine... hardware detection works... network, all ok. The problem is that when X11/X.org starts the Cinema Display goes to standby mode i.e. it gets dark and the diode "glows"... ;-)

Ok, then i looked for some hints at Google and in different forums (especially here). I found some things about Cinema Display problems, found some Modelines for XF86Config/Xorg.conf etc. Then i bootet my Hoary Live CD in power4 expert mode and tried to edit Xorg.conf by hand.

-> No difference. If i try fbdev gfx driver X11 doesn't start at all. If i try ati gfx driver it seems to start (i hear the cd drive working so maybe it starts even gnome). But the display is in standby. I tried different Modeline settings (and did many many reboots because after standby it cannot wake up) which should fix the problem for my Cinema Display but it still does not work. Btw: the display has a resolution of 1680x1050 which seems to be different from the old cinema displays...

So: Does anyone have the same configuration or maybe the (new) 20" Cinema Display and an ATI gfx card and can give me his Xorg.conf?

Thanks,
chrizel

---

### Post by daniels on 2005-04-06
It was a code problem that should be fixed with the latest daily live CD ([http://cdimage.ubuntu.com/daily-live/current/hoary-powerpc-live.iso)](http://cdimage.ubuntu.com/daily-live/current/hoary-powerpc-live.iso)).

---

### Post by smashing on 2005-04-30
i've got the same problem with powermac g5 dp1,8 and ati 9600xt+cinemadisplay. When gdm start the mac freeze. is there a solution?
i've got a preview version of hoary 5.04.

thanks and sorry for my english.

edit: how  can i boot hoary without gdm? now i can't use ubuntu because the mac freeze.

---

### Post by karoliina on 2006-08-03
Hi,

I have no experience on PPC, but with Intel machines the same thing occur with the Cinema Display and Ubuntu Linux / X:

I have 23 inch Cinema display and Dell Latitude D600 laptop. The Cinema display remains in standby mode and awakes only with ati fgrlx binary driver. With drivers "ati" or "radeon", it doesn't awake at all. I was using the fgrlx driver (with it I am only able to use the Cinema display in X, doesn't work in text mode), but now I upgraded to Edgy and fglrx module doesn't work with the current X-server version and therefore no picture. Has anybody been looking at the open source driver if it would be possible to enable Apple's Cinema displays? Very nice screen, I wouldn't part from it, but now it seems that I am forced to downgrade the X back to Dapper in order to be able to see something from the display.

Best Wishes
Karoliina Salminen
[http://www.karoliinasalminen.com/blog](http://www.karoliinasalminen.com/blog)

---

