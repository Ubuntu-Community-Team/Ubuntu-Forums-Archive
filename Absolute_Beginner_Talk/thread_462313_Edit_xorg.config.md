---
title: "Edit xorg.config"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by acutu on 2007-06-02
Hi, I have seen a post with the text I want to copy to update the xorg.config file containing the same details as my graphics card. But it is read only and I don't know how to get it to allow me to paste the copied contents in to take the place of the part referring to the graphics setting. Also, does ctrl+c work to copy and ctrl+v work to paste?
Thanks.

---

### Post by mikewhatever on 2007-06-02
Go to Applications>Accessories>Terminal and copy paste the following comands
> cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
> gksudo gedit /etc/X11/xorg.conf

---

### Post by H.E. Pennypacker on 2007-06-02
You will need administrative priviliges before you can edit xorg.conf.  That is why you should press ALT-F2, and type gksudo gedit /etc/X111/xorg.conf.  You will then be asked for your password.

---

### Post by acutu on 2007-06-02
Thx Mike & H.E.
Such quick response, this site rocks!

Al C.

---

### Post by acutu on 2007-06-02
Hi, I have edited the file and I try to save but it says: Could not save the file /etc/X111/xorg.conf..
Any ideas...maybe I am not administrator like I thought I was, but then I would have expected it would have alerted me to that earlier rather than offering the password prompt.

---

### Post by bodhi.zazen on 2007-06-02
> **acutu said:**
> Hi, I have edited the file and I try to save but it says: Could not save the file /etc/X111/xorg.conf..
Any ideas...maybe I am not administrator like I thought I was, but then I would have expected it would have alerted me to that earlier rather than offering the password prompt.

Well, it could be a tyop 

/etc/**X11**/xorg.conf

Or you did not open the file as root.

Open a new document, cut and past you shiny new edit, re-open /etc/X11/xorg.conf as root

```
gksudo gedit /etc/X11/xorg.conf
```

cut and past back your edit ~ viola.

---

### Post by ncappel1 on 2007-06-02
Another approach is to use a handy nautilus script "Root-nautilus-here that will allow you to right click on a file/folder and allow you to open it as root.

[http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)

---

### Post by bodhi.zazen on 2007-06-02
> **ncappel1 said:**
> Another approach is to use a handy nautilus script "Root-nautilus-here that will allow you to right click on a file/folder and allow you to open it as root.

[http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)

Oh, yes that is nice, be careful with it though and *try* not to abuse it too much :twisted:

---

### Post by acutu on 2007-06-02
Thx. Givin it a go.

Al C.

---

### Post by acutu on 2007-06-02
I've really screwed it up now! I managed to paste in the alterations, saved the text document, rebooted the computer, and now after introductory Ubuntu colour I get unable to load /etc/X11/xorg.conf and screen is black with white text. I think it is time to reinstall Ubuntu! Unless I can somehow tell it to use the backup? 

I presume the settings were not OK for my laptop. The guy who had posted the resolution details was using a Dell, mine is a 17" Acer. 

At least I am still in early stages of getting used to Ubuntu, and I am able to use this, my old computer in the meantime.

Al C.

---

### Post by annda on 2007-06-02
what is your video card? maybe you don't even need to edit xorg.conf by hand...

what is the name of the backup file? if you used mikewhatever's advice, you can restore it by typing:

cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by acutu on 2007-06-02
Thanks annda, but it seems that that file or directory no longer exists.

Al C

---

### Post by ncappel1 on 2007-06-02
All is not lost!!!

assuming you did the backup commands suggested by mikewhatever, it is still possible to take the old settings and put everything back to normal.

to do this enter the following into a terminal:
```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

(edit: didn't see that the previous post already mentioned the above advice)

if you didn't backup the xorg document in the first place (naught, naughty) try running the "depackage-and-reconfigure" command for xorg
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
this will run the reconfigurement at a high priority (that's what the "-phigh" means)

I certainly hope this helps

---

### Post by acutu on 2007-06-02
Thx, I think what has gone wrong is that I did make a backup, but later backed up again or saved by mistake at a time when the information was not loaded. At least I think that is what happened. I definitely saw the backup file with a date and time in the filename when I was trying to edit from within the etc folder.
I have only text interface now.   cp: cannot stat '/etc/X11/xorg.conf_backup'
Because the backup had a date in the filename last time I saw it, I have tried a wildcard aproach, and do get a different result:
etc/X11/*xorg.conf
does bring up a -bash, but permission denied. 

UPDATE: I took advice from bodhi.zazen to reconfigure X with new users, and that worked. I don't think the resolution is quite right, I chose the setting on the list above vga, but we are out of the black and white or blue screens!

Cheers!

Al C.
RESOLVED.

---

### Post by parth32 on 2007-06-05
> **H.E. Pennypacker said:**
> You will need administrative priviliges before you can edit xorg.conf.  That is why you should press ALT-F2, and type gksudo gedit /etc/X111/xorg.conf.  You will then be asked for your password.

It worked but it doesn't allow me to save it:confused:?????
Any idea why??

[IMG]http://img235.imageshack.us/img235/4671/untitledfq4.jpg[/IMG]



Thanks

---

### Post by ugm6hr on 2007-06-05
It's:
*/etc/X11/xorg.conf*

Be careful with correct spellings when you edit it too.  Best to make a backup first.  Not sure how it opened a non-existent file in the first place.

And X11 is different than x11 (i.e. case matters).

---

### Post by parth32 on 2007-06-05
> **ugm6hr said:**
> It's:
*/etc/X11/xorg.conf*

Be careful with correct spellings when you edit it too.  Best to make a backup first.  Not sure how it opened a non-existent file in the first place.

And X11 is different than x11 (i.e. case matters).

Thanks. I'm trying to get widescreen resolution, and i am totally new to Linux so i have no idea how all setting works. I read about changing this file to have it but it still doesn't give me that option..

It would be great if you can explain how it works..

Anyway thanks for your reply.

---

### Post by timzak on 2007-06-05
I'm still a newbie (going on 2 months now) and after a few reinstalls of Feisty, on my last reinstall, I immediately made a backup of xorg.conf right after the clean install.  I keep that separate from everything else so I don't ever overwrite it (I learned that it's easy to overwrite a good backup with a bad backup if you always save your backup as *.bak).  So I have two sets of backups:  the one from the clean install, and the "current" one.  If I ever screw something up, I can read through both backups side-by-side and do a line-by-line comparison.  I also have the commands to rename, backup and restore written on a piece of paper so I can refer to them if I can't load the desktop.

Glad you got your desktop back.  Now you can work on getting the resolutions, etc. right.

---

### Post by bodhi.zazen on 2007-06-05
> **parth32 said:**
> It worked but it doesn't allow me to save it:confused:?????
Any idea why??

[IMG]http://img235.imageshack.us/img235/4671/untitledfq4.jpg[/IMG]



Thanks

lmao  parth32


The file name is (watch case) :

[size=2]**/etc/X11/xorg.conf[/size]**

:lolflag:

NOT /etc/[color=red]x111[/color]/xorg.[color=red]cofg[/color]

==========================================

OK ...

Do this : 

```
gksudo gedit /etc/X11/xorg.conf
```

Under the "Monitor section", make sure you have the correct virt and horiz settings for your monitor:

> Section "Monitor"
    Identifier  "display_sgi"
    VendorName  "sgi"
    ModelName   "gdm20e21"
    **HorizSync   30-96**         [color=red]<--- Your settings here[/color]
   **VertRefresh 50-160**    [color=red]<--- Your settings here[/color]
    Option      "DPMS"

Under the screen section, reduce your color depth and enter your desired resolution :

> Section "Screen"
    Identifier  "screen_twinview"
    Device      "6600gt_twinview"
    Monitor     "display_iiyama"
    **DefaultDepth 24**  [color=red]<--- Reduce to 16[/color]

    Subsection "Display"
        Depth       16
        **Modes       "1600x1200" "1280x1024" "1024x768" "800x600" **[color=red]<--- Set Resolution[/color]
    EndSubsection

    Subsection "Display"
        Depth       24
        **Modes       "1600x1200" "1280x1024" "1024x768" "800x600"**[color=red]<--- Set Resolution[/color]
    EndSubsection

Save and exit gedit.

Restart X , In a terminal enter :

```
sudo /etc/init.d/gdm restart
```

If that *works* and you would like, you can go back and increase you color depth back to 24 -> restart X

---

### Post by parth32 on 2007-06-06
Hey bodhi.zazen, i know that i had a spelling mistake.
But anyway i followed your instruction and i still couldn't do any better. When i type command line in console it asked me to enter my password and guess what!!! I can't type anything there... 
I think i need some serious help/ 

Is there any one who had a same problem as me, and they sorted it out. If yes then please tell me how. 

```

Problem:
[COLOR="Red"]Can't get widescreen resolution.1440x900[/COLOR]

```

---

### Post by timzak on 2007-06-06
> **parth32 said:**
> Hey bodhi.zazen, i know that i had a spelling mistake.
But anyway i followed your instruction and i still couldn't do any better. When i type command line in console it asked me to enter my password and guess what!!! I can't type anything there... 
I think i need some serious help/ 

Is there any one who had a same problem as me, and they sorted it out. If yes then please tell me how. 

```

Problem:
[COLOR="Red"]Can't get widescreen resolution.1440x900[/COLOR]

```

In the console, when you type your password, you will not see anything be typed (not asterisks, dots, etc).  Just type the password in and hit Enter.  It will work.

Good luck.

---

### Post by parth32 on 2007-06-06
Thanks a lot for your help, but nothing is working...
All i want is to get 1440x900 resolution and i can not get it. :(:(

---

### Post by bodhi.zazen on 2007-06-06
If you made those changes to xorg.cong, and restated X, and still no joy ...


1. What videocard.

2. What montior, what are the horiz and vert settings?

3. Post your xorg.conf

---

### Post by parth32 on 2007-06-06
Here's my xorg.conf 
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
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "LE1923"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
    Monitor        "LE1923"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes "1440X900" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        4
                Modes "1440X900" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        8
                Modes "1440X900" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        15
                Modes "1440X900" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        16
                Modes "1440X900" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        24
                Modes "1440X900" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection


```[COLOR=RED]And this is the highest i can choose..[/COLOR]


[IMG]http://img403.imageshack.us/img403/6463/sc17fr0.jpg[/IMG]

---

### Post by snipes23 on 2007-06-06
u know what I see as kind of interesting, I cant get my 1280X768 res showing, and 1024x768 and a few other low res's show up, but not the 1280x768.  I'm almost wondering If I put another res in that is higher than the 1280x768 if that would allow me to pick 1280x768?  i dunno

---

### Post by broshe on 2007-06-06
I have the same problem with editing xorg.conf (In Xubuntu).
I tried opening the terminal and typing:
gksudo gedit /etc/X11/xorg.conf

Than, I edited the xorg.conf.
when I tried to save it, it gave me the error message:
¨Can't open file to write¨

Is there a remedy ?

Thanks

---

### Post by parth32 on 2007-06-07
> **broshe said:**
> I have the same problem with editing xorg.conf (In Xubuntu).
I tried opening the terminal and typing:
gksudo gedit /etc/X11/xorg.conf

Than, I edited the xorg.conf.
when I tried to save it, it gave me the error message:
¨Can't open file to write¨

Is there a remedy ?

Thanks

Read this Page.. It has all solution to your problem.
[HTML]http://ubuntuforums.org/showthread.php?t=462313&highlight=widescreen+resolution[/HTML]

---

