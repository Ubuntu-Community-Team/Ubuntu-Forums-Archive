---
title: "Xubuntu + Compiz Fusion"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-26
hi, thanks for reading.

basically i have a sparelaptop i use rarely and i just upgradedto 7.10.hooray.

but im trying to get Compiz fusion to work and AWN, but it says it cant find XGL.

itried:

sudo apt-get install xserver-xgl

but it wouldnt let me log in at all,
so i have removed.

what else do i do?

ive never used XFCE, only Gnome which was a piece of cake to do.

thanks once again :)

---

### Post by overdrank on 2007-12-26
> **skymera said:**
> hi, thanks for reading.

basically i have a sparelaptop i use rarely and i just upgradedto 7.10.hooray.

but im trying to get Compiz fusion to work and AWN, but it says it cant find XGL.

itried:

sudo apt-get install xserver-xgl

but it wouldnt let me log in at all,
so i have removed.

what else do i do?

ive never used XFCE, only Gnome which was a piece of cake to do.

thanks once again :)

Hi and could you give us some specs on the system?

---

### Post by skymera on 2007-12-26
wow ermm,

192MB RAM
64MB Graphics - shared i think
1.8GHz AMD Sempron

(only want very basic effects, wobbly windows really)

adn i have direct rendering checked earlier.

---

### Post by skymera on 2007-12-26
the drive it is using i believe is VIA

and when i run avant-window-navigator from terminal i get:

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by overdrank on 2007-12-26
> **skymera said:**
> wow ermm,

192MB RAM
64MB Graphics - shared i think
1.8GHz AMD Sempron

(only want very basic effects, wobbly windows really)

adn i have direct rendering checked earlier.

Ok I am assuming that with the xgl it is a ATI graphics card?

---

### Post by skymera on 2007-12-26
ermm no.

i didnt know what to do and some useless Googling i read about XGL

my cars isss

"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"

---

### Post by overdrank on 2007-12-26
> **skymera said:**
> ermm no.

i didnt know what to do and some useless Googling i read about XGL

my cars isss

"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"

Ok sorry I have had no luck with the unichrome chipsets so I wish you luck! :KS

---

### Post by skymera on 2007-12-26
o, even you?

bugger >_< 
i'll google a lil bit more.

so there no way to get XGL? i get thatsort of error when i run CF

---

### Post by spiderbatdad on 2007-12-26
have you tried the xserver-xorg-video-unichrome...just curious? BTW wobbly windows seems to be one of the more resource intensive effects.

---

### Post by liam.dunn144 on 2007-12-26
what do u mean by:

> but im trying to get Compiz fusion to work and AWN, but it says it cant find XGL.

itried:

sudo apt-get install xserver-xgl

but it wouldnt let me log in at all,
so i have removed.

---

### Post by chessercizes on 2007-12-26
heya!

umm i'm running xubuntu 7.10 with compiz fusion.

maybe this can help:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by overdrank on 2007-12-26
> **chessercizes said:**
> heya!

umm i'm running xubuntu 7.10 with compiz fusion.

maybe this can help:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

HI and what is your graphics card?

---

### Post by chessercizes on 2007-12-26
ATI Radeon 9600 Pro

---

### Post by overdrank on 2007-12-26
> **chessercizes said:**
> ATI Radeon 9600 Pro

Ok and the link you posted is for 
Supported Hardware

    *

      ATI
          o

            Mobility Radeon 9700 SE: Xgl running with proprietary fglrx driver 8.23
          o

            Radeon X300: Xgl running with proprietary fglrx driver 8.23
    *

      NVIDIA
          o

            A MX 4xxx series card or newer using the NVIDIA binary driver.
    *

      Intel
          o

            i8xx and i9xx

(./)
And this post is asking for unichrome,

---

### Post by chessercizes on 2007-12-26
well, mines not in the list either and it worked....

but super sorry! i don't think that guide is for 7.10 x.x.

i'll be more careful in the future. (or maybe just not post at all....)

---

### Post by overdrank on 2007-12-26
> **chessercizes said:**
> well, mines not in the list either and it worked....

but super sorry! i don't think that guide is for 7.10 x.x.

i'll be more careful in the future. (or maybe just not post at all....)

Please and I did not mean to imply that at all. I was asking because there are many user with that graphics chipset.

---

### Post by skymera on 2007-12-27
> **chessercizes said:**
> well, mines not in the list either and it worked....

but super sorry! i don't think that guide is for 7.10 x.x.

i'll be more careful in the future. (or maybe just not post at all....)


i'll try your link anyway.
whats to lose? :)

---

### Post by skymera on 2007-12-27
ok xserver-xgl

just hangs login and i get taken back to login screen.

doh, thanksfor link anyway

---

### Post by skymera on 2007-12-27
ive googled all day and nothing.

ive tried xorg-video-unichrome
xorg-video-openchrom
xorg-video-via

and nothing has worked,
i did however find my card model name,

its k8m800.

xserver-xgl freezes mycomp, it dosent login and i get taken back to the login window.
the only way i can login after is to remove xserver-xgl

im puzzled, anyone got ideas? thanks so much

---

### Post by spiderbatdad on 2007-12-27
[http://ubuntuforums.org/showthread.php?p=3923300&p=3923300](http://ubuntuforums.org/showthread.php?p=3923300&p=3923300)

this link might get you steered toward a driver.

---

### Post by skymera on 2007-12-27
awesome, thanks for link.

i just have to compile drive myself, wasnt listed on the ubuntu distro page :(

thanks, i give you udate whenever i get it done

---

### Post by skymera on 2007-12-27
well, i downloaded the source codefor my chip.

executed

./makedriver
./vinstall

seemed ok, the archive came withnob instructions, justa text file eith some text, no actusal instructions.

and now my Via driver dosent work at all and im in safe graphics mode.

is there a .run file for my card for ubuntu?

i'll do littlebit of Googling now.

card is:

k8m800
VIA Unichrome S3 Pro

---

### Post by enoshei on 2008-01-24
VIA Unichrome video adapter driver does not support 3D acceleration my friend,only Nvidia and ATi video adapter binary drivers has that,so installing xserver-xorg-xgl doesn't help,it's for ATi cards btw.

---

