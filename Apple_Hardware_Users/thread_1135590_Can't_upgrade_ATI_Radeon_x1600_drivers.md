---
title: "Can't upgrade ATI Radeon x1600 drivers"
date: 2009-04-24
forum: Apple Hardware Users
---

### Post by burvowski on 2009-04-24
Hi,

I am a new user to Ubuntu (9.04) on a 1st generation Macbook Pro. I installed 9.04, and everything works great, except that, when turning on a few 3D effects in compfiz, the system slows down to a halt, making it unusable. I've been playing around and trying to install the proprietary drivers for the past week, with bad results. Usually, my efforts result in Ubuntu not being able to boot, and me getting a black screen and weird static instead:

[http://i41.tinypic.com/2rxjm91.jpg](http://i41.tinypic.com/2rxjm91.jpg)

I've tried getting help in the #ubuntu irc channel, and while everyone who helped was incredibly patient and helpful (for which I am extremley thankful for, and made me already glad I have switched to Linux), we haven't been able to figure it out.

I've gotten that screen with static twice, after going into Synaptic, and searching for "ATI Radeon" and checking the drivers option that comes up. I've been forced to reinstall 9.04 after each of these incidents.

I'd really really like to play around with Ubuntu's eye candy, so any help is really appreciated.

---

### Post by burvowski on 2009-04-24
Ok, I just tried again and got that black screen again (posting from OS X). Is there anyway to fix my Ubuntu system without reinstalling the OS? It's becoming very tedious/frustrating.

---

### Post by cyberdork33 on 2009-04-24
I am using the X1600 in my iMac, and it works great with nothing else to install. My screen will look like that for a second before gdm starts up. My guess would be that there are some bad compiuz plugins you are trying to enable. Try to limit the number of "effects" that you are trying to use at once or narrow it down to the culprit. Either way, I don't think it is a graphics driver issue.

---

### Post by burvowski on 2009-04-24
No...it freezes there only after I install the drivers, nothing to do with enabling certain effects. The last freeze I got had no effects enabled.

---

### Post by cyberdork33 on 2009-04-24
> **burvowski said:**
> No...it freezes there only after I install the drivers, nothing to do with enabling certain effects. The last freeze I got had no effects enabled.
Hmm.... I guess I am saying that you should not need to install drivers... Have you tried enabling effects without first installing any drivers?

---

### Post by burvowski on 2009-04-24
Thanks for the quick reply.

I got it working (well, back to booting). I booted into recovery mode, entered the console, and did:

```
sudo apt-get remove fglrx*
``````
sudo dpkg-reconfigure xserver-xorg
```

It seems like my card doens't support 3D graphics well in 9.04, because of a new xserver version or something, despite having 256 megs of dedicated video ram. I guess I will go back to OS X until I can buy a new laptop with a nvidia card or until the drivers get better. :(

---

### Post by Richae on 2009-04-25
it's bad news that older ati drivers are no longer supported by AMD from 9.04 on while the open source driver install by default is slow. you are back to mac and I'm to windows 7.

---

### Post by pxwpxw on 2009-04-25
> **Richae said:**
> it's bad news that older ati drivers are no longer supported by AMD from 9.04 on while the open source driver install by default is slow. you are back to mac and I'm to windows 7.

Does that lack of support apply to the AMD drivers here 
 
 [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I had problems compiling with kernel headers in ubuntu904-amd64 (BETA) for Radeon2600HD, also in debian with 2.6.29 kernel.

---

### Post by burvowski on 2009-04-25
> **Richae said:**
> it's bad news that older ati drivers are no longer supported by AMD from 9.04 on while the open source driver install by default is slow. you are back to mac and I'm to windows 7.

Yeah, it's like Ubuntu took a step backward for us ATI card users, which have to be a pretty sizable chunk. I've heard that the open source drivers are expected to be improved by the end of summer, though, so my fingers are crossed for that. I really did love Ubuntu for the few days I got to try it and would drop OS X and Windows with no hesitation to use it. :(

---

### Post by cyberdork33 on 2009-04-25
is the open source driver really that bad? I haven't had any issues with it...

---

### Post by burvowski on 2009-04-25
Yes, because it doesn't let me take advantage of the money I paid for a 256 meg video card. (which at the time, wasn't cheap). Even moving a window in ubuntu had bad graphics on my system :(

---

### Post by angryfirelord on 2009-04-25
> **burvowski said:**
> Yeah, it's like Ubuntu took a step backward for us ATI card users, which have to be a pretty sizable chunk. I've heard that the open source drivers are expected to be improved by the end of summer, though, so my fingers are crossed for that. I really did love Ubuntu for the few days I got to try it and would drop OS X and Windows with no hesitation to use it. :(
The problem doesn't lie on Ubuntu, it's a fault of ATI for getting rid of support for their cards. In order for Ubuntu to use the newest X Server, it had to include Catalyst 9.4, which drops support for a bunch of cards.

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English")
> AMD has moved a number of DX9 ATI Radeon™ graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.

The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series
I know your pain because I have an X1600 in my laptop and I can't simply upgrade. Fortunately, the open-source driver, radeonhd, is moving at a quick development base and already has some very basic 3D support. I'd expect that in a year or two it should be usable enough to play 3D games with it. In the meantime, you can keep a copy of 8.04 or 8.10 loaded on your computer or just boot into Windows when you need to play a game.

---

### Post by bobbyi on 2009-04-25
This is pretty lame :(

---

### Post by csmth on 2009-04-26
> **cyberdork33 said:**
> is the open source driver really that bad? I haven't had any issues with it...

The open source driver does have a few issue for me, despite my games are not really demanding in graphics.

I used to play civilization 4 (and all expansions) on Wine. After upgrading to 9.04, the game is no longer playable. I can view the menu but not the actual game.

I am using X1250 chipset, but that is not much difference.

---

### Post by burvowski on 2009-04-26
Does anyone know where I can get a live cd download of 8.04?

This link [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/) does not work for me.

edit: nevermind, i found it

---

### Post by Jonne on 2009-04-30
Can anyone tell me if compiz and video accelleration work properly with the FOSS drivers? I don't care about 3D games on this box (this is a work box), but decent compiz is really something I need for productivity and stuff.

I have a x1600 card, btw.

---

### Post by cyberdork33 on 2009-04-30
> **Jonne said:**
> Can anyone tell me if compiz and video accelleration work properly with the FOSS drivers? I don't care about 3D games on this box (this is a work box), but decent compiz is really something I need for productivity and stuff.

I have a x1600 card, btw.
it works fine on my iMac

---

### Post by Hakrabim on 2009-05-19
Does anyone know how to activate the extended desktop (using 2 screens), without the flgrx driver?

---

### Post by cyberdork33 on 2009-05-19
> **Hakrabim said:**
> Does anyone know how to activate the extended desktop (using 2 screens), without the flgrx driver?
you should be able to go to System > Preferences > Display

---

### Post by Hakrabim on 2009-05-20
Thanks for your answer.

I tried that, the problem is that if I try to start ubuntu with the S-video cable conected, both of the displays will appear blank; and if I try to plug it afterwards ubuntu will not detect the second screen.

Any ideas?

---

### Post by yoszik on 2009-08-22
> **angryfirelord said:**
> The problem doesn't lie on Ubuntu, it's a fault of ATI for getting rid of support for their cards. In order for Ubuntu to use the newest X Server, it had to include Catalyst 9.4, which drops support for a bunch of cards.

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English")

I know your pain because I have an X1600 in my laptop and I can't simply upgrade. Fortunately, the open-source driver, radeonhd, is moving at a quick development base and already has some very basic 3D support. I'd expect that in a year or two it should be usable enough to play 3D games with it. In the meantime, you can keep a copy of 8.04 or 8.10 loaded on your computer or just boot into Windows when you need to play a game.

It's not ATI fault - because they shouldn't modify their drivers because of new xserver. New xserver should support old drivers anyway....

---

### Post by angryfirelord on 2009-08-22
> **yoszik said:**
> It's not ATI fault - because they shouldn't modify their drivers because of new xserver. New xserver should support old drivers anyway....
True, the Xorg team has been absolutely no help in setting guidelines for long-term standards development. But don't forget, ATI also dropped these cards for the Windows version too. Quite frankly, I don't see any reason why they would have had to do that for a relatively modern video card, especially for laptop users.

---

### Post by Taenon on 2009-08-23
I'm on the exact same laptop, and have kind of given up on using Ubuntu as the primary OS. I'll boot 9.04 or CrunchBang in a VirtualBox VM if I want to use some of the excellent programs not available for OSX (Gnumeric :( ), and I'm counting the days till I can build a desktop and have a good time with a powerful Ubuntu machine. 

The open source drivers work, I get decent graphics performance (including compiz effects, haven't tried gaming), haven't tried dual-head with this version either, but I do get that band of fuzz at the top before gdm starts. 

Its usable but I feel neutered, so I end up going back to OS X. That and firefox + default gnome vertical space utilization is a nightmare on a 15 inch screen....

---

