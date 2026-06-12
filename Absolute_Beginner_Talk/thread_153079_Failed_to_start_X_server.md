---
title: "Failed to start X server?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by SamSlater on 2006-03-31
1st time ubuntu'r here and I cant even boot up the live cd! I boot up from the live cd and go through the normal setup process and come to a screen that says:

'**[!] Configuring Xserver-xorg**'

'**Select resolutions you would like the xserver to use**'

I select the usual 800x600, 1024x768 and my monitors native resolution of 1680x1050

The live install carries on a while doing lots of checks and getting lots of 'ok's'
before the 'ubuntu' load screen comes up.

I then get:

'**Failed to start X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x servers ouput to diagnose the problem?**'

I select 'yes'

I then get:

'[B]X Windows system version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release date: 9 febuary 2005
X Protocol version 11, Revision 0, Release 6.8.2
Build Operating system: Linux 2.6.8.11 x86_64 (ELF)
Current operating system: Linux Ubuntu 2.6.12-9-amd64-generic # 1 Mon
Oct 10 13:27:39 BST 2005 x86_64
Build date: 10 Oct 2005
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure of latest version
Module loader present
OS kernal: Linux version 2.6.12-9-amd64-generic (build@king) (gccversion 3.4.5.20050809 (prerelease) (Ubuntu 3.44-6ubuntu8 )) #1 Mon
Oct 10 13:27:39 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting[/B]'

I select 'OK'

Then get:

'**Would you like to view detailed x server output as well?**'

I select 'Yes'

I get (again)

'[B]X Windows system version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release date: 9 febuary 2005
X Protocol version 11, Revision 0, Release 6.8.2
Build Operating system: Linux 2.6.8.11 x86_64 (ELF)
Current operating system: Linux Ubuntu 2.6.12-9-amd64-generic # 1 Mon
Oct 10 13:27:39 BST 2005 x86_64
Build date: 10 Oct 2005
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure of latest version
Module loader present
OS kernal: Linux version 2.6.12-9-amd64-generic (build@king) (gccversion 3.4.5.20050809 (prerelease) (Ubuntu 3.44-6ubuntu8 )) #1 Mon
Oct 10 13:27:39 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting[/B]'

I select 'OK'

Then get:

'**The x server is now disabled. Restart GDM when it is configured correctly**'

I select 'OK'

The get back to the command lines like 'Checking battery state...... (ok

I cant input anything apart from C+A+D which ejects the CD and reboots.

I is the ATI Radeon X800 drivers that Ubuntu doesn't support or my NEC MultiSync 20WGX2 widescreen?

My pc specs are:

Athlon64 Venice 3500+
Gigabyte K8N Pro SLI
Sapphire Radeon X800 512MB
2GB corsair xms3200
1 80gb Barracuda HDD with XP installed & 1 250GB WD Caviar doing nothing as it's waiting for Ubuntu installation!!!!

Helps much appreciated! I really wanna learn Ubuntu!

Ps I did boot up the live cd on my old system that had a different monitor & gfx card and it worked fine for the 3 hours I was playin around!


Thanks in advance

SamSlater

---

### Post by Mustard on 2006-03-31
Possible solutions are,

1. Use the boot option vga=771 (the boot options are listed with the functions keys at the boot: prompt when the CD first starts up)  I think the syntax is 'live vga=771'. It's been a long time since I booted up an Ubuntu live CD though, and my memory is less than perfect.

2. Try to reconfigure the xorg.conf to use 'vesa' drivers using this command..

```
sudo dpkg-reconfigure xserver-xorg
```
then
```
startx
#alternatively try this one
sudo /etc/init.d/gdm restart

```

I'm not totally sure how this works with a live CD either.  I think I asked someone to try it once with a live CD and I don't recall them saying it failed.

To get to a command line, you may need to use the ctrl + alt + f1 keys.  I'm not sure whether you are being dropped to a command line atm or not.

The issue is going to be your ATI card for sure.  It's as regular as clockwork that someone who has display issues is using ATI graphics.  ATI and linux are not a good mix due to the poor quality of the ATI drivers written for linux.

---

### Post by localzuk on 2006-03-31
> The issue is going to be your ATI card for sure. It's as regular as clockwork that someone who has display issues is using ATI graphics. ATI and linux are not a good mix due to the poor quality of the ATI drivers written for linux.

I'll second that. I have an ATI Xpress 200 built in gfx card which Does Not Work Well With Linux (TM). I had to go out and buy an Nvidia replacement.

---

### Post by SamSlater on 2006-03-31
Thanks Mustard,

I managed to boot up ubuntu to the desktop which is a hell of a lot further than I got before. Problem is I can only see the top toolbar or the bottom toolbar. It's like the widescreen has been rotated 90deg onto its side so it's really 1050x1680! Though the desktop in ubuntu is the right way!

'**sudo dpkg-reconfigure xserver-xorg**' and '**startx**' got me to go through all the hardware options which I left at defaults. The problem now is that when I set up the monitor I've tried setting it up via entering the resolution (1680x1050 @ 75hz) but then my monitors osd says 'out of range' and the ubuntu desktop is too tall and not wide enough. Going to the monitor resolutions options in ubuntu it's stuck at 1400x1050. 

My monitor at the 1680x1050 res runs at 60hz but the option in the ubuntu setup sets that res to 75hz and doesn't have a 60hz option for that res so I get why it's out of range. Going through the advanced setup and entering the horizontal and vertical frequency doesn't change a thing and I still get 1050x1680 instead of 1680x1050.

Trying other resolutions gets: '**error no displays detected**' or something simular.

Maybe it's because my monitor wont run at 75hz and only 60hz when the resolution is 1680x1050?

Any idea's how to get around this?

P.s I wish I had known about the ATI drivers problem. I only bought this card 2 days ago and was going to get the 7800gt but changed my mind at the last minute! doh!

Dying to ditch XP!! (apart from gaming)

---

### Post by sn123 on 2006-03-31
[QUOTE=SamSlater]Thanks Mustard,

I managed to boot up ubuntu to the desktop which is a hell of a lot further than I got before. Problem is I can only see the top toolbar or the bottom toolbar. It's like the widescreen has been rotated 90deg onto its side so it's really 1050x1680! Though the desktop in ubuntu is the right way!

'**sudo dpkg-reconfigure xserver-xorg**' and '**startx**' got me to go through all the hardware options which I left at defaults. The problem now is that when I set up the monitor I've tried setting it up via entering the resolution (1680x1050 @ 75hz) but then my monitors osd says 'out of range' and the ubuntu desktop is too tall and not wide enough. Going to the monitor resolutions options in ubuntu it's stuck at 1400x1050. 

My monitor at the 1680x1050 res runs at 60hz but the option in the ubuntu setup sets that res to 75hz and doesn't have a 60hz option for that res so I get why it's out of range. Going through the advanced setup and entering the horizontal and vertical frequency doesn't change a thing and I still get 1050x1680 instead of 1680x1050.

Trying other resolutions gets: '**error no displays detected**' or something simular.

Maybe it's because my monitor wont run at 75hz and only 60hz when the resolution is 1680x1050?

Any idea's how to get around this?

P.s I wish I had known about the ATI drivers problem. I only bought this card 2 days ago and was going to get the 7800gt but changed my mind at the last minute! doh!

Dying to ditch XP!! (apart from gaming)[/QUOTE]
could you post the contents of your xorg.conf file? The problem is generally with ati driver, you can fix it by changing the driver to a generic one like vesa or mesa to get the screen fixed up first and then try to download fglrx which has better support for ATI drivers. Please post the content of your xorg.conf file and somebody should be able to give you a detailed procedure of changing your driver.
Open a command terminal and execute the following command to get the contents of xorg.conf file.
```

$ cat /etc/X11/xorg.conf

```

S

---

### Post by Mustard on 2006-03-31
I'm in agreement with, sn123.  Set up the 'vesa' drivers using sudo dpkg-reconfigure xserver-xorg.  Pick a resolution that works.  Show us your current xorg.conf.  Then when you've got a resolution that is workable, you can have a look over these two links below on setting up your ATI card to work.

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) 

or

[http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)

For now I think you just need any resolution that works and allows you to go through the process of learning how to install better ATI drivers.

---

### Post by SamSlater on 2006-04-01
Thanks guys.

I've got a 1024x768 res @ 61Hz refresh working ok and got my the contents of my xorg.conf file here:

> ubuntu@ubuntu:~$ cat /etc/X11/xorg.conf
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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X800 (R430 UO)"
        Driver          "vesa"
        BusID           "PCI:5:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon X800 (R430 UO)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
ubuntu@ubuntu:~$

Remember this is only a 'live cd' and learning as much as I can before installing for proper. I will mainly use Ubuntu for web browsing, e-mail, instant messaging and downloading/listening to music and updating my iPods.

I'm a budding photographer and once I'm confident with Ubuntu I want to start editing my pics using 'the gimp' so I'll not need another windows again apart from the odd game!

SamSlater.

---

### Post by Mustard on 2006-04-01
Heh..I keep forgetting it's a live CD. :)

So what resolutions have you got functioning atm?

---

### Post by SamSlater on 2006-04-01
At the moment I've got 1024x768, 800x600 and 640x480 which all run at 61Hz and they all work fine. These resolutions are the only ones that work which I chose during set up. 

Other resolutions either don't work at all and I get sent to a command promt with 'error' or I get to the desktop but it's totally messed up and I can only see the top half of the desktop.

---

### Post by Mustard on 2006-04-01
I'm thinking that these are going to be only resolutions you will be able to use via the live CD, while you are running vesa drivers.  I could be wrong though.  This link below shows a tutorial on how to muck around with resolutios and refresh rates..

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by SamSlater on 2006-04-01
It looks like I can't install the ATI drivers when I'm using the 'Live CD' version.

Can I install Ubuntu on my free HD, use that HD as the first HD and install grub on the first sector of a /boot partition? I just don't feel like overwriting my 'mbr' just yet until I feel I'm fairly confident with Ubuntu.

Will this then boot up 'grub' and give me the choice of OS's and boot up Ubuntu from the hard disk without needing a bootable floppy? (have no floppy drive).

Thanks,

SamSlater

---

### Post by Mustard on 2006-04-01
I'm not sure what the installer does if you don't choose 'install Grub to the MBR'.  I've never tried it. :)  Quite a few linux distros that I have tried give you the option to not install Grub on the MBR, but to install in on the partition that linux is on.  I'd be curious what happens if you say no to installing Grub on the MBR with Ubuntu, so tell me how you go. :)

There is a neat little utility you can get hold of though that might let you work around the problem, called Super Grub Disk.  I would give it a try and see if you can avoid installing Grub on the MBR and use this utility to start up your Ubuntu installation.

[http://freshmeat.net/projects/supergrub/?branch_id=62132&release_id=219714](http://freshmeat.net/projects/supergrub/?branch_id=62132&release_id=219714)

It can be used on a CD or a floppy disk.  I couldn't find any instructions on how to write the .img file for the floppy disk on the website for Super Grub Disk, but I worked it out in the end by googling around a bit.  Making a Super Grub Disk CD is much easier than the floppy disk version.

There are possibly many ways to go about this.  Another method I could think of, would be to physically disconnect the first hard drive and just have the second drive going when you install and install Grub to the MBR on your second hard drive (you might need to fiddle with jumpers on the back at this stage to make the second disk the 'master' temporarily, I'm not sure).  Then you could connect up the first drive again (making it master again with jumpers if that was changed earlier), and then using the Boot options from the BIOS screen to decide which drive you want to boot first.  Sometimes you can press a key at the startup screen to choose boot order without going into bios.

I'm sure there are more solutions too.  I recently tried the Super Grub Disk solution at my brothers place, where I he is not so keen on me using his MBR for grub on one of his XP machines.  So I ended up installing Kanotix on a 30 gig partition and then using Super Grub Disk to find Grub installed on the partition so I could boot Kanotix up.

---

### Post by Mustard on 2006-04-01
Do you have your XP disk handy?  If you have that, fixing the MBR if something goes wrong is a pretty simple process I believe.  I think you start up the XP disk, go to 'rescue mode' or 'repair mode' or something like that, and then in the console you type fixmbr.  This basically writes over the top of Grub in the MBR, so at that stage, Ubuntu would not have Grub to boot anymore.  I understand your reticence to install Grub on the MBR, but it would certainly make life easier in terms of getting linux going on a dual boot system.  I'm surprised there isnt an option to boot Ubuntu from a floppy actually.

I'd just mention this, although its probably not relevant to your setup. Windows XP will insist on being on the 'master' in the first partition.  Grub can trick Windows XP into thinking its on the master if you put it on a secondary drive.  Your XP is on the first hard drive already, so as I say its not really relevant.  Just something you might want to know. :)

---

### Post by SamSlater on 2006-04-01
Cheers m8,

I found this page: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall)

3/4's of the way down it mentions:
> 
Another example is when you have a separate boot partition which is mounted at /boot. Since GRUB is a boot loader, it doesn't know anything about mountpoints at all. Thus, you need to run grub-install like this:

     # grub-install --root-directory=/boot /dev/hda

Does this sound like what I'm looking for?

SamSlater

---

### Post by Mustard on 2006-04-01
[QUOTE=SamSlater]Cheers m8,

I found this page: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall)

3/4's of the way down it mentions:


Does this sound like what I'm looking for?

SamSlater[/QUOTE]

It certainly looks like it could be helpful at some stage. :)  I haven't been to succesful with installing grub manually myself.  I usually try to get some utitility that will do it for me, or let the installer do it.  You might have more luck than me.  Apparently its 'easy'. Emphasis on quotes around easy.  For me it's never been 'easy', but I think I just have trouble understanding it, whereas others seem to 'get it' straight away.

---

### Post by SamSlater on 2006-04-01
Well since I'm living In th UK, since I've backed up my important stuff in XP onto DVD's, since I'm kinda an F1 fan, and since the GP's in Melbourne, It starts at 5am our time so I have 5 1/2 hours to try!

If it's possible then I guess you can re-install XP as many times as you want and Grubs boot loader can't be wiped clean!

I'm definately diving in at the deepend here, lets see if I get my fingers burnt! :)

I'll keep you informed how it turns out.

SamSlater

---

### Post by Mustard on 2006-04-01
[QUOTE=SamSlater]Well since I'm living In th UK, since I've backed up my important stuff in XP onto DVD's, since I'm kinda an F1 fan, and since the GP's in Melbourne, It starts at 5am our time so I have 5 1/2 hours to try!

If it's possible then I guess you can re-install XP as many times as you want and Grubs boot loader can't be wiped clean!

I'm definately diving in at the deepend here, lets see if I get my fingers burnt! :)

I'll keep you informed how it turns out.

SamSlater[/QUOTE]

Good luck. :)  44 minutes since you posted.  I guess you are probably near completion by now.

---

