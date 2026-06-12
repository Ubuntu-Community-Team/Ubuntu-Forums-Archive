---
title: "Kubuntu 7.04 hangs/stops at boot-up"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Heelix on 2007-07-02
Hi 

I have recently installed Kubuntu on my Dell Latitude X1 laptop and everything have been working well until now.

Whenever i start Kubuntu now, i see the load bar reaching the top, but then it looks like it is logging me out because i see the status bar going down to the bottom again and then the screen goes black and the only thing i see is a white blinking underscore.

I had just installed linux drivers for my printer and then i restarted the computer and all this happen. As you can see i don't know anything/very little about ubuntu and linux, as i have just moved from microsoft windows.

I understand that the given information is not much to go on, but if there is a way of removing the boot screen graphic and see the under laying error message(s), i might be able to provide some more info.

ps. i went in to recovery mode and tried to reset the xorg-server, but with out any luck

---

### Post by whizbaby on 2007-07-02
You can switch the consoles with
ctrl-alt-F_KEY

where F_KEY is one of F1,F2,F3,F4,F5,F6,F7,F8(,F9)

I think the first four and the seventh are relevant for boot (try dem all to find the error message(s) if any)

Btw what do you mean with 'installed printer drivers'?

---

### Post by Heelix on 2007-07-02
Thanks for the quick reply!

i tried all of them and sure enough i saw the console print, but there where no error messages at all.

the console ended with:
[I]
kinit: No resume image, doing normal boot...

<my computer name> Login:_[/I]

i can login as normal, but i am still in console mode.

(just mentioned that i had installed the printer drivers as this might be a cause to my current problems)

---

### Post by aquavitae on 2007-07-02
When the grub boot menu comes up, move to the ubuntu entry and press 'e' to edit the commands.  A list of about 3 line will come up.  The longest line will probably have the text 'splash' in it.  Remove the word 'splash'.  I can't remember exactly what you have to press to do this, but there's a short help message at the bottom of the screen.  Once, you've removed splash, boot by pressing 'b' (I think!)  It will boot ubuntu without the ubuntu logo so you can see exactly whats going on.  This isn't premenant so don't worry about changin it back later.  There's probably another option next splash which says 'quiet'.  I'm not certain, but I think if you remove this too it will show more info.  It certainly won't harm your system so its worth a try.

Btw, you might have to press a key at startup to get the grub boot menu if you are only running one system on your pc.

---

### Post by whizbaby on 2007-07-02
please login and type

sudo /etc/init.d/gdm restart

and post the errors of this (if any).

I was only astonished because it is really rare to have to install printer drivers by hand. Tell me what printer do you have and I can help you with the installation (mostly...).

So:
-what are the errors when you restart gdm?
-what 'printer driver' did you install?

---

### Post by Heelix on 2007-07-02
neat now i can see the console output.

my systems stops right after this output is preformed:

[I]
Starting K Display manager: kdm.
    * Running local boot scripts (/etc./rc.local)
                                                                   [OK]
[/I]

(After this output i only get the blinking underscore.)

---

### Post by Heelix on 2007-07-02
> sudo /etc/init.d/gdm restart

gives me

> sudo: /etc/init.d/gdm: command not found

I have a epson stylus d78 and it didn't work with the driver present in Kubuntu (have had it working in ubuntu using d68 drivers) so i followed this ([http://kubuntuforums.net/forums/index.php?topic=3082894.new](http://kubuntuforums.net/forums/index.php?topic=3082894.new)) recommendation and installed gimp and foomatic-db-gutenprint.
I don't know if this has anything to do with my current problem, but i haven't done any other major changes to my system just before this happened.

Thanks for taking the time helping me, very much appreciated

---

### Post by whizbaby on 2007-07-02
This is because I read too fast over the lines and didnt see the 'k' in front of ubuntu...
Try the same procedure with /etc/init.d/kdm
,lol

---

### Post by Raineer on 2007-07-02
The white blinking underscore is just X crashing as it's trying to come up.  Typically this is a display issue but it is related to other drivers as well.

Try looking at /var/log/Xorg.0.log

This can be a rather long file, but the last 20 lines or so should clue us in to something.

```
tail -20 /var/log/Xorg.0.log
```

---

### Post by Heelix on 2007-07-03
> tail -20 /var/log/Xorg.0.log

> 
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRSVFieldPosition: 0
MaxPixelClock:0
(EE) I810(0): No Video BIOS modes for chosen depth.
(II) UnloadModule: "i810"
(II) UnloadModule: "ddc"
(II) UnloadModule: "int10"
(II) UnloadModule:"vm86"
(II) Unloading /usr/lib/xorg/modules//libvm86.so
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.se
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


ok that seems to narrow it down a bit. any suggestions how to proceed from here?

----

> sudo /etc/init.d/kdm restart 

it starts and stops the K display manager (the spalsh screen flickers about), but reverts back to the console mode.

---

### Post by aquavitae on 2007-07-03
Looks like a problem with your X setup.  Can you post the contents of /etc/X11/xorg.conf.  What graphics card do you have?

---

### Post by Heelix on 2007-07-03
My xorg.config

> Section "Files"
FontPath "/usr/share/fonts/x11/misc"
FontPath "/usr/share/fonts/x11/cyrilliac"
FontPath "/usr/share/fonts/x11/100dpi/:unscaled"
FontPath "/usr/share/fonts/x11/75dpi/:unscaled"
FontPath "/usr/share/fonts/x11/Type1"
FontPath "/usr/share/fonts/x11/100dpi"
FontPath "/usr/share/fonts/x11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "int10"
Load "vbe"
load "glx"
load "GLcore"
load "v41"
EndSection

Section "InputDevice"
Idetifier "Generic Keyboard"
Driver "kbd"
option "CoreKeyboard"
option "XkbRules" "xorg"
option "XkbModel" "pc105"
option "XkbLayout" "gb"
End Section

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
option "SecondCoerEvent" "true"
option "Device" "/dev/psaux"
option "Protocol" "auto/dev"
option "SHMConfig" "on"
option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
option "Device" "/dev/input/wacom"
option "Type" "stylus"
option "ForceDevice" "ISDV4"# Tablet PC Only
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
option "Device" "/dev/input/wacom"
option "Type" "eraser"
option "ForceDevice" "ISDV4"# Tablet PC Only
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
option "Device" "/dev/input/wacom"
option "Type" "cursor"
option "ForceDevice" "ISDV4"# Tablet PC Only
EndSection

Section "Device"
identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
boardname "i810"
busid "PCI:0:2:0"
driver "i810"
screen 0
EndSection

Section "Monitor"
identifier "Generic Monitor"
vendorname "Plug 'n' Play"
modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
 depth 24
 virtual 640 480
 modes "640x480@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configure Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "erase" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection
Section "device" #
identifier "device1"
boardname "i810"
busid "PCI:0:2:0"
driver "i810"
screen 1
EndSection
Section "screen" #
identifier "screen1"
device "device1"
defaultdepth 24
monitor "monitor1"
EndSection
Section "monitor" #
identifier "monitor1"
gamma 1.0
EndSection
Section "ServerFlags"
EndSection


The graphics card is a Intel GMA 900 (Intel's 915GMS chipset) with a native resolution of WXGA = 1280 x 768 resolution.

cheers!

---

### Post by Heelix on 2007-07-03
thanks for all your help. with the info i got from you guys i managed to google some info on restoring xorg.config.

replaced the original xorg.config with xorg.config~

used the following instructions:
(taken from Ubuntuforums post by SkyNet2029 [LINK]("http://ubuntuforums.org/showthread.php?t=265529"))
> 

As for the backup copy of your xorg.conf, you might get lucky and see a file in the X11 directory named 'xorg.conf' followed by a string of numbers (time and date stamp actually) of a previous backup file.
If its there, open it up using 'nano', not 'ed' and change ONE character, then change it back (the charcter I mean). CTRL+X to save changes, and for the 'file to save as', just change the name to xorg.conf (backspace works good to remove all of those extra numbers on the end). If it's there.
Nano does save a backup file whenever you change a file with it,
It's also alot simpler to master as go its commands.

[QUOTE]
$sudo nano /etc/X11/xorg.conf[/QUOTE]

---

### Post by aquavitae on 2007-07-04
And is it working?

I think this is the problem section in xorg.conf:
> 
Section "Monitor"
identifier "Generic Monitor"
vendorname "Plug 'n' Play"
modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
gamma 1.0
EndSection

modeline shows a resolution of 640x480, but your card does something much higher.  You can fix this by generating a new modeline (google will help on how to do this), but if you've got it working by using the backup then you don't need to.

---

### Post by Heelix on 2007-07-04
It is working now! as good as  new :)

you are right it was the Monitor section that was faulty. Luckily the backup xorg.conf had previous settings that functioned correctly.

It is refreshing to be on a forum where people actually help each other.

cheers

---

### Post by GMachine_24 on 2007-08-22
Hello:

I am having the same problem - I can boot the computer as far as logging in on the nice KDE splash screen but then, instead of the KDE desktop I get the blinking cursor in the upper left hand corner of the screen.

I did this, which was suggested by whiz:

<code>

root@computer:~# sudo /etc/init.d/kdm restart

</code>

and got:

<code>
Stopping K Display Manager: kdm not running (/var/run/kdm.pid not found).
Starting K Display Manager: kdm.
root@computer:~#

</code>

I will search but if anyone knows what this means I'd be much obliged.

gm

---

### Post by aquavitae on 2007-08-23
Have you had a look at /var/log/Xorg.0.log?  Is there anything obviously wrong in /etc/X11/xorg.conf?  Did you do aything recently which could have caused this?
> [COLOR="Red"]root[/COLOR]@computer:~# sudo /etc/init.d/kdm restart

Why are you logged in as root here?

---

### Post by GMachine_24 on 2007-08-25
Hi:

Thanks for your prompt reply and my apologies for not posting sooner. I finally just reinstalled Kubuntu because something obviously had become corrupted on my install - I got more error messages, more messages about files not found, a message to force fsck which I could not do because I could not unmount hda nor could I navigate from the command line through the directory tree so I threw in the towel, reinstalled Kubuntu 7.04 and updated everything. So far, so good. Since all my data files are on other drives and backed up to yet another hard drive, there was no loss there. Just a few hours of frustration.

Thanks again.

gm

---

### Post by aquavitae on 2007-08-26
Glad you're sorted out.  

Just for future info: you're quite right, you can't run fsck on your root drive (/dev/hda) because it is mounted.  You can't unmount it because it contains the root file system which you're trying to run fsck from.  I.e. if you could unmount it, you wouldn't be able to find the fsck program to run.  The solution is to boot of a live cd and run fsck from there.

---

### Post by GMachine_24 on 2007-09-04
ok, thanks for the info. always good to learn new things :) and thanks for not treating me like an idiot.

---

### Post by fredscripts on 2007-09-05
Hi! 

I had the same problem that the computer crashed completely at boot up with Kubuntu 7.04. I don't know why, after booting a lot of times among the frustration, one time KDE boot up perfect. Since then KDE never has crashed again.

I've read this entire post and I'm very newbie and I would like to know if there's a formal HOW-TO about solving this problem (In case I has it on another computer without internet or something, or even in my own computer again), which would be very nice to print or keep on a pen drive how to manage this situation.

Thank you very much for your help!!!!

---

### Post by fredscripts on 2007-09-05
any help? :(

---

### Post by aquavitae on 2007-09-06
There is no simple answer to that.  Linux can crash on boot up for any number of reasons: hardware failure, incorrect boot up parameter, and number of incorrect entries in the config files...  Fixing it depends on understanding the error messages and log files, and learning from your mistakes.  

As you say you are a newbie, the best thing to do if something goes wrong would be to first do a bit of hunting on google and the forums to see if anyone has had a similar problem - you might be able to fix it easily without any help.  Otherwise make a post on a forum like this and get someone with more experience to help you (remember to post any error messages, logs, config files, etc which may be relevant).

---

