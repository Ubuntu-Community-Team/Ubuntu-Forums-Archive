---
title: "Ati card on gutsy: &quot;The composite extension is not available&quot;"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-10-15
Hi, I've got an X850XT on my PC. I recently installed gutsy and wanted to enable compiz/(extra desktop effects in appearance).

When I installed my Graphics card through the Restricted drivers manager I tried enabling the extra desktop effects option in appearance. This first gave me the error message "The composite extension is not available". Then I installed xserver-xgl through synaptic and tried again. This time it waits around and then tells me "The effect could not be enabled".

What have I done wrong/haven't done?

---

### Post by swisscow on 2007-10-15
Hang on for a few days. Supposedly the new driver from ati 8.42 is due out which is rumoured to run compiz etc without xgl. On the other hand, I'll believe it when I see it!

---

### Post by Fixel on 2007-10-15
So there is no imediate solution?

---

### Post by Martje_001 on 2007-10-15
What do you see if you run 'compiz --replace' in a terminal? Is you card blacklisted?

---

### Post by Jape-2000 on 2007-10-16
> **Martje_001 said:**
> What do you see if you run 'compiz --replace' in a terminal? Is you card blacklisted?

I of course didn't start this topic, but I have the same problem. What does this output suggest?

> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Martje_001 on 2007-10-16
You should read this:
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by alexander.forster on 2007-10-18
i am in the same situation as Jape-200, with the same output. any help would be REally appreciated :D thanks!

---

### Post by scottfinman on 2007-10-18
Ditto, exact some problem that Jape-2000 has.

---

### Post by scottfinman on 2007-10-18
Tried using skip_checks as per the above wiki link, and it gives the following:

> Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


---

### Post by maxxym on 2007-10-18
I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

---

### Post by dynamethod on 2007-10-18
> **Fixel said:**
> Hi, I've got an X850XT on my PC. I recently installed gutsy and wanted to enable compiz/(extra desktop effects in appearance).

When I installed my Graphics card through the Restricted drivers manager I tried enabling the extra desktop effects option in appearance. This first gave me the error message "The composite extension is not available". Then I installed xserver-xgl through synaptic and tried again. This time it waits around and then tells me "The effect could not be enabled".

What have I done wrong/haven't done?

oh dude -.- i feel sorry for you man, i got an ATI Radeon X800 XT agpx8, ive never been able to get compiz-fusion or ANY eye candy working with it, and believe me ive jumped through some hoops trying to, tried every how to out there, i just install the fglrx driver (8.40) with envy and leave it be now :S, but if you manage to find a way let us know man!!

---

### Post by scottfinman on 2007-10-18
Confirmed - I had to do both of the above (just enabled Composite on xorg.conf didn't do it).

But working like a charm now!

---

### Post by dynamethod on 2007-10-18
OMG!!!! IT WORKS!!!! OMG!!!!

THANK YOU GUYS! ive been trying (this is no lie) about 3 months trying to get this eye candy!!!!! and it finally works!!!! yeaaaaaaaaaaaaah!!!

---

### Post by me_melb on 2007-10-18
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

Had same issue....done above steps and all good now....:guitar:

---

### Post by scottfinman on 2007-10-18
> **dynamethod said:**
> OMG!!!! IT WORKS!!!! OMG!!!!

THANK YOU GUYS! ive been trying (this is no lie) about 3 months trying to get this eye candy!!!!! and it finally works!!!! yeaaaaaaaaaaaaah!!!
Hehe, I think I felt the same way after wrestling through it all a year or so ago.

---

### Post by maxxym on 2007-10-18
> **me_melb said:**
> Had same issue....done above steps and all good now....:guitar:

HOLY S**T! I helped someone!! LOL

WOOHOO!!!


:)

I love this OS!!! Soooo much better than Kubuntu...I am installing Gutsy now on my home desktop :)

---

### Post by Savok on 2007-10-18
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...


Its not letting me save the changes. Says I dont have permission. How do I get around that?

---

### Post by scottfinman on 2007-10-18
I'm betting you missed typing 'sudo' when you typed 'sudo gedit /etc/X11/xorg.conf'

---

### Post by Savok on 2007-10-18
> **scottfinman said:**
> I'm betting you missed typing 'sudo' when you typed 'sudo gedit /etc/X11/xorg.conf'

actually i am an idiot and was just typing gedit /etc/X11/xorg.conf

that actually opened the file but wouldnt let me save the changes

when i type click alt+f2 and type in  sudo gedit /etc/X11/xorg.conf nothing happens at all

I am probably missing something here

---

### Post by maxxym on 2007-10-18
> **Savok said:**
> actually i am an idiot and was just typing gedit /etc/X11/xorg.conf

that actually opened the file but wouldnt let me save the changes

when i type click alt+f2 and type in  sudo gedit /etc/X11/xorg.conf nothing happens at all

I am probably missing something here

You need to do it from the terminal or Konsole or whatever you call it.. lol

so:

sudo gedit /etc/yadayadayada and hit enter

It will ask you for your password, so type in your root pass..then hit enter...it will open up file in text editor.. so scroll down to the very last section and change 0 to 1... save it and exit...

---

### Post by msak007 on 2007-10-18
I have the same card as the OP (X850 XT). As swisscow already stated, the new driver from ATI due out real soon (it's almost end of October) should have the composite extension enabled for the cards it supports so desktop effects will be working out of the box with AIGLX, without having to resort to using XGL. I'll wait until then as XGL has always been horribly slow for me, but it's nice to know how easy it is now to enable it with XGL (it was a pain in the *** last time I tried it several months back).

---

### Post by skompier on 2007-10-18
I've been trying for weeks to get this to work for my Radeon 9600. Very simple solution that WORKS!. Thank you.

---

### Post by pacofvf on 2007-10-18
i have problems too, i have ati 200m xpress here is my xconf
:confused:
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RC410 [Radeon Xpress 200M]"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RC410 [Radeon Xpress 200M]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "1"
EndSection

---

### Post by happymellon on 2007-10-18
> **pacofvf said:**
> i have problems too, i have ati 200m xpress here is my xconf
:confused:
# xorg.conf (xorg X Window System server configuration file)

Section "Extensions"
        Option          "Composite"     "1"
EndSection

What error message do you actually get?

---

### Post by drjiga on 2007-10-19
Yes!!! It all works. So simple.
Just follow what maxxym said and compiz will work. 
Edit xorg.conf  to Composit 1 
and download xgl 

Thank you maxxym, great work.

---

### Post by scomofo on 2007-10-19
I have restricted drivers enabled, and I did the composite "1" thing, but no luck.

I'm using the xpress 200m, when i try do "sudo apt-get install xserver-xgl"  i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libglitz-glx1 but it is not installable
               Depends: libglitz1 (>= 0.4.3+cvs20050728) but it is not installable


please help, i really want to get effects going.

---

### Post by Baggers on 2007-10-19
Maxxym  you are  hero, thanks for that I was inches away from retreating back to feisty.

---

### Post by gummo on 2007-10-19
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

Thank you for this very helpfull post it worked like a charm for me

---

### Post by jmpmjmpm on 2007-10-19
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...


worked like a charm on ati x1550 :-) thanks!

---

### Post by scomofo on 2007-10-19
I got it fixed now, i didn't have the proper repositories enabled. Thanks maxxym!

---

### Post by Kougaiji on 2007-10-19
after taking the advice, should I disable the proprietary drivers? I've done what you said, but it still says they cannot be enabled. I have a [newer] onboard ati chipset that reserves some ram for its memory and shares my cpu's power. It's powered by a dual core 2ghz 64 amd processor, and i know that it can handle things much more demanding than compiz. 

When I enable the composite extension and download xgl the system draws things horribly slow and it still isn't able to use desktop effects.

---

### Post by Jadd on 2007-10-19
That worked great for my ati 200m. Thanks people!

---

### Post by pointone on 2007-10-19
You're doing twice as much work as you need to here... all that's required is Xgl; no need to edit xorg.conf.

Simple... if you're using fglrx, just sudo apt-get install xserver-xgl, log out, and log back in.

---

### Post by DarkPegasus on 2007-10-19
Thanks **maxxym**. \\:D/ it finally works..... YIPPIE!

---

### Post by julien.fs on 2007-10-19
Works fine thanks

---

### Post by EAL on 2007-10-20
Thanks maxxym!  That worked for me as well.

> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

---

### Post by xyzyyz on 2007-10-20
Thanks for the info Maxxym.  I had already resigned myself to not being able to enable any compiz eye-candy due to having an ATI X1300.  I clicked on this forum post on a whim, saw your suggestion and figured since my gutsy install is pretty much a blank slate at the moment it was worth a try.  Now I can enjoy the graphical goodies like everyone else, so thanks again.

---

### Post by TekNullOG on 2007-10-20
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

OMG - Thank you so much! With previous releases I was never able to get this to work and I thought I was doomed again till I fallowed this advice! You da man!

BTW, I have an ATI X300 in my laptop if that might help others.

---

### Post by millfarm on 2007-10-20
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

Thanks, this seems to have worked for me as well..

Only problem is that this seems to have messed up my dual-head setup, the external monitor is still working, but no desktop appears there.. any ideas?

---

### Post by k3bab on 2007-10-20
> **maxxym said:**
> Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

That didn't work at all. The only thing it did was making everything worther. When I move the windows or scroll at web pages it lags like I was playing Half Life 2 with all details on max and using software rendering. And it puts a lot of crap on the screen. xP

---

### Post by soxs on 2007-10-20
I would say enabling the composite extension is quite stupid, as long as you use the non beta drivers from ati, which actually do not support the composite extension at all.
So i suggest everybody with an ATI card to leave composite disabled and only install the xgl-xserver and reboot. This is the only thing you actually have to do (exception: If you have any of the graphicsaccelerators posted here as allready mentioned: [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist))

---

### Post by tenmillionmilesaway on 2007-10-20
I had this propblem with my card (x850xtpe) and the only thing i had to do was enable the restricted driver and ```
sudo apt-get install xserver-xgl
```

Still a bit annoying tho as i didnt have to do anything on feisty.

---

### Post by johnnybgood115 on 2007-10-20
I have an ATI Mobility Radeon X300  ... when I change the composite extension parameter in xorg.conf from "0" to "1" and install xserver-xgl I reboot and get a black screen and get a black x as a cursor.  I need to reboot and revoert back my backup xorg.conf file.  Any thing else I can try?

---

### Post by omenz on 2007-10-20
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...


Thanks! Works like a charm.

---

### Post by ledenjes on 2007-10-21
The answer is simple: do not install the ATI driver through the restricted drivers manager.
If you did, uncheck the ATI driver in the restricted drivers manager. Then reboot your computer. After that you can set compiz-fusion to the max and enjoy the show. You will not be bothered by the message "The composite extension is not available".

The above mentioned method (by maxxym) does not offer an all-time solution and might even mess up your graphics in Ubuntu.

---

### Post by andreimatei on 2007-10-21
Hello guys,

I added Option "Composite" "1" to xorg.conf, I installed xserver-xgl, but no magic happened. When is the eye candy supposed to pop-up :) ? How can I check if compiz is enabled? How can I check if everythign is all right? Is xserver-xgl a different x server than x.org? If so, how can I check which one I'm using?

compiz-real --replace displays a FATAL error, about loading some texture from a pixmap and makes the machine unusable, keyboard doesn't work right after this.
 
Thanks

---

### Post by Bothered on 2007-10-21
My keyboard layout gets messed up if I install xgl. Is there any easy way to fix this?

---

### Post by ledenjes on 2007-10-22
to **andreimatei**: you have to change the looks of Ubuntu (under System | Preferences | ...). You will find "Visual effects". There you can change the value to "Normal" or "Extra". In this way you can enable the visual effects in Ubuntu.

to **Bothered**: you could change the keyboard layout again.

to both of you: you might just let Ubuntu choose the proprietary driver for you ATI graphics card and set the visual effects to the max. It just works. There is no need to use the "restricted drivers manager".

---

### Post by Bothered on 2007-10-22
The ati driver doesn't have good 3d performance on my system, and worse causes my system to hang at random intervals if using compiz-fusion. Hence I can't use the pre-selected driver.

---

### Post by light50 on 2007-10-24
> **soxs said:**
> I would say enabling the composite extension is quite stupid, as long as you use the non beta drivers from ati, which actually do not support the composite extension at all.
So i suggest everybody with an ATI card to leave composite disabled and only install the xgl-xserver and reboot. This is the only thing you actually have to do (exception: If you have any of the graphicsaccelerators posted here as allready mentioned: [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist))

Holy Crap! It was so simple all along. ATI X600. Works like a charm. Cheers soxs!!

---

### Post by orthorim on 2007-10-26
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

Thanks a lot!! This did it! 

ATI X1600 mobility here.

---

### Post by dragonlor20 on 2007-11-01
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...


This worked flawlessly on my Compaq Presario V2000 laptop with Gutsy. The last time I saw desktop effects on this laptop was in Dapper. Thank you so much.

---

### Post by floyd4one on 2007-11-07
seems to have worked fine with my x1800xt... now how do i configure the effects?

---

### Post by Aanidaani on 2007-11-07
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

I too had to use both steps, but now everything works great! Thanks! :popcorn:

---

### Post by johnnybgood115 on 2007-11-07
I've got an ATI mobility Radeon X300 on an IBM Thinkpad.  .. once i run through this tutorial and install xserver-xgl, I restart the xserver and my desktop environment goes black with an "X" cursor. .. any help?

---

### Post by Phryxus on 2007-11-08
When I install xserver-xgl Gnome won't start anymore. I get the log-in screen and can enter my username and password as usual, but during the log-in procedure my screen goes back to the log-in screen.

I have a ATI Mobility Radeon X700 and fglrxinfo gives:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6958 Release

Thanks in advance!

---

### Post by strabes on 2007-11-08
You can undo your changes to xorg.conf by using nano. Hit Ctrl+Alt+F2, log in, and then run:```
sudo nano /etc/X11/xorg.conf
```Then change the 1 back to a 0, hit Ctrl+O to save, Ctrl+X to exit, then Ctrl+Alt+F7 to get back to gdm. The restart X again with Ctrl+Alt+Backspace.

---

### Post by oamster on 2007-11-13
>  Originally Posted by maxxym  View Post
I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...:

Wow thanks man, I've been ng forever to get compiz to run and this finally worked!

---

### Post by ftaylor on 2007-11-13
maxxym you are an absolute legend. This has totally fixed my graphics card problems and ubuntu looks lovely now! Your advice should be made a main article on the ubuntu page in relation to ati cards.

---

### Post by thrice_loved on 2007-11-14
> First, run sudo gedit /etc/X11/xorg.conf
Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection

Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace

Easy peasy! 
Specifically I edited the config file (it didn't work) then installed the xserver-xgl and restarted the computer (restarting X has been buggy for me in the past) and it worked! :) 
I have an ATI graphics card (Raedon 9550) and it didn't work initially, but it does now.

Thank you :D

---

### Post by Solenoid on 2007-11-14
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

Thank you very much, works on ATI Radeon X1600XT.

---

### Post by djRobbieF on 2007-11-14
This also worked on my emachines m6805, which uses the ATI Mobility Radeon 9600 chip.  I'm using the restricted drivers, and had to install XGL following the instructions here.

Thanks!  How easy was that!

---

### Post by sunami900 on 2007-11-14
EXACTLY WHAT YOU DO IS GO INTO TERMINAL AND PUT THIS IN  sudo apt-get install xserver-xgl   THEN INSTALL IT IN THERE AND BOOM IT WORKS 

;)

---

### Post by Casual Fan on 2007-11-15
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

This worked for me--thanks!!!!!!!!!!!!

---

### Post by NineseveN on 2007-11-16
Listed method worked like a charm. Thanks a million! Now I have to figure out what I'm doing with it. :)

---

### Post by Bothered on 2007-11-17
Has anyone managed to get this to work with a non-US keyboard?

---

### Post by myle on 2007-11-17
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

I haven't install anything about graphics except Restricted Driver for ATI x700. Is it going to work for me or I have to install something more?
Do I run the risk to ruin my graphics system by doing these?

EDIT: It works fine!! Thanks.
I have a ATI Radeon X700

---

### Post by jarelkamar on 2007-11-24
Ok it seems it's working fine with everyone but me .. here's my xorg.con document : 

> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"StudioWorks"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"StudioWorks"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection


So I miss something ?? Why don't I have the 
> EndSection
Section "Extensions"
Option "Composite" "1"
EndSection

Part ??

Should i add that manually ?? I've been trying to figure that out for a month now . your Help is so so much Appreciated .

---

### Post by TekNullOG on 2007-12-04
> **johnnybgood115 said:**
> I've got an ATI mobility Radeon X300 on an IBM Thinkpad.  .. once i run through this tutorial and install xserver-xgl, I restart the xserver and my desktop environment goes black with an "X" cursor. .. any help?

I previously posted that all worked well for my Radeon X300 but the glory days ended quickly when I wanted to configure a second screen (Big Desktop). I could get both working independently but never together. Are you using 2 screens?

Basically, I gave up after 2-3 weeks and after reinstalling my machine like 6-10 times because reverting to previous configs wasn't working for me either.

Good luck to you.

---

### Post by TekNullOG on 2007-12-04
> **Phryxus said:**
> When I install xserver-xgl Gnome won't start anymore. I get the log-in screen and can enter my username and password as usual, but during the log-in procedure my screen goes back to the log-in screen.

I have a ATI Mobility Radeon X700 and fglrxinfo gives:


Thanks in advance!

Do you have 2 screen configured?

This is exactly what happened to me when I tried to fallow this How-To with Big Desktop configured.

Using only my laptop screen, it worked marvelously though. I decided my 2nd screen was more important. Maybe someone has a solution for doing both. Any volunteers?

---

### Post by jamesey on 2007-12-08
> **maxxym said:**
> I just went through the same problem...

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection
.

90% of the time this issue happens, the fix is this

---

### Post by cam_macleod on 2007-12-15
Thanks for this last instruction, it activated Compiz for me!

Full storyline for those googling to get here: I installed Gutsy on a Toshiba Satellite M50-MX2, and tried to activate the ATI restricted driver, but  I got the "the software source for xorg-driver-fglrx is not enabled" message. I enabled the source under Software Sources, and then the restricted driver activated just fine.

Next, I tried to activate Visual Effects,but got the "The composite extension is not available" message. I tried he below steps and the apt-get fixed it. Wooo!

Cam


> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

---

### Post by adwol on 2007-12-15
Hey, this got effects working on my computer but for some extremely bizarre reason, it has mucked up my keyboard settings and reversed the function of some keys, any thoughts?

---

### Post by UrBaNAcID on 2007-12-17
> **sunami900 said:**
> EXACTLY WHAT YOU DO IS GO INTO TERMINAL AND PUT THIS IN  sudo apt-get install xserver-xgl   THEN INSTALL IT IN THERE AND BOOM IT WORKS 

;)
Hey new to the forums. I followed what Max said but for some reason my system is locking up .. how do i remove the xserver-xgl or undo "sudo apt-get install xserver-xgl" . Its actually running worse now than it was before.. i am still unable to enable  Extra features.. ATI x850XT. Any pointers would be very helpful. First time running Linux Thanks

---

### Post by Igron on 2007-12-17
> **UrBaNAcID said:**
> Hey new to the forums. I followed what Max said but for some reason my system is locking up .. how do i remove the xserver-xgl or undo "sudo apt-get install xserver-xgl"
Try 'sudo apt-get remove xserver-xgl'.

---

### Post by wernicke81 on 2008-02-04
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

This also worked great for me. Thanks for the tip!

---

### Post by jaypmcwilliams on 2008-02-06
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...





JayPMcWilliams:- OK guys, I figured out the problem for a few select of us with (Compaq V2718WM laptops with ATI cards). Ubuntu screwed up the updates reset. They changed the GRUB bootloader so that it loads "KERNEL-SERVER" instead of "KERNEL-RT". all you need to do, after you follow the previous instructions, use STARTUP MANAGER to change the default & that's it. WORKS. Good Luck.   :popcorn:

---

### Post by Cyclones on 2008-02-08
Here is a link to fixing the problem. 

I had the same exact problem and after I followed the directions, my effects worked wonderfully.

[http://beans.seartipy.com/2007/10/30/finally-got-3d-desktop-effects-in-my-ubuntu-gutsy-ati-hardware/](http://beans.seartipy.com/2007/10/30/finally-got-3d-desktop-effects-in-my-ubuntu-gutsy-ati-hardware/)

Hope this helps someone.


Cheers.

---

### Post by ngreimel on 2008-02-29
Thanks maxxym! Worked great!

> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

---

### Post by guevara on 2008-02-29
I didn't fixed :(. What packages do i need must install before the do this :confused:

---

### Post by Virgilius on 2008-02-29
I installed the Xserver stuff and it worked like a charm! Nothing like desktop eye-candy :) Thank you!

---

### Post by Shnap on 2008-03-07
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...


I had the same problems that the people had above his post and I did what he said and it worked! I love you! (sorry about that, a little to happy...)

---

### Post by Jole on 2008-03-16
**This worked for me** :):):)


---------------------------------------------------
 Originally Posted by maxxym  View Post
I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace

---

### Post by tomtrauberts on 2008-03-19
I'm running a practically fresh install of Ubuntu 7.10 with an **ATI Mobility X1300** card.

Doing this:

```

sudo apt-get install xserver-xgl

```

and then logging out/logging back in worked perfectly for me.  I'm now happily enjoying the desktop effects :-)

Thanks!

---

### Post by juky on 2008-03-22
> **maxxym said:**
> I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

Those two steps above worked for me well!

Thanks!

---

### Post by ian_33 on 2008-03-26
Worked for me, on my ATI X200 graphics card (HP Laptop). It took me much longer to get my broadcom wireless driver working!

Thanks a bunch!

\\:D/

---

### Post by Kriskan on 2008-04-04
Hi ,
that worked for me..... cheers
kris

---

### Post by redtom on 2008-04-16
this also worked for me, except each time i restart my screen goes black and a black x with a white outline appears after the login screen and before the desktop appears - can this be switched off or is this actually what is needed to get all the eye candy stuff?

---

