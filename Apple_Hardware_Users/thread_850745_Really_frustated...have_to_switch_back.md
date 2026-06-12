---
title: "Really frustated...have to switch back"
date: 2008-07-05
forum: Apple Hardware Users
---

### Post by Oscar Pradilla on 2008-07-05
Hi..i'm feeling really frustrated i have to switch back to MAC OS, because of this

Machine: Macbook Pro intel core duo 2,16 - 2gb ram - ATI x1600 256mb - 100gb hd

1. Keyboard: The F6 and F7 doesn't work right (in fact, they doesn't work at all)
2. Batter power: with ubuntu 8.04 (gnome) the battery time was 2.50min an hour less than in MAC os 3:50 - 4:15min
3. When i connect the video output for a external monitor or (and most important) a video beam, nothing happend, there's no way to get video (This was the worst of all, i really need this working because i do a lot of seminars, conference and things like that)

if anyone has solved this issues please help me....

Thanks
O.P.

---

### Post by russo.mic on 2008-07-06
The video output on my mbp works great.  You have to remember that apple hardware is created to be very properitary.  If you want to point a finger, blame steve jobs.

anyway, install the package pommed.  from a terminal type "sudo apt-get install pommed".  That should help with the F keys.

Have you tried booting with the 2nd monitor connector plugged in?  worked for me out of the box. Make sure you install the restricted driver from the driver manager under system ---> administration.

Russo

---

### Post by Oscar Pradilla on 2008-07-06
yes i've done that but after pommed the F6 and F7 doesn't work also, i've even change the keyboard in the preference panel to Apple - Macbook pro (int)but then a sort of mistake appeared, with the XB something config....(it's a post on that already before) but nothing happend, i've boot with second monitor, the ubuntu logo is fine, then when is going to change to the login window, the signal goes off.    I've also installed the ATI-linux drivers but was worst....

any other idea? thanks

---

### Post by _alex_ on 2008-07-06
Does Fn+F6 / Fn+F7 work as F6/F7?

---

### Post by russo.mic on 2008-07-06
well,  what do you mean it was worst?  eleborate.  The aticonfig utility isn't hard to use.  You might have to make some changes to xorg.conf.  

Why don't you start by telling us all what is wrong when you enable the ati driver?  it sounds like your 2nd output is just fine, you just have to tell it what you want it to do.  Also, is your native resloution set?  i.e., does everything look why to big?  or blurry?  

in reguards to the F keys, what are you trying to do with them?  for example, my F6 is numlock, and although the light doesn't work, the function does.  Are you trying to assign them to a function in linux?  It could be such that whatever icon is painted on the key isn't a function the ubuntu supports.  

Russo

---

### Post by pveith on 2008-07-06
with the open-source driver you should be able to use the xrandr Xorg extension. Try the follwing command (it would be best with a connected 2nd Monitor) and post the output.
```
xrandr -q
```

It outputs a list of connected and connectable devices. The Code ```
 xrandr --output <devicename 2> --below <flatpanel devicename> --auto
```

Unfortunally i don't have a macbook pro, so i can't test it here. The above line works on a macbook with the following device names.
flatpanel devicename: LVDS
devicename 2: VGA (i have the VGA-adapter not the DVI one)

There is a GUI version for xrandr, but that allways fails on my macbook. So i skripted the dual-monitor part. 
Another thing is that there is a Standard "virtual desktopsize" setting which restricts the expanded desktop to a 2048x2048 size. That is why is choose below instead of right or left.

---

### Post by pveith on 2008-07-06
For the non-functioning F6 anf F7 key try the following:
```
xev
```
It  will open a small window and output al lot on the console. Give the programm the fokus and press F6 and F7. There should be output for both keys.
It should look like this: 
```
KeyRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x5a, subw 0x0, time 4101439, (38,95), root:(43,580),
    state 0x0, **keycode 72 (keysym 0xffc3, F6)**, same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x2a00001,
    root 0x5a, subw 0x0, time 4101863, (38,95), root:(43,580),
    state 0x0, **keycode 73 (keysym 0xffc4, F7)**, same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
Important ist the keycode part. Mousemovement is also monitored so be sure to not move it to see, which code belongs to the key. And post the output here. If it apears here, it should be easy to bind the output to something sensible...

---

### Post by Oscar Pradilla on 2008-07-06
i'm gonna try this, the F6 and F7 doesn't work at all after pommed, when i use the ATI driver that ubuntu suggest everything is fine (Res 1680*1050) and when i connect the second display if ubuntu is already running there's no way to get a signal the Detect display in the Screen Resolution app don't do it.  If i start the laptop with the second display attached the ubuntu logo (when it starts) is ok, but when it is going to enter to gnome interface the signal goes off and can't get it back.

I'm going to make this changes i'll reply the results.

Thanks

---

### Post by pveith on 2008-07-07
You really should add hardware information to your post. So it would be helpfull to provide the output off the above commands. The given command itself will probably not help directly, but hint where the problem might be. (xrandr could possibly solve the problem, but xev just outputs keyboard-events in a human readable way. So actions have to be taken afterwards to activate the keys. Possibly via the xmodmap command.)

It might also be a good idea to post you xorg-log-file (/var/log/Xorg.0.log), so someone in the forum might see, what happens on your laptop at xorg start.

For best Effect: Just connect a secondary Monitor, boot your laptop and post your /var/log/Xorg.0.log file here. The file is written automatically, so it is always up to date. Just to be sure have a look at the creation date of this file. (If you reboot before posting the file, it will overwritten. So at least copy it using the console, if the connected second display crashes X.)

An afterthought so: I have a desktop with a working secondary screen using an ati-graphic-adapter. An option for the device in my self-generated xorg.conf-file did the trick for me:

```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        **Option      "DesktopSetup" "horizontal"**
EndSection

```

---

### Post by BLTicklemonster on 2008-07-07
Congrats guys. I finally found a post where someone says they are leaving, and no one has said anything useless.

:guitar:

Good luck getting Ubuntu set up to run the way you want, Oscar!

---

### Post by pveith on 2008-07-07
> **BLTicklemonster said:**
> Congrats guys. I finally found a post where someone says they are leaving, and no one has said anything useless.

:guitar:

Good luck getting Ubuntu set up to run the way you want, Oscar!
Oh no! You just broke the record... :) (No pun intended here. Just a little bit of off-topic fun.)

---

### Post by BLTicklemonster on 2008-07-07
(that was going through my mind but I posted anyway.)

---

### Post by Oscar Pradilla on 2008-07-07
**well i've run te xve this is it...**

KeyPress event, serial 31, synthetic NO, window 0x6e00001,
    root 0x87, subw 0x0, time 381485, (-228,286), root:(446,337),
    state 0x0, keycode 73 (keysym 0xffc4, F7), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x6e00001,
    root 0x87, subw 0x0, time 381565, (-228,286), root:(446,337),
    state 0x0, keycode 73 (keysym 0xffc4, F7), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

But still the F5 - F6 doesn't work.

**When i change the keyboard layout to macbook pro int this appear**

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Thanks a lot...i don't want to switch back....

---

### Post by Oscar Pradilla on 2008-07-07
This is my Xorg file
# xorg.conf (X.Org X Window System server configuration file)
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
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"alt-intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Oscar Pradilla on 2008-07-11
Well i found this solution for activating Keypad it was very good also activates the green leds of the keyboard, just enter

System>Administration>Synaptics Package Manager 

then search for mouseemu and remove it, Apply

That's all....works fine

Now i still have the problem with the video output for an external monitor, i've downloaded and installed the ATI driver from (ati.com) nothing happend...  need help on this...

Video cardo: Ati radeon x1600

---

### Post by BLTicklemonster on 2008-07-11
> **Oscar Pradilla said:**
> Well i found this solution for activating Keypad it was very good also activates the green leds of the keyboard, just enter

System>Administration>Synaptics Package Manager 

then search for mouseemu and remove it, Apply

That's all....works fine

Now i still have the problem with the video output for an external monitor, i've downloaded and installed the ATI driver from (ati.com) nothing happend...  need help on this...

Video cardo: Ati radeon x1600

Good God, Good Luck with the ATI. I sat for hours last night trying to get some drivers better than just plain fglrx. Problem is, the ati card I put in the machine (working on a friend's computer) is one I have been trying to get rid of for a while now! I ended up putting my good stand by eVGA Nvidia card in and getting the new Nvidia drivers running on it.

I hate ATI with Ubuntu, so help me Zog.

---

### Post by cyberdork33 on 2008-07-11
> **Oscar Pradilla said:**
> Now i still have the problem with the video output for an external monitor, i've downloaded and installed the ATI driver from (ati.com) nothing happend...  need help on this...

Video cardo: Ati radeon x1600
you should use the drivers in the repos instead of directly downloading from ATI unless there is some specific feature change that you need.

You can also try [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install your video drivers.

---

### Post by Oscar Pradilla on 2008-07-11
Well i'm really happy, finally i made it, got video output, so i'm formating my macbook today...ubuntu native.....

i will post how i did it...so easy....

Thanks a lot...all

---

### Post by Drk Guy on 2008-07-11
Ubuntu power, mac's are mostly top-secret, but linux can pwn them ;)

---

### Post by Oscar Pradilla on 2008-07-12
[IMG]http://www.neurologiahospitalsanjose.com/images/11-07-08_1336.jpg[/IMG]

It's really easy:

1. Install ATI propietary drivers recomended by ubuntu (Then restart)
2. FileSystem>usr>share>applications>
3. Open Screen and Graphics app
4. Select Screen 1 as default
5. On screen 2 select: Type of monitor (Normal video beam 1024X768) and type of output (Mirror default screen)
6. Test
7. If works, then OK (It's gonna change your screen resolution - so only use it when you are plugged to an external monitor)
8. To make it a little bit easier, make a launcher at desktop like this:
   Type: Application  / Name: Screen and Graphics / Command: gksu displayconfig-gtk 
9. Enjoy...

---

