---
title: "proprieraty/desktop effect problem"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by lolzlolz on 2007-12-31
the basic error is "Desktop effects could not be enabled!"
i have a nvidia geforce 7900gs 
it works fine with nv but nv doesn't support desktop effects
then proprietary drivers forget the resolution on restart and set it at 800x600 when using nvidia-settings it says im not using the xserver because it gets out of the xserver when this occurs
i have tried envy but that doesn't work 
it forgets resolution as well
others have used this card and no problems with some config, but what config should i use because the driver that supports desktop effects doesn't work, i have attempted to use the latest nvidia driver but once i quit the xserver with ctrl+alt+f1 and run it it says the xserver is still running, and won't continue
any help would be appreciated
thanks

---

### Post by Perfect Storm on 2007-12-31
Try with **gksudo nvidia-settings** instead nvidia-settings.

> others have used this card and no problems with some config, but what config should i use because the driver that supports desktop effects doesn't work, i have attempted to use the latest nvidia driver but once i quit the xserver with ctrl+alt+f1 and run it it says the xserver is still running, and won't continue

You need to shut it down first
```
sudo /etc/init.d/gdm stop
```

---

### Post by Ub1476 on 2007-12-31
This card works out of the box for me. Just had to open Restricted Driver Manager and check the driver for download and installing there.

---

### Post by Sef on 2007-12-31
> This card works out of the box for me. Just had to open Restricted Driver Manager and check the driver for download and installing there.

System > Administration > Restricted Drivers Manager

---

### Post by SOULRiDER on 2007-12-31
If that doesnt work youll have to install the derivers and then edit your xorg.conf.

To install the drivers type
```
sudo aptitude install nvidia-glx-new
```
Then press alt + f2 and type
```
 gksu gedit /etc/X11/xorg.conf
```
Now look for the line that says
> Driver    "nv"
and change "nv" for "nvidia" making it look like this:
> Driver    "nvidia"
After that, restart the X server with **ctrl + alt + backspace**

Post if you get stuck or something

---

### Post by lolzlolz on 2007-12-31
i did that out of the box but it didn't work first time i tried
i'll try the other stuff and tell u how it goes

---

### Post by SOULRiDER on 2007-12-31
> **lolzlolz said:**
> i did that out of the box but it didn't work first time i tried
i'll try the other stuff and tell u how it goes

Ok, ill be waiting for your response :)

Good luck!

---

### Post by lolzlolz on 2007-12-31
```
sudo /etc/init.d/gdm stop
```
didn't work for me it puts me in text but if i enter any code it doesn't work at all, it just leaves me there without doing anything it'll let me type but htere is no visible result if i type code the only way i can get out is if i hit the reset button

---

### Post by Perfect Storm on 2007-12-31
It's the way to do it. You need to shut down the interface. After you are in CLI it ask for user, thereafter enter password.

---

### Post by lolzlolz on 2007-12-31
ok it stuck me in low graphics when i logged out with
ctrl alt backspace
then when i went to login it changed to just the peach colored screen and wouldn't let me do anything, so i had to ctrl alt backspace and then restart then it stuck me in low graphics mode and made me begin using the vesa driver,
and the nvidia driver is "enabled" but isn't in use, so now wat?

---

### Post by lolzlolz on 2007-12-31
@ artificial intelligence
it doesn't ask for my username or anything though

---

### Post by Perfect Storm on 2007-12-31
ok, try this, do ctrl+alt+F1 before entering the code.

---

### Post by lolzlolz on 2007-12-31
> **Ub1476 said:**
> This card works out of the box for me. Just had to open Restricted Driver Manager and check the driver for download and installing there.
weird no fair for u? :P

---

### Post by lolzlolz on 2007-12-31
im trying it

---

### Post by lolzlolz on 2007-12-31
did that, installed the new driver and it reverted to vesa, so now what should i do?

---

### Post by lolzlolz on 2007-12-31
it also went to low graphics mode again

---

### Post by lolzlolz on 2007-12-31
it says in restricted drivers manager that the nvidia driver is enabled and in use, although it is low graphics again 
and when i used glxgears it came out like it's not using the nvidia driver
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by Perfect Storm on 2007-12-31
```
cat /etc/X11/xorg.conf
```

---

### Post by lolzlolz on 2007-12-31
should i enter that?
also i just had a slight but major problem
my friend told me to switch the port my graphics card was in so i moved it to another port with everything including the power supply turned off
then i went to go into ubuntu and it shows the ubuntu logo and the load bar loads but kicks me into text only mode with the terminal thing i start the xserver won't give me anything it will only give me the text and won't go to the login screen, u might think the problem is the graphics card port umm nope sorry
im posting this from the same computer but im in vista, i dual boot vista and ubuntu so, vista acted like it had lost the card but let me login reinstalled the driver for the card and started working again how do i get it so i can at least go into ubuntu?

---

### Post by lolzlolz on 2007-12-31
wat should i do?
bump

---

### Post by smartboyathome on 2007-12-31
Try this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup && sudo dpkg-reconfigure xserver-xorg && sudo apt-get reinstall nvidia-glx-new
```
This will backup your graphics card settings, reinstall the driver and reconfigure the graphics (and should help you).
Also, run this command that Artificial suggested and post the output here (you can also install ext2ifs on Vista if you aren't on a 64 bit processor to make it easier).

---

### Post by lolzlolz on 2007-12-31
i'll try  these
after i do ur command smartboy i'll do the cat one 
my friend also suggested
```
dpkg-reconfigure -phigh -xserver-xorg 
```
which should i do first?
urs smartboy
or my friends?
thanks

---

### Post by lolzlolz on 2007-12-31
my friend says urs first smarboy

---

### Post by doorknob60 on 2007-12-31
yeah his is pretty much the same but backs up the xorg.conf and reinstalls the driver, and also if you try mine do xserver-xorg not -xserver-xorg i made a typo :P

---

### Post by lolzlolz on 2007-12-31
ok ill do urs first smartboyathome im gonna go try it

---

### Post by lolzlolz on 2007-12-31
ill tell u how it works

---

### Post by doorknob60 on 2007-12-31
lolz told me on Google Talk that it still does what it's always been doing, he just forgot to post it on here. He really needs help, and I'm trying to help but I have no more ideas...

---

### Post by smartboyathome on 2008-01-01
Did he edit the xorg.conf again? Reconfiguring xserver-xorg resets it (which is why I made a backup of it), so he will have to set the graphics card again. Also, tell him to post the result of that cat command so we can see what his xorg.conf looks like and help him configure it.

---

### Post by lolzlolz on 2008-01-01
ok after the text mode issues smartboyathome ur command got it so i could login and right now ive got it at 1440x900 with the nv driver which doesnt support desktop effects, but this is the correct resolution so i can at least see non text mode now i will post cat results immediately after this

---

### Post by lolzlolz on 2008-01-01
```
cat /etc/X11/xorg.conf
```
when run in terminal here is the output
```
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
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7900 GS]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "VX1945wm-3"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7900 GS]"
        Monitor         "VX1945wm-3"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x1440" "1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```
what should i do now?
thanks

---

### Post by doorknob60 on 2008-01-01
And by the way, dont tell him to change the "nv" to "nvidia", trust me it doesn't work for him.

EDIT: You might want to just delete the stuff about the tablet Pc :P probly won't fix it but still

EDIT 2: Under screen I see a resolution 1440x1440...you might want to remove that...could actually fix your problems.

---

### Post by lolzlolz on 2008-01-01
my friend just noticed the 1440x1440 in the xorg.conf file which is impossible and shouldn't be there alhtough current res is 1440x900 i went and deleted the 1440x1440
also deleted the tablet pc part

---

### Post by doorknob60 on 2008-01-01
Now that your xorg.conf isn't screwed up, try restarting.

---

### Post by lolzlolz on 2008-01-01
done i got peach screen then made some changes to xorg.conf now it looks like it's at 1440x900 but still nvidia driver not working, so no desktop effects im gonna restart then post the cat of my xorg.conf file
thanks

---

### Post by lolzlolz on 2008-01-01
after the restart it stuck me in low graphics again
and when i boot it goes to text mode then the screen flashes 3 times then it gives low graphics alert then goes into login screen 
here's the cat of my latest xorg.conf that i modified
```
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
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7900 GS]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "VX1945wm-3"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7900 GS]"
        Monitor         "VX1945wm-3"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900" 
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```
now what?
 thanks

---

### Post by lolzlolz on 2008-01-01
im at 1440x900 after i set res and driver to nv in system->admin->screen and graphics
and restarted xserver (not comp) and am at right resolution but if i restart it will switch to low again i think

---

### Post by doorknob60 on 2008-01-01
Happy new year woot! And gl installing Hardy aplha 2 lolz :P

---

### Post by doorknob60 on 2008-01-01
And thats why its in alpha :P screwed up his computer but he had just installed so its fine.

---

### Post by lolzlolz on 2008-01-01
ya the graphics card is completely uncompatible with hard alpha
and i decided to try reinstalling ubuntu to see if it might work then, 
so im reinstalling but it appears the disk i burned it to isn't workign so i may have to reburn it
im going to try to get a new graphics card if this doesn't work
thanks
if u have more ideas tell me and i'll try because i'd rather not have to get a new card, currently i have to reinstall ubuntu but i should have that done in a day

---

### Post by lolzlolz on 2008-01-01
great now with a new ubuntu disk when i try to install it shows ubuntu logo and loading bar, then sticks me in text mode like command line not text mode install but the terminal thing in text mode with the user ubuntu@ubuntu 
i try to install in text mode and it says the same thing

---

### Post by smartboyathome on 2008-01-01
Ok, are you using Hardy or Gutsy now? If gutsy, it seems that there may be an error upon startup.

Also, after looking at my xorg.conf, it seems a little longer, but that may be because I have a different graphics card.

---

### Post by smartboyathome on 2008-01-01
Here is a quote from a [topic I found]("http://ubuntuforums.org/showthread.php?t=500202") while doing a google search for problems with your graphics card. I think this solves the problem with the driver you installed not working. Try it out (skip the first step where you install the driver, as you aready did that). :)

> **bdtgp said:**
> I don't have that set up but I have an ABIT board with a GeForce 7300gt.  Heres what I did:
```
sudo apt-get install nvidia-glx-new
```
Then
```
sudo nvidia-xconfig --no-composite
```
Then
```
sudo gedit /etc/usr/share/applications/NVIDIA-Settings.desktop
```
Add this to the file that pops up:
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;
```
Save that file and then exit and it should go back to your terminal.  Now just log out and hit Ctrl+Alt+BkSp to restart the X Server.  That should work.

---

### Post by lolzlolz on 2008-01-01
wait but ubuntu isn't installed right now and won't install.... 
also it seems that i may not be able to get it to work with this card as 
nVidia GeForce 7900 GS (Does not work with XGL)
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL) 
im guessing there's a work around though,
i will try to get ubuntu working and do ur thing
thanks

---

### Post by lolzlolz on 2008-01-01
when i reinstall it will start over cuz  i deleted some stuff from the xorg.conf file that's why it's shorter,
i'll tell u when i get ubuntu working again

---

### Post by lolzlolz on 2008-01-01
i will be reinstalling gutsy

---

### Post by doorknob60 on 2008-01-01
Hmm, try switching your video card back to the other slot that it originally worked with.

---

### Post by lolzlolz on 2008-01-01
ehh, ok i did that, i'll attempt installation again

---

### Post by lolzlolz on 2008-01-02
doing that allowed me to check file integrity, it said it had an error, no wonder, re dl and burning when finished installing i will tell u

---

### Post by lolzlolz on 2008-01-02
just finished reinstall ubuntu without any trouble, now i will do the commands suggested smartboyathome 
thanks

---

### Post by lolzlolz on 2008-01-02
should i restart once i enable the proprieraty driver?
because i did a fresh install it isn't enabled or installed so should i install then restart?
it seems i shouldn't because it kicks it out once i do but you never know.... :confused:
thanks

---

### Post by lolzlolz on 2008-01-02
after doing this it put me in low graphics mode once again
it appears im going to have to get a new card
which i am working on right now, im trying to trade my card with a person who uses windows :P

---

### Post by smartboyathome on 2008-01-02
> **lolzlolz said:**
> should i restart once i enable the proprieraty driver?
because i did a fresh install it isn't enabled or installed so should i install then restart?
it seems i shouldn't because it kicks it out once i do but you never know.... :confused:
thanks

Just restart the xserver (control+alt+backspace). Restarts aren't needed after every command (like in windows), most just require xserver to be restarted (if at all).

---

### Post by lolzlolz on 2008-01-02
yes i did that and it stuck me in low graphics
so i think i need another gfx card, im trying to trade

---

