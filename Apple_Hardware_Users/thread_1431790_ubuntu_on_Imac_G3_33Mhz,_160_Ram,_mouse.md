---
title: "ubuntu on Imac G3 33Mhz, 160 Ram, mouse"
date: 2010-03-17
forum: Apple Hardware Users
---

### Post by michamicha on 2010-03-17
Is it possible to put ubuntu(last version) on a Imac G3, 333Mhz, 160 Ram?

Probely a guide to do so ia allready as a thread...please refer to.

Now it runs a 9.x OS. Mac

With this system a mouse was supplied with a network plug. It fits to the Mac, but does not work.

Does it need extra software?? Name; Vtech.


If possible also a answere to my e-mail; [email]om.hc@hotmail.com[/email]

This because I am a NewBee on this forum, I might not found this thread.

Thank You

A kiss from the Holland.

---

### Post by linuxopjemac on 2010-03-17
You have too little RAM to have a graphical user interface. 256Mb is really the minimum.

---

### Post by michamicha on 2010-03-19
Thanx for reaction!

So, I will keep the OS 9.x.

Only problem is my T-mobile  Mobile internet usb stick.

The OS does regognize it....but I have no idear how to instal the software, wich is located on the stick. The stick is being regonized as a cd-rom. I can enter it. But that's it.

Any body a tip for this please. I could run a linux on it?????

Other question.

I very much like the look of this older Mac. But it really is loud with system sounds of fans.

Is it possible to do something about this.

Some older P2 can run with the fan off.

Is this possible for this machine, or is it to dangereus??

Thanks for replies.

Micha
Holland

---

### Post by linuxopjemac on 2010-03-19
> I have the 500 MHz version of the final iMac G3 design. They don't have a fan, I've taken mine apart several times. The sound (if it's a high pitched whir) you're hearing is probably the drive beginning to fail. Happened to mine, I'd back up your data and start looking for a replacement drive.

[http://forums.t-mobile.com/t5/Laptop-Stick-Help/TMOBILE-USB-STICK-FOR-MAC/m-p/89890#U89890](http://forums.t-mobile.com/t5/Laptop-Stick-Help/TMOBILE-USB-STICK-FOR-MAC/m-p/89890#U89890) (probably only OSX)

---

### Post by linuxopjemac on 2010-03-19
If you want an easy installation in the future, I would frequently visit the next link. It is WattOS. Someone else on the forum pointed me towards this. it's based on Ubuntu, but with very lightweight desktop/window manager (LXDE/OpenBox), which will probably also run on your low RAM machine.

[http://www.planetwatt.com/index.php?module=FAQ#faq8](http://www.planetwatt.com/index.php?module=FAQ#faq8)
[http://www.planetwatt.com/index.php?module=Dizkus&func=viewtopic&topic=760](http://www.planetwatt.com/index.php?module=Dizkus&func=viewtopic&topic=760)

---

### Post by oswaldkelso on 2010-03-19
> **michamicha said:**
> Thanx for reaction!

So, I will keep the OS 9.x.

Only problem is my T-mobile  Mobile internet usb stick.

The OS does regognize it....but I have no idear how to instal the software, wich is located on the stick. The stick is being regonized as a cd-rom. I can enter it. But that's it.

Any body a tip for this please. I could run a linux on it?????

Other question.

I very much like the look of this older Mac. But it really is loud with system sounds of fans.

Is it possible to do something about this.

Some older P2 can run with the fan off.

Is this possible for this machine, or is it to dangereus??

Thanks for replies.

Micha
Holland

Debian will install and run on 160mb fine. I will be slow but you'll get a system up on that. The browser is the biggest drain but my system running iceweasel/firefox was using less than 100mb ram.

[http://2.bp.blogspot.com/_7Y8k50qHvgs/Su9fo4jxRlI/AAAAAAAAAHI/jV4vDk8t2fM/s1600-h/imac-blackbox-rox.png](http://2.bp.blogspot.com/_7Y8k50qHvgs/Su9fo4jxRlI/AAAAAAAAAHI/jV4vDk8t2fM/s1600-h/imac-blackbox-rox.png)

If you use net-serf or dillo ram wont be a problem (in getting the system to run anyway) The real issue is your usb internet dongle you need to provide more info on the make and model 

In reality you will need to use a friends  etho-net internet connection to build your system then configure your dongle (if it's possible). Or go the easy route and use the Debian xfce/lxde install to get you going in a more straight forward manor, especially if access to the internet is a problem.

The 333mhz does have a fan the 500mhz does not. a replacement or removal should not be to challenging but the CRT has lethal currents so if you start stripping anything ensure all safety measures are carried out. There are  lots of guides out there google "imac 333 disassemble" from memory fan access does require more stripping down than most "how to's show"  Have fun.

---

### Post by linuxopjemac on 2010-03-19
Oswald, you use a very stripped down version I guess. Which desktop/window manager are you using on your Mac ? I knew that you can run Debian on such a low RAM machine. I thought of WattOS for him, I would guess that it is easy to install. Your way also works, but might be more difficult, especially without a wired connection.

---

### Post by oswaldkelso on 2010-03-19
The install in the snapshot was based on the how-to in my sig.

Now I start with a 12mb net install iso [http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso) 

Then add everything as I need it. xorg slim openbox tint2 rox-filer (without zero install) alsaplayergui fbpanel etc

The xfce/lxde CD is fine, Debian will install on as low as 32mb it switches to low ram mode. Running on that would be painful though I did have an old laptop doing so before switching to DSL. As I said the browser is the hog netsurf is the lightest normal browser but dillo2 (you need to compile it) is the lightest/fasted but it's missing meny features that are considered normal.

The doggle is a main area of concern. 

But if he installs the xfce/lxde CD he could download other disks and add them to his sources.list to ensure access to more software.Then download what is required to run his dongle (if it's possible) to usb or CD drive. Not having internet when searching for info makes all this very hard, really it needs to be done at a friends to get it set up first.

this is on my netbook so I have more things running than on my imac but you can see where your ram goes. (both browsers have 4 tabs open)

----8<----------8<----------8<---------8<--------

  1.4 MiB + 483.5 KiB =   1.9 MiB	tint2
  1.5 MiB + 899.0 KiB =   2.4 MiB	smbd (2)
  2.7 MiB +  91.5 KiB =   2.8 MiB	hald
  2.3 MiB + 483.5 KiB =   2.8 MiB	openbox
  3.3 MiB + 503.0 KiB =   3.8 MiB	wicd-monitor
  4.1 MiB + 330.0 KiB =   4.4 MiB	wicd
  3.9 MiB +   1.7 MiB =   5.6 MiB	rox
  4.1 MiB +   1.6 MiB =   5.7 MiB	fbpanel
  5.4 MiB + 833.0 KiB =   6.2 MiB	bash (3)
  4.3 MiB +   3.8 MiB =   8.1 MiB	apache2 (11)
 11.9 MiB + 237.5 KiB =  12.1 MiB	tor
 11.7 MiB +   2.6 MiB =  14.4 MiB	python2.5
 13.0 MiB +   1.8 MiB =  14.8 MiB	Xorg
 22.5 MiB +   2.4 MiB =  24.8 MiB	netsurf-gtk
 78.1 MiB +   2.0 MiB =  80.2 MiB	iceape-bin
---------------------------------
                        213.3 MiB
=================================

 Private  +   Shared  =  RAM used	Program

---

