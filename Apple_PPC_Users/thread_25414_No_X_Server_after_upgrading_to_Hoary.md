---
title: "No X Server after upgrading to Hoary"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by medina on 2005-04-10
Hi,

On Friday I made -upgrade from Warthy to Hoary 5 on an iBook g3. Everything seemed to work ok until I restarted. Since then a message appears saying the following:

"I cannot start the X Server. It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem? Yes/No"

It's the same wether I click "yes" or "no". There is no information after.

A second message appears then:

"I will disable this X Server for now. Restart GDM when it is configured correctly"

Now I allways work with the shell, even with Lynx for internet, and it's of course very uncomfortable. :-(

Anyone has the **Hoary with an iBook g3**? The file with the configuration? xorg.conf or something like that?

thanks

Iñigo

---

### Post by heimo on 2005-04-10
No iBook here. But have you tried to reconfigure xorg? Like this:
```
sudo dpkg-reconfigure xserver-xorg
``` 
It goes through of lots of settings, defaults are most of the time ok. The part you should particularly pay attention is graphics cards chipset and screen resolution.

---

### Post by medina on 2005-04-10
[QUOTE=heimo]No iBook here. But have you tried to reconfigure xorg? Like this:
```
sudo dpkg-reconfigure xserver-xorg
``` 
It goes through of lots of settings, defaults are most of the time ok. The part you should particularly pay attention is graphics cards chipset and screen resolution.[/QUOTE]
 Yep, I already made it. Message after is neither funny:

"xserver-xorg is broken or not fully installed"

If I make again -upgrade, though there are packages it stops because of problems with dependencies in Firefox.

I also tried "dpkg-reconfigure xserver-xfree86" and message was the same: "broken or not fully installed". :-(

---

### Post by heimo on 2005-04-10
I'd try:
```
sudo apt-get install -f
``` 
Check for any signs of broken dependencies or missing packets. You could also try
```
sudo apt-get install ubuntu-desktop
``` 
to see if anything is missing.

EDIT: Oh, and this one:
```
sudo dpkg-reconfigure -a
```

---

### Post by medina on 2005-04-10
This is the current file of the xorg.conf

---

### Post by heimo on 2005-04-10
Helpful log file to keep eye on (when starting Xorg)
```
/var/log/Xorg.0.log
``` 

Your problem is not probably in the xorg.conf file. I tried it on my setup - as we have different graphics cards, I had to change ati to nvidia. Other changes I did was: uncommented this line:

```
#       Load    "xtt"
``` 

And I had to increase Monitor section's VertRefresh, but that is not probably your problem as you have LCD and mine is CRT.

---

### Post by medina on 2005-04-10
Hi heimo,

I love you. ;-)

I ran <apt-get install -f> and reconfiguring GDM started suddenly the X Server and everything goes ok. No doubt it was not fully reconfigured. I hope I have no problem when I reboot. :-(

Thanks a lot heimo :-)

Iñigo

---

### Post by Gray Ghost on 2005-04-10
[QUOTE=heimo]No iBook here. But have you tried to reconfigure xorg? Like this:
```
sudo dpkg-reconfigure xserver-xorg
``` 
It goes through of lots of settings, defaults are most of the time ok. The part you should particularly pay attention is graphics cards chipset and screen resolution.[/QUOTE]

I'm trying to solve a problem that is just about the same as this one, I did what you said and it presented me with a list, how do I know which one to choose?

---

### Post by heimo on 2005-04-11
Ok, I'll do it on my computer (right now), and go through different options and reasons why I select each one. Sorry if this is duplicative, feel free to skip ahead.

First I execute:
```
sudo dpkg-reconfigure xserver-xorg
``` 

**1**
First I get question if I want to attemt autodetecting recommended X server. I select *YES*.

*2*
Now I'm presented with a long list of video card / chipsets. 
```
 
apm                                                           &#9474;  
ark                                                           &#9474;  
ati                                                           &#9474;  
chips                                                         &#9474;  
cirrus                                                        &#9474;  
cirrus_alpine                                                 &#9474;  
cirrus_laguna                                                 &#9474;  
cyrix                                                         &#9474;  
fbdev                                                         &#9474;  
glide                                                         &#9474;  
glint                                                         &#9474;  
i128                                                          &#9474;  
i740                                                          &#9474;  
i810                                                          &#9474;  
imstt                                                         &#9474;  
mga                                                           &#9474;  
neomagic                                                      &#9474;  
newport                                                       &#9474;  
nsc                                                           &#9474;  
nv                                                            &#9474;  
nvidia                                                        &#9474;  
rendition                                                     &#9474;  
riva128                                                       &#9474;  
s3                                                            &#9474;  
s3virge                                                       &#9474;  
savage                                                        &#9474;  
siliconmotion                                                 &#9474;  
sis                                                           &#9474;  
tdfx                                                          &#9474;  
tga                                                           &#9474;  
trident                                                       &#9474;  
tseng                                                         &#9474;  
vesa                                                          &#9474;  
vga                                                           &#9474;  
via                                                           &#9474;  
vmware                                    
```

You could check your computers spesification (from manufacturers website) to get clues for which one to choose, or you could open your computer case and see the name of the manufacturer on the card. Most of the modern desktop computers have Nvidia's (nv and nvidia) or Ati's (ati) cards - some integrated graphics cards use nvidia driver too. I'm not 100% sure but on the list i740 and i810 look like Intel's integrated chips. mga stands for Matrox (not so usual these days, but was very popular late 90's). On very old computers you can have cards with s3 chips, or Cirrus Logics' (cirrus) chips.

vesa and vga are general choices which should work for almost anyone, but those are bad choices because they don't support all the resolutions or hardware 3D acceleration. If you don't know which one to choose, you can guess and try to reconfigure until you get it right. Or you can send everything you know about your computer, is it Dell/HP/IBM/Apple, is it desktop/laptop, minitower/miditower, what model is it (could be written on the back or side of the computer / or receipt) on this list and get some hints.

For me nv and nvidia choices are the best ones (nvidia has hardware acceleration, but it's buggy at the moment). So I select nv.

**3**I can give name to my graphics / video card. Default is ok, all I do is press enter.
```
NVIDIA Corporation NV34 [GeForce FX 5200]
```

**4** I'm asked for video cards bus identifier. Leave it to default. Mine happens to be:
```
PCI:1:0:0
```

**5** I'm asked for amount of memory on my card. This one can be left empty, unless there's something special about your card. Leave the field empty.

**6** Question about enabling framebuffer can be answered *YES.* or *NO*, but as the text on this box suggests, one could work for you, one could cause problems. I select *YES*.

**7**Keyboard layout? us for English keyboards, de for German, for me ```
fi
```

**8**XKB rule, best bet is the default *xorg*

**9**Keyboard model? English keyboards pc104, "European" keyboard pc105.

**10** Keyboard variant? Leave it empty.

**11** Keyboard options? Safe to leave empty.

**12** Mouse autodetection. Select *YES* and move your mouse. If you have PS2 mouse, select /dev/psaux or /dev/input/mice - if you have very old mouse with 9-pin connector, and it's in first serial port, select ttyS0, for second port ttyS1. /dev/input/mice should be safe bet for most of us.

**13** Emulate 3-button mouse? If you have 2-button mouse, select *YES*, otherwise *NO*.

**14** Enable scroll events? If you have wheel mouse, select *YES*, otherwise *NO*.

**15** X modules. You can go with defaults, but should probably check that at least dri and glx are enabled.

**16** Write default files section to configuration file? *YES*

**17**Write default DRI section to configuration file? *YES*

There was ~10 second pause between this and next question.

**18** Enter an identifier for your monitor. Leave it to default, but if it's blank, choose something (whatever reads on the front side of your monitor).  *Generic Monitor* is fine for me, although I know mine is Hitachi CM752ET 19" CRT.

**19** I'm presented with a list of screen resolutions with some of them preselected. You can consult your monitor spesification for good values. I unselect 640x480 and 800x600 and select 1024x768, 1280x1024. For modern 15" LCD/TFT, select only 1024x768, for 17" modern LCD/TFT select only 1280x1024. For CRT's (cathode ray tube), 15" => 1024x768, 17" => 1280x1024, 19" => 1400x1050. These are not only possibilities, but should be safe ones.

**20** Please choose a method for selecting your monitor characteristics. Select *Medium*

**21**  Choose the "best" resolution and refresh rate you believe your monitor capable of. You are not choosing default resolution. You are defining the possibilities of your monitor. For example, I use 1400x1050 resolution or 1280x1024 resolution on my 19" CRT, but at this question I have to choose 1600x1200 @ 60Hz, and I'll get 1400x1050 @ 86 Hz. This depends mostly on your monitor and you can find the right value from manufacturers website (or you can ask here, if you can give us the manufacturer and model name).

**22** Write monitor sync ranges to configuration file? I select YES, but NO should be safe bet, too.

**23**  Please select your desired default color depth in bits. This depends on the amount of memory on your graphics card. You should select 24 or 16. I'll select 24.

**24**  That's it! At least for me it was. Now I can try to start xorg by typing
```
startx
```
and if everything works fine, I'll press ctrl+alt+backspace to exit xorg and start gdm (login manager)
```
sudo /etc/init.d/gdm start
```

----------------------------------

And would the insructions be complete if everything just worked? No. Because everything doesn't work all the time. :) Sometimes you run into trouble. Bad instructions, bad values chosen, missing software and so on.

I actually did what I say abowe - tried those settings and they were not identical to my previous setup. (There's also some inconsistency in the instructions, my choices - I choose only 1240x1024 and 1024x768 resolutions but I'm also talking about 1400x1050). I run startx and X didn't start up.

At this point, you should watch what errors you get on the screen or /var/log/Xorg.0.log file. I saw "no screens found" which is typical if you messed up the resolutions and "monitors capabilities" part. The configuration file for xorg is /etc/X11/xorg.conf - so I went there looking for Section Monitor and found:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection
```

These are the values you're actually selecting when you choose the 1600x1200 @ 60 Hz or anything on the resolution / refresh rate menu. These are used to select the actual resolution your monitor is cabable of. If set too low, you don't get any valid resolutions and you get "no screens found" error. If set too high, you get too demanding signal from graphics card to monitor and monitor probably says something like "out of sync". These values:HorizSync and VertSync can be found in your monitor spesification (probably just the upper limits). I'm going to Google my monitors model 'CM752ET'.

First hit is:
[http://66.102.9.104/search?q=cache:jMyS_l3leWUJ:www.hitachidigitalmedia.ru/products/catalog/cm752et.pdf+CM752ET&hl=en](http://66.102.9.104/search?q=cache:jMyS_l3leWUJ:www.hitachidigitalmedia.ru/products/catalog/cm752et.pdf+CM752ET&hl=en)

And on that page I can see that my monitor can do 1600x1200 @ 75Hz. That's much better than the 60Hz I chose. I'm going back, through all those settings...
(to be continued)

This time I choose two questions differently. I choose NOT to use framebuffer and I choose 1600x1200 @ 75 Hz for the best my monitor can do. Now typing startx starts xorg, but the screen flickers at 60Hz. That's awful for your eyes. I'll go to terminal window and check the xorg.conf Monitor section:

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     30-60
EndSection

```

There must still be something wrong, but at least the X is now working. Iäll flip to other resolution (1024x768) by hitting ctrl+alt+numberpad's +. That also gives me only 60Hz. (Normaly you get better refresh rate for lower resolutions)

Back to Google. This time I search for CM752ET xorg - and only hit I get is this page:
[http://www.javadesktop.org/forums/thread.jspa?messageID=54015](http://www.javadesktop.org/forums/thread.jspa?messageID=54015)

Someone somewhere has already found out what's best for my monitor. On this discussion forum I find xorg.conf file with this Monitor section:

```
Section "Monitor"
Option "CalcAlgorithm" "CheckDesktopGeometry"
DisplaySize 367 276
HorizSync 28-96
Identifier "Monitor[0]"
ModelName "CM752ET"
VendorName "HITACHI"
VertRefresh 50-180
UseModes "Modes[0]"
EndSection
```

I take three lines of it. DisplaySize, HorizSync and VertRefresh and put it in my own xorg.conf. I still can't get more than 60Hz! And I'm getting a bit frustrated.

I go to terminal window and run: sudo xresprobe nvidia (nvidia here is the driver I'm using, same choice as in the menu when we configured xorg). I should get a list of frequencies and other information like this:

```
id: CM752
res: 1600x1200 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 31-101 50-160
disptype: crt

```

Here I can see the horizontal sync rate 31-101 and vertical 50-160. I put those into xorg.conf unded Monitor section, and vo la! I finaly get decent resolution and refresh rate 1280x1024@85Hz. Now I can go to System->Preferences->Screen Resolution to select some other screen mode, if I want to.

---

