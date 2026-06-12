---
title: "Beryl Crashing:("
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by chesman on 2006-12-31
Okay, i am trying to setup beryl, i have followed all the steps in here:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

I have managed to get all the stuff installed that i need to install, but for some reason it craps out and Beryl will not load. 

I do not get the Beryl splash screen, but i do get the diamond in the task bar. When i chang the windows manager to Beryl, it flickers and goes back to Metacity.

anyone have any ideas?

---

### Post by chesman on 2006-12-31
As well, when i change my session before logging in to the one i was told to change too, it makes all my scrolling choppy, and loading very slow and jagged.

---

### Post by croppyboy on 2006-12-31
What video card do you have? Are you using Beryl 0.1.4?

---

### Post by croppyboy on 2006-12-31
For 0.1.4 . . . to get the splash screen . . . you need to open **Beryl Manager** - scroll down to **Image Format** - and make sure both **Png** and **Svg** are checked

---

### Post by chesman on 2006-12-31
i am useing an ATI x1300.

And i am currently in my windows right now, so i cant tell the version, whatever the version that was downloaded through the the rep in that how to i linked.

---

### Post by croppyboy on 2006-12-31
Also . . . I used [[COLOR="Orange"]**this**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=263851") How-To with no problems . . .

---

### Post by chesman on 2006-12-31
that how-to is aimed at Nvidea though isnt it?

---

### Post by croppyboy on 2006-12-31
Here is a link to the ATI instructions from the link I posted above . . . you might want to check this against the one you used to see if they are the same . . . I've got an nvidia card so I haven't any experience with ATI . . .

[http://doc.gwos.org/index.php/BerylOnEdgy]("http://doc.gwos.org/index.php/BerylOnEdgy")

---

### Post by chesman on 2006-12-31
Thanks.

i am aalmost completed that setup, but wheni h vae to edit the xorg.conf file i get a permissions error :(

You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

would changeing the permissions to allow me on that one file let me save it?

---

### Post by chesman on 2006-12-31
As well it tells me to replace my Device section in the file, but i have two:

> Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Which one would i replace with:

> Section "Device"
Identifier "{your card model}" <-do not edit this line in your xorg.conf
Driver "ati"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
## If above is hashed, change the following to "XAANoOffscreenPixmaps"
Option "EXANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 1, 2, 4, or 8 depending on your system
Option "AGPFastWrite" "on"
EndSection

---

### Post by croppyboy on 2006-12-31
you need to use sudo to edit the file - open a terminal and enter the following:

```
sudo gedit /etc/X11/xorg.conf
```

make the changes and save . . .

---

### Post by croppyboy on 2006-12-31
Here is my xorg.conf

```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
    Option          "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24

    # Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

    # If you are using an older version of compiz that
    # does not support rendering into the Composite
    # Overlay Window, you will need to disable clipping
    # of GLX rendering to the X Root window with this
    # option, or you will get a blank screen after
    # starting compiz:
    #    Option "DisableGLXRootClipping" "True"

    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by croppyboy on 2006-12-31
I would say the second one . . . but like I said, I have nvidia so I don't have any experience configuring ATI . . .

---

### Post by chesman on 2006-12-31
Okay, i think i totally have it all fooled up, wher ei tried a few things, and i dont even know what i have and not have installed.

How can i totally remove beryl, and start over again?

---

### Post by croppyboy on 2006-12-31
Go to **System** > **Administration** > **Synaptic Package Manager**

**Search** - Beryl

Right click on the Beryl and Emerald packages and then click apply

Also - make sure your xorg.conf file is back to its original settings (if you changed it) . . .

---

### Post by croppyboy on 2006-12-31
Sorry . . .

Right click on the Beryl and Emerald packages and **Mark for Complete Removal** and then click apply

---

### Post by chesman on 2006-12-31
cool, removed both, and now rebooting and will start again later.

---

### Post by croppyboy on 2006-12-31
Also . . . you might want to check out this: [http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7]("http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7")

Check out the top of the page

> Radeon open source driver, aiglx, and Beryl

The following steps apply for all ATI cards supported by the radeon open source driver. To find out whether your ATI card is supported look here:
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
If your ATI card is not supported by the radeon driver consider using fglrx driver and xgl

And follow the link to see if your card is supported . . .

---

### Post by croppyboy on 2006-12-31
Hopefully, someone with ATI and Beryl experience can offer some more advice . . .

---

### Post by chesman on 2006-12-31
Okay,

Well when i try to run the first command.. i get this error:
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by croppyboy on 2006-12-31
This step?

```
Install your *ubuntu-desktop metapackage specific to your DE, e.g. sudo apt-get install ubuntu-desktop
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If so . . . you probably have synaptic open . . . you can't have more than one package manager (synaptic, update manager, etc) open at the same time . . . so close synaptic

---

### Post by chesman on 2006-12-31
yup, realized that, so iwent back, and did everything from step 1, it all went flawlessly wihtout errors, time to restart and see whats happens.

Now will i be able to get this going from my gnome desktop?

or do i have to create a different session?

---

### Post by croppyboy on 2006-12-31
Did you add beryl-manager to your start-up programs?

---

### Post by croppyboy on 2006-12-31
I just did a quick search for info on the ATI x1300 and it appears that the card isn't supported by aiglx . . .

You are going to have to try XGL . . .

---

### Post by croppyboy on 2006-12-31
Here is a link that will hopefully get you up and running with XGL and beryl . . .

[http://ubuntuforums.org/showthread.php?t=327751&highlight=beryl+ati+x1300+xgl]("http://ubuntuforums.org/showthread.php?t=327751&highlight=beryl+ati+x1300+xgl")

---

### Post by chesman on 2006-12-31
lol

my Ubuntu now lcoks up on boot :)

So i am going to reinstall Ubuntu later and start from scratch.

---

### Post by croppyboy on 2006-12-31
Good luck . . .

When I first switched to Ubuntu a few months ago, I had to do a couple of clean re-installs . . . but I've now been using Ubuntu as my primary OS for about 5 months . . .

Look into the XGL for beryl when you do the re-install . . .

---

### Post by chesman on 2006-12-31
and wow, that last how-to seems very good, i will try that out tomorrow and let you know.

---

### Post by chesman on 2006-12-31
So, can you do a clean reinstall straight from the cd?

---

### Post by croppyboy on 2006-12-31
> **chesman said:**
> So, can you do a clean reinstall straight from the cd?

Yep . . . no problem . . . just pop the live cd in and run through the install process again . . . (make sure to back-up any files you don't want to loose) . . . :)

---

### Post by chesman on 2006-12-31
Awesome, ill hit that up now.

Thanks Croppy

---

### Post by chesman on 2006-12-31
okay... new problem, when i pop in the live CD, i run the install, it gets to Step 5, i click next for it to automaticlly resize, and it flashs a pop-up , to fast for me to read, then it just sticks at the screen with the loading icon as the cursor, nothing happens.....


What should i do?

---

### Post by croppyboy on 2006-12-31
Hmm . . . I never did the auto resize option . . . I always did a manual configuration . . . 

Are you installing to a dual boot system with some flavor of windows? If so, you might want to defrag your hd first . . .

---

### Post by croppyboy on 2006-12-31
Then do a manual configuration . . .

---

### Post by chesman on 2006-12-31
defrag in windows?

and then what do i select for a manuel install?.....

imsoo totally lost lol

---

### Post by croppyboy on 2006-12-31
Do the install like you did before . . . but when it comes to the selection of partitons there should be a choice to manually configure partitons . . .

---

### Post by croppyboy on 2006-12-31
Are you going to keep a windows partiton?

---

### Post by chesman on 2006-12-31
Yerah, i selected the pre-made partitions from the first install, and only selected them for formatting and to install to them.

I am keeping a dual boot system going, for my girlfriends sake right now, and well for ine as well when this does not work :)

---

### Post by croppyboy on 2006-12-31
What size hd do you have?

---

### Post by chesman on 2006-12-31
250 gig, partitioned originally to have 60 gigs for system files, the rest for storage.

I currenlty have the 60 gigs broke up for both OS's

---

### Post by croppyboy on 2006-12-31
I would try the manual configuration if you already have partitons set up . . .

When I did a re-install . . . I started from scratch . . . re-installed windows and everything . . .

I've got a 120 GB hd and 300 GB hd . . . I use the 300 for storage (/home) and I have the 120 split  - 40 GB for Vista - 10 GB for Ubuntu root (/) - 30 GB for FAT32 partiton - 30 GB for back-up - and space for the swap 

If are you going to format your storage in ext3 you  might want to create a FAT32 partiton to easily share files between Ubuntu and Windows . . .

---

### Post by chesman on 2006-12-31
im posting this from Ubuntu now. It installed fine, and my windows os is fine as well :)

Time to try that howto guide you sent me.

---

### Post by chesman on 2006-12-31
Oh, something strange i found.....

upon booting ubuntu for the first time, it already mounted my NTFS storage partition and its readable, as well as the two hidden Dell partitions, which 1 i can unmount lol

---

### Post by croppyboy on 2006-12-31
Yeah . . . you can read the ntfs but you can't directly write to them (although there are work-arounds for this) . . .

Let me know if the XGL works out . . .

---

### Post by chesman on 2006-12-31
oh, definitly will, waiting for updates to finish then a reboot, and away i go :)

---

### Post by chesman on 2007-01-01
Hey Croppy, i follow that howto you sent me, when i get everythin done, do the final reboot, it reboots to a black and white checkered screen with the loading cursor and doesnt go anywhere :( happened twice so far.
so i gota reinstall ubuntu yet again later today

---

### Post by croppyboy on 2007-01-01
What version of Ubuntu are you using? 6.10? and is it Gnome or KDE (Ubuntu or Kubuntu)?

---

### Post by croppyboy on 2007-01-01
I would use the second how-to on that link I provided . . . here is a link straight to the page . . . [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")

Start with the **Graphics Card Drivers** - I think, because of the card you have, you are going to have to use the **fglrx** driver . . .

Then move to the **XGL** section and follow the instructions for installing . . . (use the repos - ubuntu.beryl-project.org/ edgy main in your sources.list file) . . .

---

### Post by croppyboy on 2007-01-01
If, after this, it still doesn't work . . . then I'm not sure what to do . . . the ATI x1300 doesn't really support all of the fancy eye-candy natively (from what I understand) . . . 

You might try searching for **Beryl ATI x1300** threads or starting another post with a more specific title **Help: Beryl on ATI x1300** - do the search first, though . . .

If you still have problems but you [COLOR="Red"]really, really[/COLOR] want the Beryl eye-candy :) . . . I would try to invest in a better graphics card (if you can) - preferably **nvidia** . . . you should be able to do a search and find a list of graphics cards that will work . . .

---

### Post by chesman on 2007-01-01
Thanks croppy.

ill give it a try :)

---

### Post by chesman on 2007-01-01
Okay, went trhoguh everything, seemed to go fine, when i try to load the XGL session from logging in, it just sticks at a blank screen. So i guess its the card not supporting it :(

i will poke around the xgl and beryl irc chans, but who knows.

---

### Post by croppyboy on 2007-01-01
Good luck!

---

### Post by chesman on 2007-01-01
Thanks, i have decided to stop looking to have my desktop all flashing, and concentrate on what i use windows for from now on, Web design, chating, and playing wow, lol.


So i shall be moving onto wine, trying to get my damn Dock to work, and well, eventually find a reason beryl will not work for me.

Can you she dany light on my dock? reccommend one?

---

