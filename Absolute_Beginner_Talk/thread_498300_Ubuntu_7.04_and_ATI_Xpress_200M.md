---
title: "Ubuntu 7.04 and ATI Xpress 200M"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by originald on 2007-07-11
OK does anyone actually have Ubuntu 7.04 and ATI Xpress 200M working together properly ?

I have been trying for days now to get the 3D graphics to work but nothing yet. I am now using the latest drivers from the ATI site and is fine running 2D nothing wrong there, but when I try to run a 3D all I get it crazy flickering / tearing (The flickering / tearing is constant and extremely bad). The speed of the 3D graphics is great but cannot get rid of the flickering.

When I do a fresh install of Ubuntu 7.04 the 3D works but is too slow to use anything in 3D.

Does anyone have any ideas ? Or managed to get these too working together without flickering 3D ?

Thanks

---

### Post by rlozano on 2007-07-11
From my experience, Xpress 200M of ATI is not really working well in Ubuntu. Since Dapper Drake, I have not gotten a good performance of 3D in ATI Xpress 200M.

Try searching around the forum, you maybe able to find some success.... :-)

---

### Post by originald on 2007-07-11
I did find a thread that seems as though some people solved the flickering problem here [http://ubuntuforums.org/showthread.php?t=286527&page=3]("http://ubuntuforums.org/showthread.php?t=286527&page=3") but the problem is I don't have anyway to change the settings they did in the BIOS as I don't have those options. Is there anyone other way of doing this ?

---

### Post by arron on 2007-07-11
I have my 200m working very well with fiesty.  I just used the restricted drivers in system -> administration and voila it worked.  I now run NWN with better performance than under windows.  Try a fresh install with that, then run a 3d game.  Under 6.10 it was a pain to install the drivers from ATI, there is a big howto here that you can try if you have no luck with the restricteddrivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Good luck!

---

### Post by arron on 2007-07-11
I should of mentioned my performance:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

$ glxgears
7883 frames in 5.0 seconds = 1576.496 FPS
8197 frames in 5.0 seconds = 1639.346 FPS
7933 frames in 5.0 seconds = 1586.576 FPS

```

I know this is slow for some, but works awesome for me.

---

### Post by originald on 2007-07-11
Yeah I think i've been through that tutorial before, but will try again.

I've tried just enabling the restricted drivers first of all but the 3D is amazing slow. This is why I tried the ones from the ATI site which are fast but the flickering makes it impossible to use.

---

### Post by originald on 2007-07-11
Those are the sorts of the frame rates I get to, but the flickering I get is really really really bad.

---

### Post by arron on 2007-07-11
What is your resolution, maybe that is to high for the screen to handle with 3d.  Have you tried some different 3d games?  Does glxgears flicker?  What kind of laptop?

---

### Post by originald on 2007-07-11
Laptop is a Toshiba L30 Celeron M 410 1.86 (i think, at work at moment) and resolution 1280 X 800. Not tried different res though

---

### Post by lamalex on 2007-07-11
[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

this is the howto I wrote for this card and feisty with beryl. It has worked for most people with ATi card, I have an x200m and it works quite well. Lucky for us a lot of work is being done right now in the development of a free driver for our card. Compiz currently partially works, they're getting close =)

---

### Post by originald on 2007-07-11
Thanks for the link lamalex but all I want to do is to be able to use 3D apps like google earth or some of the 3D screensavers.

I really don't understand how some people have got it working for them and I have done the same and get a really bad flickering on all 3D.

Surely someone knows how to sort this flickering ?

---

### Post by stchman on 2007-07-11
> **originald said:**
> OK does anyone actually have Ubuntu 7.04 and ATI Xpress 200M working together properly ?

I have been trying for days now to get the 3D graphics to work but nothing yet. I am now using the latest drivers from the ATI site and is fine running 2D nothing wrong there, but when I try to run a 3D all I get it crazy flickering / tearing (The flickering / tearing is constant and extremely bad). The speed of the 3D graphics is great but cannot get rid of the flickering.

When I do a fresh install of Ubuntu 7.04 the 3D works but is too slow to use anything in 3D.

Does anyone have any ideas ? Or managed to get these too working together without flickering 3D ?

Thanks

My Toshiba laptop (A135-S2246) has a Celeron M processor and a Radeon XPress 200M.  It works very well under Feisty.  I can run Google Earth.  I get excellent framerates running glxgears and fglxgears.

I run the restricted driver.

So yes Ubuntu does support the 200M.

---

### Post by originald on 2007-07-12
Hi,

Can you post your xorg.conf so I can check it against mine and see if there is something not right ?

What steps did you take to get it working ?

Thanks

---

### Post by Paul820 on 2007-07-12
I have the 200m built into my Acer Apire 5100 and it's working fine, just went to system->administration->restricted drivers manager, clicked it, it downloaded, installed, rebooted, works perfectly. I will post my xorg.conf if you want? Sorry you can't get yours working properly.

---

### Post by originald on 2007-07-12
Hi Paul820,

Can you post your xorg.conf, as I tried the way you explained in your post but the 3D I get has really bad flickering.

Thanks

---

### Post by originald on 2007-07-15
I have now checked my xorg.conf against someone who has this same chipset working on their version of ubuntu and followed the same procedure that they did to install the drivers but is still causing really bad flickering when using 3D.

The only thing I can think of now is that people are using an older version of the drivers.

Can anyone running Feisty Fawn and ATI Xpress 200M together with working 3D let me know what version of the ATI drivers they are using ?

Thanks

---

### Post by tarek on 2007-07-15
> **originald said:**
> OK does anyone actually have Ubuntu 7.04 and ATI Xpress 200M working together properly ?

I have been trying for days now to get the 3D graphics to work but nothing yet. I am now using the latest drivers from the ATI site and is fine running 2D nothing wrong there, but when I try to run a 3D all I get it crazy flickering / tearing (The flickering / tearing is constant and extremely bad). The speed of the 3D graphics is great but cannot get rid of the flickering.

When I do a fresh install of Ubuntu 7.04 the 3D works but is too slow to use anything in 3D.

Does anyone have any ideas ? Or managed to get these too working together without flickering 3D ?

Thanks

I have XPRESS 200M, worst card, anyways, I got it to work using:

Either:

The Restricted Driver Manager from the Administration menu. That got the TV-out working and the 3D acceleration. I'm running compiz-fusion too.

OR

If you want an ATI utility to manage TV-out and other settings, then I recommend using [Envy,]("http://www.albertomilone.com/nvidia_scripts1.html") 
It installs the latest ATI driver and setups an icon in the menu to control your card and enables 3D and TV-out.

Just to make sure you  have 3D enabled run: **fgl_glxgears** It will start a 3D cube.

*By the way, I have the card on a laptop so I had some problems with suspend and hibernate, actually I got that working last night, I'll add a how-to later today. If you or anybody is having the same problem with suspend/hibernate let me know.*

TK

---

### Post by RavanH on 2007-07-15
> **tarek said:**
> *By the way, I have the card on a laptop so I had some problems with suspend and hibernate, actually I got that working last night, I'll add a how-to later today. If you or anybody is having the same problem with suspend/hibernate let me know.*

tarek, both suspend and hibernate are doing strange things on my system (AMD64, Feisty 64bit, Radeon Xpress 200M)... so your how-to would be GREATLY appreciated! :-) 

--ravan

---

### Post by tarek on 2007-07-15
> **RavanH said:**
> tarek, both suspend and hibernate are doing strange things on my system (AMD64, Feisty 64bit, Radeon Xpress 200M)... so your how-to would be GREATLY appreciated! :-) 

--ravan

Here's my solution: [http://ubuntuforums.org/showthread.php?p=3024394#post3024394]("http://ubuntuforums.org/showthread.php?p=3024394#post3024394")

---

### Post by RavanH on 2007-07-15
> **tarek said:**
> Here's my solution: [http://ubuntuforums.org/showthread.php?p=3024394#post3024394]("http://ubuntuforums.org/showthread.php?p=3024394#post3024394")

Thanks! I'll try it out... Shall I post my results on that thread?

---

### Post by tarek on 2007-07-15
> **RavanH said:**
> Thanks! I'll try it out... Shall I post my results on that thread?

That'd be a good idea, since everybody there is having the same problem. Thanks.

---

### Post by bbfuller on 2007-07-16
Hello originald

I've just installed 7.04 on this laptop, an hp nx6125 with ati x200m graphics.

It was set up during installation with the ati driver.

I've just followed the instructions on this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

to install "linux-restricted-modules-kernel name" and "xorg-driver-fglrx" from the repositories.

I then manually changed the driver from ati to fglrx in xorg.conf and made the changes to the sections "ServerFlags" and "Extensions" as suggested.

I haven't modified anything else.

I have glxgears at a 2800 frame rate and fgl_glxgears at frame rates varying between 170 and 550, depending on, I presume, how many faces of the cube are being drawn.

If you want to see the xorg.conf file post back.

---

