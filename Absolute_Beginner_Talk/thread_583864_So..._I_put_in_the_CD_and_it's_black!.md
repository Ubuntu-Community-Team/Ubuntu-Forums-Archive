---
title: "So... I put in the CD and it's black!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Deadcode on 2007-10-20
Ok. I just downloaded the 64-bit version of Ubuntu. And while I'm making this thread I might as well throw in a question about that as well, but anyways:

1. Just downloaded 7.10. I put it in the CD-rom and boot up. I choose "Run or Install Ubuntu" (you kow, the first selection) and it loads. Then 4 lines of white font over a black backround comes. After that I can type stuff myself or just stare at it. I chose the last and waited for it to do something and after like 4-5 minutes I figured... is there anything I have to type myself? With 7.4 I got right into Ubuntu itself (desktop etc), with this.. I don't know.
I also tried the 32-bit version - same happened.

2. Does the 64-bit version act just like the 32-bit, only using my 64-bit processor fully?

Thanks for all answer and ask if you don't understand my english!

---

### Post by Deadcode on 2007-10-20
Already on page 2?

:(

Ok, to shorten it:
**When I put in the Ubuntu CD - I get 4 lines of text saying something about kernel and shizzle. This didn't happen when I tried 7.4 - what's up!?**

---

### Post by llamakc on 2007-10-20
> **Deadcode said:**
> Already on page 2?

:(

Ok, to shorten it:
**When I put in the Ubuntu CD - I get 4 lines of text saying something about kernel and shizzle. This didn't happen when I tried 7.4 - what's up!?**

Please share more information about your hardware.

---

### Post by Deadcode on 2007-10-20
Sapphire Radeon X1950PRO 256MB GDDR3,
MSI K8N SLI-FI, nForce4 SLI, Socket-939,
AMD Athlon 64 3800+ 2.4GHz Socket 939,
Corsair Value S. PC3200 DDR-DIMM 2048MB
Corsair Powersupply 620W, 120mm

---

### Post by llamakc on 2007-10-20
Did you burn the ISO at 4x speed (or something similarly slow)? Many folks seem to have issues with their ISOs.

---

### Post by Deadcode on 2007-10-20
No, I didn't. But I didn't with 7.4 either.
It's not like I get a bluescreen of errors, after the first Ubuntu orange loading bar I get some text and it just stops there.

---

### Post by hessiess on 2007-10-20
post the errors outputed before it lockes up

---

### Post by Deadcode on 2007-10-20
> **hessiess said:**
> post the errors outputed before it lockes up

*Starting deferred execution scheduler atd [OK]
*Starting periodic command scheduler crond [OK]
*Checking battery state... [OK]
*Running local boot scripts (/etc/rc.local) [OK]

_    <-- blinking. and i can type stuff

---

### Post by Deadcode on 2007-10-20
Is it really any point burning it on 4X...?

---

### Post by Maestro23 on 2007-10-20
> **Deadcode said:**
> Is it really any point burning it on 4X...?

Probably not liking your video card.  What kind do you have? ATI?

Might have to reconfigure the Xserver to use the "vesa" driver so it can boot.

---

### Post by Deadcode on 2007-10-20
> **Maestro23 said:**
> Probably not liking your video card.  What kind do you have? ATI?

Might have to reconfigure the Xserver to use the "vesa" driver so it can boot.

I have a ATI Sapphire Radeon X1950PRO 256MB GDDR3-card.
How do I "reconfigure the Xserver to use the "vesa" driver so it can boot"? This is my first real attempt at Linux, I don't know too much.

---

### Post by Maestro23 on 2007-10-20
> **Deadcode said:**
> I have a ATI Sapphire Radeon X1950PRO 256MB GDDR3-card.
How do I "reconfigure the Xserver to use the "vesa" driver so it can boot"? This is my first real attempt at Linux, I don't know too much.

When you are sitting there at the 4 lines of code and the blinking cursor,  try:

Ctrl + ALT + F2 (Should take you to a command line)

then

> sudo dpkg-reconfigure xserver-xorg

*Pick the "vesa" driver and then default options all the way thru.

Come back and post results.

---

### Post by Me Doc on 2007-10-20
I have the same problem! I have an ATI Radeon 9250 Pro vid card & just get black screen when I try to install 7.10 from cd. I get the same problem when doing the online upgrade from 7.04. I installed 7.04 with no problem.
 I'm installing the i386 version on a Compaq Presario. AMD Duron 750
I don't even get to see the lines of code. I get to the choices of installing, ect. & after that the screen goes black.

---

### Post by Deadcode on 2007-10-20
Interesting.

I tried the vesa stuff... It's like... 4 hours of setting the thing up. I though 7.10 was gonna be even more accesible? At least 7.4 got me to the desktop-screen.

---

### Post by jermyang on 2007-10-20
I also have the same problem as me doc, running the 64bit version and an ATI radeon x800 pro

---

### Post by jermyang on 2007-10-20
bump

---

### Post by Maestro23 on 2007-10-20
> **Deadcode said:**
> Interesting.

I tried the vesa stuff... It's like... 4 hours of setting the thing up. I though 7.10 was gonna be even more accesible? At least 7.4 got me to the desktop-screen.

After recofiguring the Xserver, are you back to where you where hanging up? If so, get back to command line and try:

> startx

*I installed 7.10 (64-bit) this morning with an ATI 1600.

---

### Post by llamakc on 2007-10-20
The OP is having problems with the install LiveCD and is not even to the point of the first post-install boot yet.

The LiveCD has an option for safe-graphics mode that will use the "vesa" driver. Try installing with that.

---

### Post by Maestro23 on 2007-10-20
> **llamakc said:**
> The OP is having problems with the install LiveCD and is not even to the point of the first post-install boot yet.

The LiveCD has an option for safe-graphics mode that will use the "vesa" driver. Try installing with that.

Missed that llamakc.  Thought he was at the 1st post-install.  My bad.:(

---

### Post by the_real_bubba on 2007-10-22
See also this ([http://ubuntuforums.org/showthread.php?p=3600836&posted=1](http://ubuntuforums.org/showthread.php?p=3600836&posted=1)) thread.  Boot into recovery mode and remove the "quiet" grub options to skirt the black screen of purgatory...

---

