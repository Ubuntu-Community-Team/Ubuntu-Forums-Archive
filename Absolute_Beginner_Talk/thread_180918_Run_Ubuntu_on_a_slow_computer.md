---
title: "Run Ubuntu on a slow computer"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-23
I have a pretty old computer that windows 2000 + XP sucks on. Can anyone help me how to get ubuntu to run quickly on it if its possible.
AMD K6-2 450 Mhz 128 MB RAM

---

### Post by Jagot on 2006-05-23
Well, you could use Xubuntu which uses the XFCE desktop environment instead of Ubuntu's GNOME.  XFCE is less resource hungry:

[https://wiki.ubuntu.com/XubuntuReleases](https://wiki.ubuntu.com/XubuntuReleases)

Upgrading your RAM as much as possible wouldn't hurt either.

---

### Post by Sef on 2006-05-23
Besides Xubuntu, you could do a server install and then install fluxbox, the lightest of the lightweight window managers.  Also icewm is another choice.

---

### Post by tony_tj3 on 2006-05-23
I have an old laptop (compaq armada) that is pretty slow as well, but i removed windows and made it soley ubuntu and i have had no troubles with speed, even with gnome

---

### Post by popkid on 2006-05-23
[QUOTE=Sef]Besides Xubuntu, you could do a server install and then install fluxbox, the lightest of the lightweight window managers.  Also icewm is another choice.[/QUOTE]

I have an even older (Toshiba Satellite) Laptop (2Gb hard drive, 32Mb RAM, 199MHz PentiumMMX), running Debian Sarge (I don't know of a way of getting Ubuntu on a machine with so little memory unfortunately) and Fluxbox and it is actually acceptably quick for browsing (I use Opera on it).

Fluxbox is a really nice small footprint window manager, you can actually get it looking very nice too!

---

### Post by az on 2006-05-23
[QUOTE=Sef]Besides Xubuntu, you could do a server install and then install fluxbox, the lightest of the lightweight window managers.  Also icewm is another choice.[/QUOTE]
Install the menu package, too, to get a much better experience with icewm....

sudo apt-get install menu

---

### Post by djheadley on 2006-05-23
If you can find more memory for it to bring it up to 256mb then it should run Gnome pretty well.  My machine is a 433mhz Celeron with 256mb ram and I have almost no problems - only when I get greedy and try to open 5 or 6 windows at a time.

---

### Post by Klaidas on 2006-05-23
[QUOTE=tony_tj3]I have an old laptop (compaq armada) that is pretty slow as well, but i removed windows and made it soley ubuntu and i have had no troubles with speed, even with gnome[/QUOTE]

Linux is known for low-resources-required. So an old computer will run perfectly. ;)

---

### Post by youthforlinux on 2006-05-23
Thanks um, is it better to wait for Dapper Final or to use Breezy of Dapper Beat, or does it not matter?

---

### Post by youthforlinux on 2006-05-23
I meant Dapper Beta

---

### Post by Jagot on 2006-05-23
[QUOTE=youthforlinux]Thanks um, is it better to wait for Dapper Final or to use Breezy or Dapper Beta, or does it not matter?[/QUOTE]

At this stage in the development of Dapper it is pretty rock solid so you should haven't any problems with it.  I think with the features Dapper offers, and especially the performance increase over Breezy that I have noticed on my machine, I would personally go for the Dapper beta.

---

### Post by Klaidas on 2006-05-23
Good question.
I myself would go for the beta now and the, when released, upgrade to the stable dapper.
It's only a few days left, so beta is > rock solid

---

### Post by Bazon on 2006-05-23
I don't want to spoil the party, but regarding my experience Ubuntu isn't really good for slow computers.
I tried to run Ubuntu on a Via Epia M 6000 (600MHz) with 512MB RAM and it really wasn't so good. Even switching to XFCE didn't make it much better. At least on that machine, Windows XP was really faster!

[i]But don't get my wrong, guys, I really love Ubuntu. :)
Therefore I bought a new, faster (but also fanless and noiseless) CPU (AMD Geode Nx 1750 with 1.4GHz) and now I'm really happy with it.[/i]

---

### Post by youthforlinux on 2006-05-23
just wondering how easy it is to upgrade to Dapper Final from Dapper Beta when it comes out.

---

### Post by Bazon on 2006-05-23
[QUOTE=youthforlinux]just wondering how easy it is to upgrade to Dapper Final from Dapper Beta when it comes out.[/QUOTE]
Ehm, very easy! Just do the normal updates...! :)

---

### Post by youthforlinux on 2006-05-23
sweet then

---

### Post by Just4 on 2006-05-23
Xubuntu is very nice and I run it on similar hardware as my secondary machine (P3 1Ghz, 192MB RAM), and Xubuntu is blazing fast on my main machine (P4 3Ghz, 512MB RAM) it boots faster than XP, Firefox launches faster in Xubuntu than XP, I've actually gotten in the habit of using Xubuntu more now that its on my main machine, and honestly, the new XFCE (4.3 I believe, whatever comes with the dapper beta) is just as good as gnome, and very lightweight, I don't particularly like IceWM or FluxBox personally, but they are the lightest of the light, and I'd use them if I found Xubuntu too slow on my secondary box, I really prefer XFCE (Enough that I'm running it on my main machine which is more than enough to run Gnome or KDE comfortably). - And you could always do a server install of dapper/drake and then install all 3 (I believe you can install all 3, I know you can install XFCE and Gnome and KDE together), XFCE, IceWM and FluxBox, and see which one you like and what runs faster and then remove the ones you don't want.

---

