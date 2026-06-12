---
title: "Impossible to boot after install on an iMac  G3"
date: 2009-02-03
forum: Apple Hardware Users
---

### Post by JujuLand on 2009-02-03
After having solved the cd bug to install, the install works fine till the end when it's ask to reboot.

But, after, no boot, just a folder icon (with question mark)

I had also had this problem with 7.10 alternate.

I install on a blank disk without OSX (and I don't want it).

Can somebody have already this problem, and is there a solution to boot Ubuntu on the iMac.

Here is the thread I had opened, and on which no more answer where posted.

[http://ubuntuforums.org/showthread.php?t=1046058&page=2](http://ubuntuforums.org/showthread.php?t=1046058&page=2)

A+

---

### Post by pxwpxw on 2009-02-03
Try this - to show if the boot-device has been set by the installer

restart into openfirmware by holding down 4 keys Command Option o F during the chimes
then from the open firmware prompt

```

0> printenv boot-device

here note down what it says
then

0> reset-all

```
post that result.

---

### Post by JujuLand on 2009-02-03
I have boot on openfirmware with Alt+Apple+O+F (if I remember), and I have the text saying 

Type mac-boot ... or shut-down ...

It seems obvious that the boot hasn't been installed...

How to correct it ?

A+

---

### Post by pxwpxw on 2009-02-03
> **JujuLand said:**
> Hum, I'm a newbee with mac, and I don't know how to use Command key and Options key.

I have Ctrl, Alt and Apple (left and right)  keys, but no options and command keys.

On an another post, I think I saw that Options key is Alt key. Am-I right ?

I have tried Ctrl-Alt-O-F, and no result.

Do I try it before, or during the sound which comes ?

A+
ok
Apple=Command
Alt=Option
So you want Command Alt O F

---

### Post by JujuLand on 2009-02-03
Sorry, I have modified the previous post, thinking there were no answer.

Look at it

A+

---

### Post by pxwpxw on 2009-02-03
> **JujuLand said:**
> Sorry, I have modified the previous post, thinking there were no answer.

Look at it

A+
Hold the keys down from before the chime, until you see the open firmware message.

---

### Post by JujuLand on 2009-02-03
Yes, it's now ok, and I have this text:

Type mac-boot ... or shut-down ...

It seems obvious that the boot hasn't been installed...

I have send reset-all, and at boot, I have had very quickly a message 'config .....', and after, the cd has booted.

And here also, how to eject the CD, a moment, when booting, it was ejected, now, no more eject, and the cd is booted.

I loose the less latin I know ..

A+

---

### Post by pxwpxw on 2009-02-03
I hope your Open Firmware has English language. Tell me if I am wrong.

Try again starting up Openfirmware. This time wait to see the prompt.
```

0>

```

then you can eject the CD by typing 
```

0> eject cd

```

Then type
```

0> printenv boot-device

```
Please write down the boot-device and post here.

---

### Post by JujuLand on 2009-02-03
ok for the ejection, but I presume that we can eject a cd with a simpliest way without having to launch openfirmware; no ?

For the main problem, I had forgotten to launch the command, and thought it was displayed automatically.

Now, here is the return of the command:

/pci@f2000000/mac-io@17/ata-4@1f00/disk@0:1,\\tbxi hd,\\:tbxi

A+

---

### Post by tiresia on 2009-02-03
> **JujuLand said:**
> Yes, it's now ok, and I have this text:

Type mac-boot ... or shut-down ...

It seems obvious that the boot hasn't been installed...

I have send reset-all, and at boot, I have had very quickly a message 'config .....', and after, the cd has booted.

You misunderstood what is going on there.
'Open Firmware' is a bit like BIOS on PC (but it's more powerful and works differently). Yaboot is the Kernel Bootloader for PPC machine with Open Firmware. A Linux System on PPC works like this when you start the computer:
Open Firmware > Yaboot > System  

When you press at boot the Ctrl-Opt-O-F keys, you get that message you have seen, and a prompt. You should type there, what pxwpxw told you```
printenv boot-device
```
(Even if I believe, that having you reset all, you loose the old configuration)

Anyway, there are may be two reasons, why your iMac can't boot:
1. The bootloader (Yaboot) was not installed
2. The bootloader was installed but the Open Firmware was not correctly configured to find the bootloader (and this is what you can check running printenv)

(But the last point is also strange to me: even if Open Firmware doesn't find, where it has to boot from, it should be able to just boot the first bootable system)

.................
Please, at the OF prompt try following:
```
boot hd:2,yaboot
```


OpenFirmware works with a QWERTY US Keyboard. To type '@' you need to hit the shift-2 keys. 
have a look here to find the different keys
[http://en.wikipedia.org/wiki/File:Qwerty.svg](http://en.wikipedia.org/wiki/File:Qwerty.svg)

---

### Post by JujuLand on 2009-02-03
Thanks, 

I have some troubles to find how to enter @.

I think I have a french keyboard (hard) and I have en-US keyboard (soft)

How can I do it ?

A+

---

### Post by tiresia on 2009-02-03
Sorry, I made a mistake. Please, see in my last post the suggest command to start yaboot

---

### Post by tiresia on 2009-02-03
> **JujuLand said:**
> Thanks, 

I have some troubles to find how to enter @.

I think I have a french keyboard (hard) and I have en-US keyboard (soft)

How can I do it ?

A+

Just use your french keyboard. As i told you, you need to find the ':' key. 
On the french keyboard is : 'shift ù' (like %)
Check wikipedia at the link a gave you

---

### Post by JujuLand on 2009-02-03
I suppose that your talking about this syntax:

boot hd:2,yaboot

the return of the command is :

can't open hd:2,yaboot

A+

---

### Post by tiresia on 2009-02-03
How did you install Ubuntu? Did you just follow the normal installation process, using the alternate cd?
Did you got any message during the installation?

A last question: how much ram do you have, and how big is your hd?

---

### Post by JujuLand on 2009-02-03
Yes, I have installed as said with alternate CD, I have just launched the modprobe command to allow the installer to see the cd.

No error message.

I must say that I have had the same problem with 7.10 (except, no moprobe command need), but no boot after that.

512 Mo, and 20 Go HD

When I have installed, I have create these parts:

NewWorld 8 Mo
/              7,5 Go
swap        1 Go
/home     11,5 Go 

something like that for the sizes.

A+

---

### Post by JujuLand on 2009-02-03
What's up doc ?

Have I setup correctly ?

It seems that yaboot isn't installed ? Right ?

I have tried two different install, install and another where a full details are asked for. In the last one, I saw it says it install the loader (yaboot, if I'm right)

I have tried something else:

Boot on the cd and try to launch the disk image with this syntax:

/pci@2000000/mac-io@17/ata-4@1f00/disk@0:1

I have this return:

/pci@2000000/mac-io@17/ata-4@1f00/disk@0:1, /vmlinux unable to open file, invalid device

Is my command possible from the cd ?
Have I miss something in the command ?
In the command line, I haven't given the name of the image. 
It's perhaps not this name, and the path is probable more complex ?

I'm really tired of this machine ...

No one has idea ???

I think that if I can boot onr time, I will be able to modify the system to be able to automatically boot after, or to acces to a good config of yaboot to launch ubuntu. But for now, I'm lost ...

A+

---

### Post by tiresia on 2009-02-03
Sorry, I was away for a while. Please, be patient, I can undestand, that installing Linux on a PPC can be sometimes frustating, but I'm sure, you will do it.

I do believe that your partitions are not correct.
Tell me if I'm wrong. Did you make the partitions yourself and how?
Usually Linux on a Mac looks like this

```
#                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap bootstrap               1600 @ 64        (800.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 myLinux               85852160 @ 1664      ( 40.9G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                 8000820 @ 202238668 (  3.8G)  Linux swap
```

And it is important, that you respect the size of the first two partitions (and therefore to let the installer to do it for you, if you are experienced)

---

### Post by JujuLand on 2009-02-03
Well, it seems logical, in this case that this doesn't boot.

I have create it manually, and I haven't the first part:

Apple_partition_map

How to create it ?

A+

---

### Post by tiresia on 2009-02-03
Reinstall Ubuntu with the alternate CD. Are you trying to install Intrepid?
At a certain point, the partitioner will ask you how you want to partition your HD.
Choose the option 'using the whole HD with separate /home' (or something like this - I don't remember the exact form). After that, the installer will show you what it is going to do. There you can resize the partitions /root and /home according to your needs. But don't touch the first two! Let me know, how it works.

---

### Post by JujuLand on 2009-02-03
Yes, Intrepid

ok, thanks, I will try tomorrow

Curiously, I haven't notice this choice, but it's probably to the fact that for 386, the default part don't offer a choice to have home seperate, and I don't look for the menu and directly choose 'Manual'

It's sometimes important to take the time to read ;)

A+

---

### Post by JujuLand on 2009-02-04
I have now, with your help, solved my problem.

I have choosen automatic partitionning, and before making the partionning, choose to return back and modify the parts manually.

Thank for all the help I have found on the two threads I opened.

Hoping this can help others guys.

I have now the black (blank) screen problem.

As refering to the Known Issues page, I boot on alternate cd, and launch 'rescue' image, to make the modifications wanted, but unfortunately, it doesn't work.

I thought that this image gives me a console, or a menu to choose the part used, and allows me to modify the files, but it starts exactly like for install.

So, I tried to open a new session , but here, impossible to go to the HD part to access /etc....

Am-I wrong, or is there a difference between 8.04 (the referenced version of the Known Issues page) and 8.10 ?

Thanks

A+

---

### Post by tiresia on 2009-02-04
You don't need any Installer CD anymore

To get a working X, type at the yaboot prompt (when you boot the installed system)```
video=ofnoly nosplash
```

To get to a console: ctrl-alt-F1 (or F2, F3...)
Ctr-alt-F7 to get to X again

Now you need to edit your file /etc/X11/xorg.conf to make your video working
First of all, backup it (and backup it again, everytime you get a good solution)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
(just choose a name you like to backup it)
You can alway resume it again, if you made an error, typing again
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

To configure /etc/X11
Have a look on this thread. You should find the info you need, and even more. It refers to 8.04, but it should work also for Intrepid
[http://ubuntuforums.org/showthread.php?t=1058232](http://ubuntuforums.org/showthread.php?t=1058232)

---

### Post by JujuLand on 2009-02-04
Ok, it's as for i386 install, no real problem.

But, is-it necessary to make the commands like said for 8.04 (ide-scsi, ...) or has-it been updated during install ?

A+

---

### Post by tiresia on 2009-02-04
> **JujuLand said:**
> But, is-it necessary to make the commands like said for 8.04 (ide-scsi, ...) or has-it been updated during install ?

A+
I don't understand your question. You said, that you installed the system and that you can boot it right?
In such a case, you don't need to add any module to the kernel (if you are talking about this). 
This command (modprobe ide-scsi) is used during the installation of Intrepid, just to tell to the kernel to add this module (because of a bug of the installer, the kernel has not such a module, and can't detect the ide CD-ROM). After that you don't need it anymore (and infact you can start the system and access the CD-ROM)

---

### Post by JujuLand on 2009-02-04
I've busy for a long time, now I'm here again for a few minutes.

I have updated yaboot.conf, and no more black screen, I see the complete boot, till X server launching.

Here is the parms added in yaboot.conf: nosplash nofb video=ofonly

It fails when launching X server, and xorg.conf was empty.

If I use to launch with low config, it displays the desktop, but, and I think it's another problem, I'm not able to launch something, the console, the text editor, nothing opens.

But first, I want the server to launch correctly. I have burn a cd with the model given on the spage you give me, and I've been able to replace the xorg.conf by copying, not editing, 
but this version fails too at the end of the log:

(ww) open /dev/fb1 : no such file or directory
(ww) open /dev/fb2 : no such file or directory
(ww) open /dev/fb3 : no such file or directory
(ww) open /dev/fb4 : no such file or directory
(ww) open /dev/fb5 : no such file or directory
(ww) open /dev/fb6 : no such file or directory
(ww) open /dev/fb7 : no such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0) : failed to open framebuffer device, consult warning and/or errors above for possible reasons (you may have to look at the server log to see warnings)
(II) UnloadModule : "r128"
(II) UnloadModule : "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have usable configuration

Fatal error:
no screens found

I'm not sure having an ATI Rage 128.
How to be sure ??

A+

---

### Post by twodogsdad on 2009-02-04
Hello, Thanks for all the work you two are doing on this issue. I've been installing Xubuntu Ibex (on a 333 MHz, 256 MB ram, 20 GB HD, imac G3, tray loader) and have had all of the same issues and just got to the problem where I can't run Terminal, Package manager, programs like that. 

I typed "lspci" at the command prompt and the response was a different ATI Rage card than the 128. I put the result from lspci into my xorg.conf and I'm not sure it worked (have to go back home and keep playing) but that is how I found what my computer thinks the video card is.

Cheers

---

### Post by JujuLand on 2009-02-05
Thanks for the info, I have launch lspci, and it gives me the chipset I use:

ATI Rage 128 PR/PRO AGP 4X TMDS

So, I have probably some parameters in it to change, or else another problem I'm not able to find.

I think that the other problem I have is perhaps due to memory. If I remember, it was at the beginning one 64 Mo SDRAM 100 Mhz, and I have replaced it with two 256 Mo SDRAM 133 Mhz. curiously, it doesn't seems to hangup the system, but perhaps  just hang the programs when using more memory. I'll try to invert the two ram, to see if it crashes before (when loading the system).

A+

---

### Post by tiresia on 2009-02-05
Can you please post your xorg.conf?

---

### Post by JujuLand on 2009-02-05
I have token the [[xorg.conf]]("http://ubuntuforums.org/attachment.php?attachmentid=101931&d=1233610536") given on the [[thread]]("http://ubuntuforums.org/showthread.php?t=1058232") you gave me, and have modified it after reading some post of that [[thread]]("http://ubuntuforums.org/showthread.php?t=770033&highlight=ati+rage"). (Horiz values, and DRI disabled).

I have also tried to create /dev/fb1  to fb7, but after a reboot, this special files were gone, and the xorg error messages were the same.

I haven't yet tried the xorg.conf found at the beginning on the [[thread]]("http://ubuntuforums.org/showthread.php?t=770033&highlight=ati+rage"). I'll try it.

A+

---

### Post by JujuLand on 2009-02-05
I have started X in low display mode (X error box)
I have tried the xorg.conf found at the beginning on the [[thread]]("http://ubuntuforums.org/showthread.php?t=770033&highlight=ati+rage").
I have modified it from within a console :

pci:0:16:0
Horiz and Vert values

Ctrl-Alt-F7 to return to X desktop
Ctrl-Alt-Backspace to restart X >> X works

Restart of Linux >> doesn't work anymore same errors as before (framebuffer) ???

Launching in low display mode, and the same as above, it works ...

I really don't understand ... and I have also the problem with launching programs. Menus works, but all the programs launched disappeared quickly from the screen (I can't see anything for o few). 

For example, when I try to update the system (about 230 paquets to update), it opens a bow and load the list, display the list, and when I want to launch update, quickly disappear.

A+

---

### Post by tiresia on 2009-02-05
> **JujuLand said:**
> 
For example, when I try to update the system (about 230 paquets to update), it opens a bow and load the list, display the list, and when I want to launch update, quickly disappear.

A+
Update the system from a console (ctrl-alt-F1), just using apt-get (or aptitude)```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by JujuLand on 2009-02-05
ok for updating, I'm making it, but have you an idea about X problems ?

A+

---

### Post by tiresia on 2009-02-05
> **JujuLand said:**
> ok for updating, I'm making it, but have you an idea about X problems ?

A+
Well, Intrepid is quite different than the other versions, because X tries to detect any device - therefore you don't see in the first installed version any values. Neverthless, you can edit it, just as before.
But I can't help you, if you don't post it ;)
I don't have an imac, but I can have look on it

---

### Post by JujuLand on 2009-02-05
Here is the last one I use :

```
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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
BusID [COLOR=Red]"PCI:0:16:0"[/COLOR] #"PCI:0:18:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Horizsync [COLOR=Red]58-62[/COLOR] #35-65
Vertrefresh [COLOR=Red]75-117[/COLOR] #50-75
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"

Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "Module"
Disable "glx"
Disable "dri"
EndSection

```It works when I launch from within Desktop (Ctrl-Alt-BackSpace] in low display mode, but break from boot

A+

---

### Post by JujuLand on 2009-02-05
Here is the first one I used, coming from the thread you gave me.

```
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

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    FontPath    "/usr/share/fonts/X11/misc"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#    Load    "ic2"
    Load    "bitmap"
#    Load    "ddc"
[COLOR=Red]#    Load    "dri"
    Disable  "dri"
[/COLOR]     Load    "extmod"
    Load    "freetype"
[COLOR=Red] #    Load    "glx"[/COLOR]
[COLOR=Red]    Disable  "glx"
[/COLOR]    Load    "int10"
#    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ExplorerPS/2"
    Option        "ZaxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Rage 128 RL/VR AGP"
    Driver        "ati"
    Option        "UseFBDev"  "true"
EndSection

Section "Monitor"
    Identifier    "iMac"
    Option        "DPMS"
    HorizSync    [COLOR=Red]52-65[/COLOR] #60-60
    VertRefresh    75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Rage 128 RL/VR AGP"
    Monitor        "iMac"
    DefaultDepth    [COLOR=Red]16[/COLOR] #24
    SubSection "Display"
        Depth    1
        Modes    [COLOR=Red]"1024x768" [/COLOR]"800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    4
        Modes    [COLOR=Red]"1024x768" [/COLOR]"800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    8
        Modes    [COLOR=Red]"1024x768" [/COLOR]"800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    15
        Modes    [COLOR=Red]"1024x768" [/COLOR]"800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes    [COLOR=Red]"1024x768" [/COLOR]"800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    24
        Modes    [COLOR=Red]"1024x768" [/COLOR]"800x600" "640x480"        
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
EndSection

[COLOR=Red]# Section "DRI"
#    Mode    0666
# EndSection
[/COLOR]
```It works when I launch from within Desktop (Ctrl-Alt-BackSpace] in low display mode, but break from boot

If I change       Option        "UseFBDev"  "true" by "false,
I have the following error:
Your screen, graphic card and input device can't be detected correctly ...

If I just comment it, its like "true"

If I just comment Load "dri" and Load "glx", it loads it.
If I replace it by Disable, I have the errors :

(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
  ...and yet a little bit later, I get these:
(II) "glx" will be loaded even though the default is to disable it.
(II) "dri" will be loaded even though the default is to disable it.


A+

---

### Post by tiresia on 2009-02-05
Ok, this can be a quite frustrating thing, and therefore you must test each single value (not all together), to understand, where the problems come from (zen-attitude...)

The Sections, that interest you,  are three: Device, Monitor and Screen

Check the name of your grafic card
```
lspci | grep AGP
```

It should be 'PF' not 'PR' as you wrote before
ATI Rage 128 P**F**/PRO AGP 4X TMDS


1. Try adding it to the section Device 
```
Section "Device"
    Identifier    "ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
    Driver        "ati"
    Option        "UseFBDev"    "false" # "true"
EndSection

```

2. Did you change the BusID after the value that 'lspci' turned out?
Sometimes they differ, and you should also try leaving the original value.

3. Try other solution for Horizsync and Vertrefresh (look for it in Google).  

4. Try with Default depth at '16'
 
Here is another example of xorg for your grafic card. But it is on a g4 and has an external monitor
[https://www.linuxquestions.org/questions/debian-26/trying-to-get-screen-resolution-over-640x480-ppc-etch-476700/](https://www.linuxquestions.org/questions/debian-26/trying-to-get-screen-resolution-over-640x480-ppc-etch-476700/)

Can you please, tell me the model of your g3. You could show me in [www.everymac.com](www.everymac.com)

---

### Post by JujuLand on 2009-02-05
> It should be 'PF' not 'PR' as you wrote before
ATI Rage 128 P**F**/PRO AGP 4X TMDSUnfortunately, it's PR/PRO, and I don't see this model in the logs :(

**[COLOR=Red]1)[/COLOR]** I tried to replace the name by the real  string I found and with the one you give:

- with UseFBDev "false"

I have the following error:
```
Your screen, graphic card and input device can't be detected correctly ...
```If I just comment it, its like "true"

```
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
  ...and yet a little bit later, I get these:
(II) "glx" will be loaded even though the default is to disable it.
(II) "dri" will be loaded even though the default is to disable it.
```and then 

```
 (WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
        (you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```**[COLOR=Red]2) [/COLOR]**[COLOR=Red][COLOR=Black]Yes[/COLOR][/COLOR]

**[COLOR=Red]4) [/COLOR]**[COLOR=Black]It's already what I used

My G3 is a [M5521]("http://www.dealtime.com/xPO-Apple-APPLE-IMAC-G3POWERPC-G3400-400-128-10-DVD-SND-NC-MAC-OS-9-2-BLEU-Apple") (year 2000) , but the display card seems not to be what lspci gives me.

[/COLOR]**[COLOR=Red]3) [/COLOR]**[COLOR=Black]I'l try to find something on google, but I don't know exactly what to search

A+

[/COLOR][COLOR=Black]
[/COLOR]

---

### Post by tiresia on 2009-02-05
I'm sorry, but I don't have an imac here, and it's difficult to check every value for xorg. Maybe the easiest solution would be to install a bit older version of ubuntu, or even better debian, just to see how the xorg looks there. 
I would try with debian etch, with a netinst. You will need less than a hour (download, burn and install).
[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)
After that, it is possible that you still need to edit your xorg - but at least you will have a base to start from. When you will reach a definitive version, you can back up it at go back to ubuntu, if you like. 
If you do it, post your xorg here - I'm curious to see it. 
---
I will send you any useful info I can gather

---

### Post by tiresia on 2009-02-05
This looks interesting
[http://ubuntuforums.org/showthread.php?t=984263&highlight=imac](http://ubuntuforums.org/showthread.php?t=984263&highlight=imac)

---

### Post by JujuLand on 2009-02-06
Hi, good news ...

I have search for my exact graphic card on google and I have found a thread on french ubuntu forums, where I keep some idea.

I have add two options to Device section:

Option "noINT10" "true"
Option "noDRI"    "true"
and set
Option "useFBdev" "false"

and set
driver "r128" # instead of ati

and it works, but it seems I'm not in 1024x768, and I'm trying to change some parameters , to set the needed definition, and also to to know what exactly has make is to work.

I'm trying to chang glx, dri, useFBdev

My first try has been to try to use DRI and glx. It seems the definitionn was good, but it  eats probably a lot of memory, and X was very very very long to load.

I continue the tests and will report the better xorg.conf I will have done.

A+

---

### Post by JujuLand on 2009-02-06
Some test results:

a) no DRI + no glx = no 1024x768 definition

b) DRI + glx = too much long, but seems to accept 1024x768 definition.

c) DRI + no glx = a little quicker then first test, but no more 1024x768 definition

d) DRI + useFBdev + fb1 to fb7 creation = error (so I think we must disable useFBdev)

The fb1 to fb7 devs created are deleted.
Could it be due to the option used when launching Linux image (in yaboot.conf) : nofb ??

e) glx + no DRI = like c)

f) load INT10 = error (so I think we must disable INT10)

h) idem with d), but modifying yaboot.conf (deleting nofb) + ybin command. I have remove nofb

It doesn't work better. But I have a problem now: having forgotten to restore yaboot.conf, and having set UseFBdev to false, I have loose the console sessions. I don't know if there is a link with that, but I havent anymore other consoles.

To modify yaboot, I have used the solution to choose xterm on load screen, and modify yaboot.conf and launch ybin.

But now, always no more consoles (Ctrl-Alt 1 to 5) ???  merde ... :cry:

No more idea for the moment, but I ought to use a console command (when I make it work again) to know the xserver definition used, as I can't launch a command in graphical mode.

A+

---

### Post by JujuLand on 2009-02-06
Here is the version which works:

```
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

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    FontPath    "/usr/share/fonts/X11/misc"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#    Load    "ic2"
    Load    "bitmap"
#    Load    "ddc"
[COLOR=Red]#    Load    "dri"
    Disable    "dri"[/COLOR]
    Load    "extmod"
    Load    "freetype"
[COLOR=Red]#    Load    "glx"
    Disable    "glx"
#    Load    "int10"
    Disable    "int10"[/COLOR]
#    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ExplorerPS/2"
    Option        "ZaxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"
EndSection

Section "Device"
[COLOR=Red]    Identifier    "ATI Technologies, Inc. Rage 128 PR/PRO AGP 4X TMDS"[/COLOR]
    Driver        "ati"
[COLOR=Red]    Option        "noINT10"    "true"
    [COLOR=Black]Option        "UseFBDev" [/COLOR]   "false"
    Option        "noDRI"        "true"
    Option        "noglx"        "true" # added, but no sure it's needed[/COLOR]
EndSection

Section "Monitor"
    Identifier    "iMac"
    Option        "DPMS"
[COLOR=Red]    HorizSync    52-65
    VertRefresh    43-117[/COLOR]
EndSection

Section "Screen"
    Identifier    "Default Screen"
[COLOR=Red]    Device        "ATI Technologies, Inc. Rage 128 PR/PRO AGP 4X TMDS"[/COLOR]
    Monitor        "iMac"
[COLOR=Red]    DefaultDepth    16[/COLOR]
    SubSection "Display"
[COLOR=Red]        Modes    "1024x768" "800x600" "640x480"[/COLOR]
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
EndSection

#Section "DRI"
#    Mode    0666
#EndSection

```A+

---

### Post by tiresia on 2009-02-06
Great! You did a really good job!

Just few remarks: are you sure, that you need to add - Disable  "glx"-?
It is not enough to comment it out with '#'?

Having 'DefaultDepth 16' makes X for sure faster, but does it work also with 24? 
(I'm just asking, because i saw in other xorg that other people were using 24 with your grafic card - well, not on an imac)

Of course, don't forget to back up this file...

---

### Post by JujuLand on 2009-02-06
I think that Disable is needed, else glx is loaded even if not implicity loaded in xorg.conf. But I'm not sure for the noglx, I have added it, as i must add it for DRI.

I'll try to enable 24 bits.

But for now, the problem I have with the impossibility to open console. Very ennoying ...

If you have an idea ...

I'm also searching the reason why I can't launch a program in grafic window

I have invert the memory modules > the same
I have replaced these modules 256/133 with 64/100, same problem

I think that I'll make a new clean install (with what I have made now) it ought not to be too much difficult.

A+

---

### Post by tiresia on 2009-02-06
I have no idea, why you don't any console now.
For fbdev you can have a look here 
[http://www.linux-fbdev.org/](http://www.linux-fbdev.org/)
But the section about ppc is empty...

If you want to reinstall, I would suggest you to give a try with Debian Etch 4.0 (with netinstall) You will need not more than 30-40 Min. I find that for old hardware is Debian the best solution. I would install Xfce. (You can install first just the system and add afterwards the xfce-desktop ) 

And you can alway go back to Intrepid

---

### Post by JujuLand on 2009-02-06
ok, I'll try the debian 4.0

I'm surprised, I thought that debian was just build with gnome, and I see that there are kde and xfce builds too.

A+

---

### Post by tiresia on 2009-02-06
The default Desktop for Debian is Gnome, but when you install debian with the netinstall cd, after you installed the basic system you can choose to install or not a Desktop environment. There you shoul choose not to install it, otherwise it will install gnome. Finish the installation. An reboot. 
Then you install from the console xfce and everything you like

---

### Post by twodogsdad on 2009-02-08
JujuLand and tiresia,
Again, thanks for your work in this thread. I'm using my install on my imac G3 as a linux "homework" project. My main goal is to learn more about being a good linux user and I'm using this difficult install as a way to learn more. 

Are either of you interested in continuing a conversation here as I continue to trouble shoot this issue? Basically, I have everything working to the point of loading the xfce environment. 

I don't have any more trouble with video resolutions, etc. I can get to the shell with ctrl-alt-F1 and everything works like it is supposed to from there. My stopping point now is that when I try to run programs in xfce, Terminal for example, the program just launches and then apparently, the window closes, shuts itself down. I don't think it is a memory issue since I've run in low graphics mode with very low screen resolution, 512x384, and I still have the same issue.

I posted my imac specs earlier, a couple of pages ago. Again if you have an interest in helping me along with suggestions. I'd appreciate that. When I get home I can post my xorg.conf here.

Take care,
Cal

---

### Post by tiresia on 2009-02-08
> **twodogsdad said:**
> My stopping point now is that when I try to run programs in xfce, Terminal for example, the program just launches and then apparently, the window closes, shuts itself down. I don't think it is a memory issue since I've run in low graphics mode with very low screen resolution, 512x384, and I still have the same issue.

I don't use Xfce, but I remember of a similar problem. It refers only to thunar, but you can have a look here
[http://www.ppclinux.info/wiki/maclin/Ubuntu_Kubuntu_and_Xubuntu](http://www.ppclinux.info/wiki/maclin/Ubuntu_Kubuntu_and_Xubuntu)
[http://ubuntuforums.org/showthread.php?t=977120](http://ubuntuforums.org/showthread.php?t=977120)

I imagine, that you want to run Ubuntu. But I would really recommend for old mac to run debian instead (with Xfce)

---

### Post by JujuLand on 2009-02-09
@twodogsdad,

I have the same problem with Ubuntu and gnome. I have tried to change the memory modules (as the one I put to upgrade memory (64 > 512 Mo) were 133 Mhz instead of 100 Mhz, but the test whith two 64 Mo had the same result.  So I don't think it's due to memory, but what ?

@tiresia,

I have installed debian, but I think I had not make it correctly, because now, I can log, but no xserver. I've been too much busy today, and I try again, but without unchecking something. I'll try to install xfce then. . 

A+

---

### Post by tiresia on 2009-02-09
> **JujuLand said:**
>  @tiresia, . I have installed debian, but I think I had not make it correctly, because now, I can log, but no xserver. I've been too much busy today, and I try again, but without unchecking something. I'll try to install xfce then. . A+
You did it right, otherwise you would have the default desktop (GNOME)
Now you need only to login as root and run
```
aptitude install xorg xfce4 xfce4-goodies 
```
[http://wiki.debian.org/DebianXFCE](http://wiki.debian.org/DebianXFCE)

---

### Post by JujuLand on 2009-02-10
ok, I'm doing it.

You just forgot to mention the su command before ;-)

I'll report how it works

A+

---

### Post by JujuLand on 2009-02-10
Well, I have tried it, and except some habits I have taken with Ubuntu (and more with gnome), it's really a nice and light GUI.

I have just some questions about the way to install programs.

Is there an install manager like synaptics under ubuntu ?

How and were to found the programs we can install on debian ?
I suppose it's debs, but are  installs as achieved as under ubuntu ?
Perhaps better to try xubuntu for powerpc ?

And the first question I ought to send : how to browse the web. When I launch the debian browser, it gives me an nice file browser, but in local and in a kind of terminal.

I don't want to use Firefox which sucks a lot, but a smaller browser.

Is Galeon usable ? Is-it secure ?
Can we use wine on a powerpc ? I would like to use K-Meleon, a nice browser for Windows, I use under Ubuntu and Windows.

Thanks for the answers and for the big help you have given to me and to others.

A+

---

### Post by tiresia on 2009-02-10
> **JujuLand said:**
> I have just some questions about the way to install programs.
Is there an install manager like synaptics under ubuntu ?

How and were to found the programs we can install on debian ?
I suppose it's debs, but are  installs as achieved as under ubuntu ?
Perhaps better to try xubuntu for powerpc ?
Ubuntu is Debian based, so you will find in Debian almost anything you find in Ubuntu. I suggest you to visit the Debian web-site and download some documentations. 
If you installed Etch, you will notice how much stable Debian can be. But if you would like to try something more modern (for grafic) you can upgrade to Lenny. 
BACKUP YOUR XORG.CONF If it is working for you, you can use it also for Ubuntu or whatever you like.

Anyway, if you don't see so many programs as in Ubuntu, it't related to the Xfce Desktop not to Debian. You can install in your Desktop whatever you like. To look for a programm use 
```
apt-get search NameOfTheApplication
```  
Debian's Devs recommend to use 'aptitude' instead of 'apt-get', and debian's people do not make a large use of 'sudo'. You can install programms in a similar way 
```
apt-get install NameOfTheApplication
```  



> And the first question I ought to send : how to browse the web. When I launch the debian browser, it gives me an nice file browser, but in local and in a kind of terminal.
The default browser of Gnome is *not* Firefox but Epiphany. To install it search for Epiphany-browser

> Can we use wine on a powerpc ? I would like to use K-Meleon, a nice browser for Windows, I use under Ubuntu and Windows.
Unfortunatly there is no Wine for powerpc. You can use an emulator, Qemu - but it will run extremely slow on your machine. I think that you will like Epiphany, it works a bit different than other Browser (they use tags instead of Bookmarks), and it is much lighter than Firefox

If X is working good for you, can you please post your xorg.conf here. It would be interesting to see how it looks now.

---

### Post by JujuLand on 2009-02-12
Hi, I'm here again

I haven't yet installed the browser, because the web access was busy (with another Ubuntu install :)), but I put here the xorg.conf which works:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/X11R6/lib/X11/fonts/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/X11R6/lib/X11/fonts/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/X11R6/lib/X11/fonts/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/X11R6/lib/X11/fonts/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    FontPath    "/usr/X11R6/lib/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    [COLOR=Red]Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"[/COLOR]
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fr"
    Option        "XkbOptions"    "lv3:lwin_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS"
    Driver        "ati"
    Option        "UseFBDev"       [COLOR=Red] "true"[/COLOR]
EndSection

Section "Monitor"
    Identifier    "iMac"
    Option        "DPMS"
    HorizSync    [COLOR=Red]60-60[/COLOR]
    VertRefresh    75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        [COLOR=Red]"ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS"[/COLOR]
    Monitor        "iMac"
    DefaultDepth    [COLOR=Red]24[/COLOR]
    SubSection "Display"
        Depth        1
        Modes        [COLOR=Red]"800x600" "640x480"[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        [COLOR=Red]"800x600" "640x480"[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        [COLOR=Red]"800x600" "640x480"[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        [COLOR=Red]"800x600" "640x480"[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        [COLOR=Red]"800x600" "640x480"[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        [COLOR=Red]"800x600" "640x480"[/COLOR]
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "DRI"
    Mode    0666
EndSection

```As you can see, there is some important changes.

1) Debian recognize the good card type

2) All the modules are loaded

3) The defs for all bit depth doesn't have 1024x768

When (if) I'll try again with ubuntu, I will test with this xorg.conf, but I think I have  already tried it in my previous tests (but perhaps in 1024x768 mode). So, we can think  It perhaps won't work with Ubuntu.

I probably try to install xubuntu instead to make the system quicker (as possible) than with Etch

A+

---

### Post by twodogsdad on 2009-02-12
@Jujuland. Hello. I'm also, now, trying a Xubuntu install on a powerbook G4 550 MHz 512 MB ram. The details in your xorg.conf file look like the ones that I got when I did a reconfigure using "dpkg-reconfigure xserver-xorg". 

As for my Xubuntu install on my g3 imac... ... As tiresia pointed out to me earlier there is a pretty serious bug where gnome and xfce don't play nice with ppcs. A fellow did a recompile of most of the packages and, apparently, reinstalling them works but I haven't been able to download them yet. (@tiresia, I've been trying to wget them from [http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335cac612ab8569c87d0c]("http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335cac612ab8569c87d0c") but I'm  having some trouble so I'll have to check on whether I'm using wget right. I also tried the command line browser lynx but also with no success yet.)

Keep up the good work I'll let you know how my efforts this weekend go.

---

### Post by tiresia on 2009-02-12
> **JujuLand said:**
> 
When (if) I'll try again with ubuntu, I will test with this xorg.conf, but I think I have  already tried it in my previous tests (but perhaps in 1024x768 mode). So, we can think  It perhaps won't work with Ubuntu.

I probably try to install xubuntu instead to make the system quicker (as possible) than with Etch

A+
Great, that it is working for you with Debian. If you need some better looking software, before installing Xubuntu upgrade Etch to Lenny running Xfce. Of course, backup your xorg.conf on an external Disk ;)

---

### Post by JujuLand on 2009-02-16
Well, I have now installed Epiphany, and I can browse correctly on this little config.

I'm now trying to find  a mail client which will be lightest than possible, efficient and not a text client as Mutt.

I have looked for Debian site and found these programs that can be used:

-claws-mail
-icedove
-sylpheed

I haven't found thunderbird that I use on other configs, but I think it won't be as lighter as I want (due to xul), and I beg that icedove will have the same default to my eyes (even if I like Thunderbird)

I haven't found Evolution too , but I dont know if it takes a lot of resources.

Finally what would be the better choice ?

Now, for the OS, I'll try xubuntu (I'll replace the HD, not to broke what is ok for now).

A+

---

