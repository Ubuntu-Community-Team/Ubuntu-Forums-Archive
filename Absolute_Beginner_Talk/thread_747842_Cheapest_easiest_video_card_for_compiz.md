---
title: "Cheapest easiest video card for compiz?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-06
Okay, I've given up on a PNY Verto GeForce 6600GT - I just can't get the gui to be readable in Ubuntu (it's like the refresh, etc., are off). So.....

For a person on disability with a VERY limited income, what is the cheapest, easiest to install to Ubuntu and have work video card that will run compiz and the rest of the desktop effects ?

PLEASE be sure the card is easy to install to Ubuntu - I don't want to go through the hours and hours and hours I did with the other card to no avail.  I want something that will just work.

Thanks!

---

### Post by loell on 2008-04-07
LoL  @ be sure :)

how about, intel cards?  just waiting for someone to confirm if this is cheaper that nvidia or ati.

---

### Post by anewguy on 2008-04-07
Anyone?

---

### Post by canthus13 on 2008-04-07
The GeForce gave you problems? That's odd.  Did you use Envy to install the drivers?

--Me

---

### Post by atomkarinca on 2008-04-07
I've got geforce 5500 and it's working like a charm. I have seen MX400 series work very well, too.

---

### Post by fettster on 2008-04-07
My GeForce card has given me loads of problems.  I've been trying for months now to get the right driver enabled and working properly (Yes, I have used Envy, I've downloaded it straight from NVIDIA, I've used the one in the restricted drivers menu, I have tried just about everything I can find and it still won't work) If someone could please refer and anewguy and me to a good cheap video card, I would be more than happy to get rid of my GeForce card.

---

### Post by Crafty Kisses on 2008-04-07
Honestly, if you're going to get a cheap video card, you're probably gonna have to go with nVidia. So I'd go with either the GeForce Ti4200, or the GeForce FX 5200 Ultra.

---

### Post by fettster on 2008-04-07
By the way, my card is a GeForce4 440 Go

---

### Post by solidsteel144 on 2008-04-07
I ordered a GeForce 8400 GS just for Linux.. Hoping for reliability and compatibility.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814141068](http://www.newegg.com/Product/Product.aspx?Item=N82E16814141068)

$34.99

I'll let you know how it works.

---

### Post by atomkarinca on 2008-04-07
Well, as I mentioned I have FX 5500 and working fine, all I did to get it working was booting into Ubuntu and it installed the drivers automatically. A friend of mine had the same experience with MX 400 or something. I don't know what might cause a problem with nvidia.

---

### Post by roachk71 on 2008-04-07
Mine's an integrated nVidia GeForce 6150 LE. So far, in Gutsy, there have been numerous rendering and OpenGL hangs, but not in Hardy.

[-X A bit of advice: Avoid Envy with this chipset; it made my machine unusable until a Gutsy re-installation (I traced this down to, believe it or not, a libc6 runtime library corrupted by the package somehow!) Use the restricted drivers manager instead.

---

### Post by canthus13 on 2008-04-07
> **roachk71 said:**
> Mine's an integrated nVidia GeForce 6150 LE. So far, in Gutsy, there have been numerous rendering and OpenGL hangs, but not in Hardy.

A bit of advice: Avoid Envy with this chipset; it made my machine unusable until a Gutsy re-installation (I traced this down to, believe it or not, a libc6 runtime library corrupted by the package somehow!)

Huh.  I have the same chipset, and the only way I could get graphics to work properly was to use Envy.

--Me

---

### Post by darren1270 on 2008-04-07
Just to chime in ... I have a geforce 5500 as well and has never given me problems....

Nvidia IMO shouldn't give problems but maybe I'm just lucky...lol

Good Luck!

Darren

---

### Post by sub2007 on 2008-04-07
I can only use AGP cards on my motherboard and I had problems finding an inexpensive one to run Compiz. I was more than happy with the onboard graphics but I wanted Compiz and so I had to upgrade. The one that worked for me was the ATi Radeon 9250 and it worked straight out of the box (using the open source driver) which was amazing, the only Linux distro I've tried so far that recognised the card and selected the correct driver out of the box. And it didn't break the bank for me either (I think I paid £40 at a local electronics shop which isn't bad for a 256MB card). It probably wouldn't hold up on graphically intensive gaming but for what it is - a cheap card capable of running Compiz without any hassle, it checks all the boxes for me.

Only thing is that if you are installing onto an existing installation of Ubuntu then you'll have to reconfigure XOrg - easily done but scary if you don't know what to expect. Just make sure you find out how to do that before you install.

---

### Post by darren1270 on 2008-04-07
> **sub2007 said:**
> 
Only thing is that if you are installing onto an existing installation of Ubuntu then you'll have to reconfigure XOrg - easily done but scary if you don't know what to expect. Just make sure you find out how to do that before you install.


That is an excellent point... When I did mine I thought I had broken my Ubuntu....lol

---

### Post by TenPlus1 on 2008-04-07
My Nvidia worked no problem although the fonts were a little weird, but after going to the terminal and typing:

sudo nvidia-settings 

and setting up my card that way (and sabing settings of course) everything looked perfect...

---

### Post by canthus13 on 2008-04-07
wow.. I did once have a problem with XP install hanging with a Suma GeForce2 MX.  I had to use an old Monster Fusion to install, and then swap it out for the GeForce.  Maybe there's a similar issue with some cards?  Seems kind of drastic, though.

--Me

---

### Post by anewguy on 2008-04-07
I appreciate all of the replies so far.  My problems so very similar to one of the people who replied - Envy resulted in a non-readable X gui, the drivers direct from NVidia - even after following all the posts in the NVidia Linux forum for what to remove, what to set, etc. - still resulted in compilation errors -> it says the nvidia.ko was compiled with a different version of the compiler than the kernel so I end up with no nvidia module.  I've tried every config you can mention - everything still results in an unreadable X gui.  If it's possible, I'm starting to wonder if the friend who gave the card to me perhaps modified the BIOS on the card - he's the kind of guy who just doesn't seem to understand leaving something as-is.  At any rate, this card won't work.

So, if I'm looking on EBay and find a card cheap enough for me, will I be able to get decent compiz performance with a KT7-RAID mb with an Athlon 1000 and 512mb of memory?  In particular, as some have mentioned, a FX-5200 or FX-5500?  Will such as card work in agp 2x and 4x slot?

Thanks for the input, it is greatly appreciated to this frustrated old duffer !!  :)

---

### Post by anewguy on 2008-04-08
> **fettster said:**
> My GeForce card has given me loads of problems.  I've been trying for months now to get the right driver enabled and working properly (Yes, I have used Envy, I've downloaded it straight from NVIDIA, I've used the one in the restricted drivers menu, I have tried just about everything I can find and it still won't work) If someone could please refer and anewguy and me to a good cheap video card, I would be more than happy to get rid of my GeForce card.

Something of interest that may help you - it has helped me!  I haven't installed the nvidia driver yet, but I  *AM* running off the card with the vesa driver right now!!  First time with a readable GUI.  I did a search on the net (yahoo) and found a site that the flash utilities and the bios's for various cards in a database.  I tried the rev.1 - didn't help.  I tried the rev.2 - didn't help.  Tried the rev.3 - BINGO - I have a GUI now!  I could send you the utility and the bios if you want to try.

I just got this far, so I'm going to try Envy now, but I know I deleted a LOT of stuff following the nvidia Linux forum, so I just hope it works now!

:)

---

### Post by anewguy on 2008-04-08
Well, so much for that.  Yeah - I have a GUI, but no nvidia drivers.  I did a complete from scratch install of 7.10.  Then I tried enabling the restricted drivers and rebooting.  No good.  So I went back (I have the driver as "nv", but the restricted manager says none are enabled and none are in use, so I don't know if "nv" is a built-in or if it is falling back to vesa.  Tried nvidia-settings - said I needed to install the driver first!!!

So next I tried Envy.  Thought I might be in luck - it did a whole lot more this time than in the past.  I had to restart it a few times, but it eventually went through.  It changed xorg.conf driver to "nvidia" - on reboot it failed saying it couldn't load the nvidia driver.

So, for now, I'm running at a low resolution and the PC actually seems slower.  I did something I really couldn't afford to but did anyway:
 - bought a used XFX FX-5200 with 128mb
 - bought a used ATI Radeon 9250

When these get here, I'm trying the Radeon on a fresh install first - I've about had enough fighting with nvidia for now.  If that doesn't work, I'll try the FX-5200 - again with a fresh install.  What ever works I keep, what ever doesn't I sell along with this pos.

I'll post back later after everything arrives and I try again.

---

