---
title: "nvidia driver re-install"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by GlennW on 2007-07-15
Apologies first. I'm a newb with Linux but loving it. I know there has been a lot of talk re nvidia installation and the like. However, I couldn't find (or didn't have the patience to) help for my issue at the moment.

I just purchased an Nvidia Geforce 6200 256MB DDR2 TV DVI card. Had a couple of minor issues upon installation. No problem. I was still getting the occasional fuzzy screen and was therefore thinking that I needed a newer or more accurate driver. I found on the forums here a how-to for the nvidia geforce 6200! I began implementing the rather long process. It called for the removal of previously installed nvidia drivers. 

[INDENT]sudo apt-get remove --purge nvidia-glx[/INDENT]

then

[INDENT]chmod 777 NVIDIA-Linux-x86-100.14.11-pkgl.run[/INDENT]

[INDENT]sudo invoke-rc.d gdm stop[/INDENT]

Now this is where I am. The equivalent of MS's blue screen of death! No screens available...
How do I get back to the place where I can install the correct driver(s)?

---

### Post by techno-mole on 2007-07-15
have you tried using envy ? its an application that helps you to install the drivers for your graphics card, it more or less does it for you.
its what i use, and i think it works very well.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) have alook at this website, it should help you.
you can download it in .deb format and just click it and it should install ok.

cheers

---

### Post by GlennW on 2007-07-15
Thanks for the quick response Technomole. The issue that's pressing is that upon start up, it stops at some screen with 600X400 rez and saying that there's piles of stuff missing and that there's "no screens" available. I wouldn't have an issue to follow any advice but ubuntu doesn't even load!!

---

### Post by forestpixie on 2007-07-15
you can reconfigure x and start again if thats the problem - which if you've deleted the video driver  I assume is.

you should be able to login in where you are then 

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

I had to do same a while back - I am fairly sure you can just let it default each time it asks
 then you should be back to default without the nvidia driver

---

### Post by Ralob on 2007-07-15
> **forestpixie said:**
> you can reconfigure x and start again if thats the problem - which if you've deleted the video driver  I assume is.

you should be able to login in where you are then 

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

I had to do same a while back - I am fairly sure you can just let it default each time it asks
 then you should be back to default without the nvidia driver

Indeed, I had this issue many times myself when I first started and it is very fixable. If this does not work for some reason, let us know.

---

### Post by GlennW on 2007-07-15
Thanks guys for your quick response. These forums are the best. Just to clarify, I rebooted in "recovery mode" and I ended up with a black screen with:

[INDENT]root@glenn-desktop:~#[/INDENT]

I have no idea what to do from here. Please advise...

---

### Post by Outrunner on 2007-07-15
Type the command given above:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can put a tick(asterisk, in this case) by pressing the spacebar

---

### Post by GlennW on 2007-07-15
Thanks again. I'm on it.

Have a great day. Oh yeah, I almost forgot - Linux rules!!

---

### Post by techno-mole on 2007-07-15
you can run envy in text mode, but as you said you cant get into ubuntu to download it, so re-configuring the xserver is the best bet, but if you get it sorted then i would suggest installing envy, because if you have the same problem again you can use envy to remove and then re-install the driver and in theory you should then be able to restart the system and itll load ubuntu up with no problems.

---

### Post by Outrunner on 2007-07-15
By the way, you don't need envy to install the nvidia drivers... It takes less time to

```
sudo aptitude install nvidia-glx-new
```

---

### Post by techno-mole on 2007-07-15
im lazy thats why i use envy :)
ive also had some problems by trying to do it myself :)
cheers for that line though, i might give it a try next time.
cheers

---

### Post by GlennW on 2007-07-15
I followed the advice given and ran envy but when looking at xorg.conf here's the important section:

[INDENT]Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection[/INDENT]

I still can't bring the screen rez up to where it was previously and when going to System>Screen Resolution all I get is 1024 X 768 @ 50 Hz. That's almost painful plus it's "flickery." 

I thought that Envy would get it done. Now what?

---

### Post by techno-mole on 2007-07-15
ok, i take it your running an nvidia card, so if you go to applications --> system tools there should be an nvidia icon, if you click it it should give you various options for doing stuff with your graphics, one of which is screen resolutions.
you should be able to change to a resolution and refresh rate more to your liking, however it will only keep the settings for one session, so instead of clicking the icon as i mentioned above (if its not there it might mean things didnt install properly) open terminal and type - sudo nvidia-settings.
this should open up the nvidia control panel, you should then be able to change your resolution and refresh rate, once you've done that if you click on save to x configuration file it should save the settings so that when you restart you should have the resolutions and such you want.
the screen resoltuions are the second option down - x server display configuration.
you can also edit xorg.conf.

for example here are some lines of my xorg.conf that have resolutions in it - 

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
Option "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x800_75 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
Option "AddARGBGLXVisuals"
    EndSubSection
EndSection

you can add the resolutions you want by adding them to xorg.conf, if you want a certain resolution you can add that aswell, where mine says -  "metamodes" "1280x800_75 , obviously the 1280x800 is the resolution, the _75 is the resolution, leaving that out will mean it will use the refresh rate it feels is best depending on the resolution.

---

