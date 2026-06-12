---
title: "Totally new to Xubuntu, Any Advisde??"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by martnus on 2008-02-26
Hi Out There In Unbuntu land!!,

   I am totally new to the world of Linux and Ubuntu.  I am hoping to move more towards the Linux world and hoping to learn a lot about Xubuntu, it's install issues, etc.
   
     I work for a local school system, and we have a Linux "Keyboarding" lab, where they instruct 6th - 8th graders on how to learn typing.  It was set up a few years ago by my predecessor who had very little to work with, so he used Fedora workstations booting to a Fedora Server (A Dell desktop) all in a closed network of about 30 computers.  All of these computers run a Pentium I, 166MHz CPU with about 32MB to 64MB of RAM.  They boot from a 32MB (or 64MB) Flash Drive to the server.
     
     When I came onboard the team in July, the Tech who set this up was already long gone, and at the start of the new school year, there have been problem after problem with this lab.  So, to make this a little easier, I have decided to slowly replace the existing workstations with stand-alone Xubuntu machine.  I have been removing the Flash drives and installing small (3.8 to 6GB hard drives) and increasing the RAM (up to at least 96MB, some to 128MB) and have been installing Xubuntu on them.
      
     I chose Xubuntu Dapper Drake 6.06.1 because it boasts that it can run well on 64MB of RAM.  I tried other flavors of Linux (like Fluxubuntu) and looked at others (like Damn Small Linux and Puppy/ Chubby Puppy) but they all are a lot harder to install.  And, being VERY new to Linux, I need this to go as smoothly as possible.

     Anyway, after that long winded brief history...lol...I wanted to see if anyone could help me out with some issues I have had?

    1)Sometimes after a complete install (which usually takes about 4 hours), the machine reboots, I get the "Xubuntu" screen where it is loading all of the necessary items and telling you if the install is "OK" or not, then the screen goes blank and I wait for the GUI interface to start, and I get nothing.  Sometimes that nothing starts out as a flashing underline cursor in the upper left corner and then the screen goes completely blank.
     2)Other times I will get the same reboot startup (Xubuntu screen and all) and then it waits and I get a "Xserver/Video card" error message asking me if I want to view the log.  I can click "Yes" but then I get a command line interface that I have no idea how to use or manuever.

     So, if anyone has seen these issues before and can help out a Newbie, I'd certain relish the opportunity to learn all of this.  Thanks....Martnus

---

### Post by Seisen on 2008-02-26
What video card do you have in the computers, also have you thought about an Edubuntu setup with a LTSP server?

---

### Post by LeAstrale on 2008-02-26
i would actually suggest that you postbone the GREAT Xubuntu install for a bit and then install Xubuntu on your own desktop/laptop for a month or so just to learn the system a little before throwing your students into the lab. 

Do you use the alternate installer disc ?

The error message you get from xorg (xorg is the program controlling the GUI) shows that your graphics drivers aren't setup properly and that it would like you to review the log file to check for errors.. most basically you need to reconfiger your xorg.conf to use the vesa driver for the graphics card and only have resolutions that the screen can take.

/Astral-1

---

### Post by martnus on 2008-02-26
Hi Seisen,

  There are actually a number of various video cards in these machines.  Since I am using the machines that are existing, the ones that had problems on the Fedora Network, I am stuck with a lot of old and obsolete junk.  What most of them have are "S3 ViRGE On-Board" PCI cards.  Some are varients of that "S3" type but for the most part arre that one card.

    What is an LTSP Server?

     Basically, this is a fix for now.  Originally, my boss wanted me to use Edubuntu (and I just got the CD's I ordered in the mail yesterday), but as standalones, they require  500MHz CPU's and 128MB+ of RAM.  Since what I have to work with is only 166MHz CPU's and 64MB to 96MB of RAM, that would not work. That is why I went with Xubuntu.

    When I say that this is a temporary fix, I mean that this lab is likely to change over the next year.  That all depends on the next budget meeting in April.  If the new budget passes, we will most likely be using TermTek Thin Clients in the lab (that we have throughout the District, which will be replaced with laptops or desktops).  If that happens, then we will probably upgrade to Edbuntu, but I don't know if that will ahppen.  

    Right now, my problem and challenge, is that I have a classroom with 30 workstations with about 8 or 9 of them down (for various reasons).  I have a teacher who is getting frustrated by the fact that he can't properly teach Typing if you don't have a machine to practice on.  So, I am trying, within my day, admist various other problems I deal with at the school, to rebuild this lab.  I have rebuilt 3 so far with much success.  They ONLY use the Xubuntu for the AbiWord Word Processor.  Heck, if I could find a Linux based system that ONLY booted into a Word Processor, that's be great!!  But, I have never seen one.

   Thanks for the answer so far, and I look forward to hopefully reading more advise you might have to offer.  I hope that this exlains a bit more of what I am dealing with?  Thanks....Martnus

---

### Post by martnus on 2008-02-26
Astral-1,

    Thanks for the advise, my problem is that I don't have the means to do that.  Plus, they ONLY use these Linux machines for the Word Processor Program.  So, it's not like they haev much to do but theurn them on, wait for them to boot, start the AbiWord Word Processor and start practice typing.

    I am using the Alt. version disk.  I mistakenly started with the LiveCD, but found out fast that wasn't what I needed.

    As for the video card, I figured that was the problem, but where I get stuck is that I have NO IDEA on how to do what you referred to.  Like I said, I am not used to Linux  nor do I have much experience with it.  What I DO find comforting is that I have some experience with DOS, so command line functionality is not foreign to me.  I guess it's just knowing how to access it, what to type and how to get through it all.

   I am learning and so far this is a great experience.  Thanks for the advise...Looking forward to getting more.....Martnus

---

### Post by mali2297 on 2008-02-26
> **martnus said:**
> 
    As for the video card, I figured that was the problem, but where I get stuck is that I have NO IDEA on how to do what you referred to.  


Run this in the terminal:
```

sudo dpkg-reconfigure xserver-xorg

```
You will be asked a bunch of questions, answer them as best you can.  Here is your chance to choose the *vesa* driver etc. If you don't know the answer to a question, just go with the default.

---

### Post by Seisen on 2008-02-26
Boot into recovery mode on each computer that is giving you problems and post what it says in xorg.conf. To access xorg.conf in the cli do this ```
vim /etc/x11/xorg.conf
``` and scroll down to the section here:

```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
       ** Driver          "intel"**
        BusID           "PCI:0:2:0"

```

There tell what is says for the Driver.

Here is information on an Edubuntu setup with an LTSP server.

[http://www.freesoftwaremagazine.com/articles/linux_terminal_server]("http://www.freesoftwaremagazine.com/articles/linux_terminal_server")

---

### Post by martnus on 2008-02-26
Wow, all this great information.  

I thank you all so far, and I am going to try these out.

Luckily, this last install went very well, and actually pretty fast, just under 3 hours.  It gave me no errors and I am onto another install right now.  I am printing all of these pages so I can follow through with them if another error pops up (which I am sure it will).

Again, thanks for the information and please keep it all coming!!

---

### Post by martnus on 2008-02-26
I don't know if anyone knows about this one (although I am sure that you guys do), but once I have my install complete, everything is working fine, is there a way to go into the properties of the Display to change the screen resolution from 800x600 to 1024x768??

I can do it from the "Applications" - "Display Settings" applet, but it only reads "Default"a which is the 800x600 screen size.  I am sure it has to do with the video card and what drivers are being installed, but if I can do what "mali2297" and "Seisen" suggested and find out what kind of video card is in there, how can I change that so it will accept the 
1024x768 screen size when I reboot back into the GUI again?

As always, thanks.....

---

### Post by LeAstrale on 2008-02-26
> **martnus said:**
> I don't know if anyone knows about this one (although I am sure that you guys do), but once I have my install complete, everything is working fine, is there a way to go into the properties of the Display to change the screen resolution from 800x600 to 1024x768??

I can do it from the "Applications" - "Display Settings" applet, but it only reads "Default"a which is the 800x600 screen size.  I am sure it has to do with the video card and what drivers are being installed, but if I can do what "mali2297" and "Seisen" suggested and find out what kind of video card is in there, how can I change that so it will accept the 
1024x768 screen size when I reboot back into the GUI again?

As always, thanks.....

the answer you would be looking for would also be in the xorg.conf file we just love to talk about in here :)

i will post mine so you can see what i am talking about.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Jan 11 15:05:59 PST 2008

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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "dk"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL M782p"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 1280x1024"
    HorizSync       31.5 - 81.0
    VertRefresh     50.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Driver         "nvidia"
    BoardName      "vesa"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Monitor        "DELL M782p"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 1024
        Depth       24
        Modes      "1280x1024@75" "1280x960@60" "1152x864@75" "1280x1024@60" "1024x768@60" "1280x960@75" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection


```

you see a lot of information here... at the buttom line you see the resolutions my screen is capable of (or the resolutions i have typed in at least) those are the resolutions you typically would hae to choose between in the display settings.

i hop this clarifies a little... to get to edit this file from CLI you need to type: ```
sudo nano /etc/X11/xorg.conf
```

that should give you a very primitive text editor from CLI... to save when you're done just push ctrl+x then it will ask if you want to save the canfes and afterwards which name they should have... make sure you overwrite the default xorg.conf here

if you want to make a backup of the original xorg.conf before messing around with it here is a command for you ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

/Astral-1

---

### Post by martnus on 2008-02-26
WOW, lots to think about here huh??  I guess you DO love to talk about this huh??

Thanks, I will print this and give it a whirl.....Martnus

---

### Post by 3rdalbum on 2008-02-26
Your other option would be something non-Ubuntu. I think Puppy Linux comes with Abiword, uses less memory when installed, and has the option to use a more basic X server which probably has a greater chance of working with whatever video hardware is in those computers.

---

