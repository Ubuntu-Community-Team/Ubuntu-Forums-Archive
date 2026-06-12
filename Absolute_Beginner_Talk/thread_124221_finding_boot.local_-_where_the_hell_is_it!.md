---
title: "finding boot.local - where the hell is it!?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by sniffass on 2006-02-01
I'm trying to enter a line of text into the boot.local file but I cannot find it in /etc/rc.d or /etc/init.d  where is this file to be found on ubuntu?
Also is there some kind of a search system available so I can invoke a search botx and search for any file on my pc?

Regards
 Gabe

---

### Post by annsachd on 2006-02-05
You can open terminal, cd to the folder and ls for a list of files.

cd /etc/init.d

then

ls

Also, you can search from the menu by going to Places -> Search for Files.

---

### Post by sniffass on 2006-02-10
Well in my kubuntu there is no file called boot.local in /etc/init.d and I think I said that in my original post. I actually made a file called such and entered my desired data but to no avail. Like I said i can't see a boot.local file in either rc.d or init.d.
I need to add "/usr/bin/915resolution 38 1280 800 24"
So that when I restart my computer the correct resolution is loaded before x starts.

---

### Post by bscbrit on 2006-02-10
Is there a particular reason why you want to take this approach, rather than edit /etc/X11/xorg.conf which should do precisely what you want?

It sounds a bit like you a following a set of instructions or a guide for some other flavour of linux?

---

### Post by sniffass on 2006-02-10
quite so. I am newbie at this kind of thing that's why i'm posting in this forum. The 915resolution fixes  the display problem on computers with mine or a similar graphics card (the video bios needs to be hacked). The readme says to put the line in boot.local, and this is what i did with both suse and mandrake. I had no idea ubuntu lacked this file and no idea that i can put the said code into xorgconf or whatever. Thank you so much for pointing this out - i will be sure to try it!

---

### Post by bscbrit on 2006-02-10
Well my advice is good for setting the screen resolution but I'm not sure that it amounts to hacking the video bios.  

Which video card is this that needs hacking before it will work?  I'm not suggesting that you are wrong but I have simply never heard of it (which isn't too surprising).  I am aware, of course, of the 915 chipset but I wasn't aware that there was/is a major problem with some of the boards that use it.  

However, as a result of this thread I have carried out a search for '915' using the search facility in this forum.  There are several other threads of interest that you might want to read as they will show you how others have fared with this particular chipset. You will also be able to ask other users about your problems - they will undoubtedly know much more than I do!

Good Luck

---

### Post by bscbrit on 2006-02-10
These threads in particular seem to answer you question:

[http://www.ubuntuforums.org/showthread.php?t=124831&highlight=915](http://www.ubuntuforums.org/showthread.php?t=124831&highlight=915)

[http://www.ubuntuforums.org/showthread.php?t=93416&highlight=915](http://www.ubuntuforums.org/showthread.php?t=93416&highlight=915)

Well, I've learned something today...... :-D

---

### Post by sniffass on 2006-02-10
this is the readme from 915resolution:
> 915resolution
=============

This software changes the resolution of an available vbios mode.

It patches only the RAM version of the video bios so the new resolution
is loose each time you reboot. If you want to set the resolution each
time you reboot and before to launch X, use your rc.local, local.start ...
file of your Linux version.

Versions 0.3 and later also supports the 845, 855, and 865 chipsets.

Usage
-----

You must be root to launch it.

  Usage: 915resolution [-l] [mode X Y] [bits/pixel]
  Options:
      -l display the modes found into the vbios

  Note that bits per pixel is optional.  If you do specify anything,
  then the original value will be preserved.


Installing
----------

$ make
$ su
# make install

Setting
-------

    1.  Switch to root
       # su

    2. Display the available resolutions :

        # 915resolution -l
        Intel 800/900 Series VBIOS Hack : version 0.4.8

        Chipset: 915GM
        BIOS: TYPE 1
        Mode Table Offset: $C0000 + $269
        Mode Table Entries: 36
        Mode Table Offset: $C0000 + $269
        Mode Table Entries: 36

        Mode 30 : 640x480, 8 bits/pixel
        Mode 32 : 800x600, 8 bits/pixel
        Mode 34 : 1024x768, 8 bits/pixel
        Mode 38 : 1280x1024, 8 bits/pixel
        Mode 3a : 1600x1200, 8 bits/pixel
        Mode 3c : 1920x1440, 8 bits/pixel
        Mode 41 : 640x480, 16 bits/pixel
        Mode 43 : 800x600, 16 bits/pixel
        Mode 45 : 1024x768, 16 bits/pixel
        Mode 49 : 1280x1024, 16 bits/pixel
        Mode 4b : 1600x1200, 16 bits/pixel
        Mode 4d : 1920x1440, 16 bits/pixel
        Mode 50 : 640x480, 32 bits/pixel
        Mode 52 : 800x600, 32 bits/pixel
        Mode 54 : 1024x768, 32 bits/pixel
        Mode 58 : 1280x1024, 32 bits/pixel
        Mode 5a : 1600x1200, 32 bits/pixel
        Mode 5c : 1920x1440, 32 bits/pixel
        Mode 60 : 1280x770, 8 bits/pixel
        Mode 61 : 1280x770, 16 bits/pixel
        Mode 62 : 1280x770, 32 bits/pixel
        Mode 63 : 512x771, 8 bits/pixel
        Mode 64 : 512x771, 16 bits/pixel
        Mode 65 : 512x771, 32 bits/pixel

    3. I personnaly decided to overwrite the 1280x1024 resolution
       because I don't use it :

        # 915resolution 38 1280 800

    4. Now the bios reports a 1280x800 resolution :

        # 915resolution -l
        Intel 800/900 Series VBIOS Hack : version 0.4.8

        Chipset: 915GM
        BIOS: TYPE 1
        Mode Table Offset: $C0000 + $269
        Mode Table Entries: 36
        Mode Table Offset: $C0000 + $269
        Mode Table Entries: 36

        Mode 30 : 640x480, 8 bits/pixel
        Mode 32 : 800x600, 8 bits/pixel
        Mode 34 : 1024x768, 8 bits/pixel
        Mode 38 : 1280x800, 8 bits/pixel
        Mode 3a : 1600x1200, 8 bits/pixel
        Mode 3c : 1920x1440, 8 bits/pixel
        Mode 41 : 640x480, 16 bits/pixel
        Mode 43 : 800x600, 16 bits/pixel
        Mode 45 : 1024x768, 16 bits/pixel
        Mode 49 : 1280x800, 16 bits/pixel
        Mode 4b : 1600x1200, 16 bits/pixel
        Mode 4d : 1920x1440, 16 bits/pixel
        Mode 50 : 640x480, 32 bits/pixel
        Mode 52 : 800x600, 32 bits/pixel
        Mode 54 : 1024x768, 32 bits/pixel
        Mode 58 : 1280x800, 32 bits/pixel
        Mode 5a : 1600x1200, 32 bits/pixel
        Mode 5c : 1920x1440, 32 bits/pixel
        Mode 60 : 1280x770, 8 bits/pixel
        Mode 61 : 1280x770, 16 bits/pixel
        Mode 62 : 1280x770, 32 bits/pixel
        Mode 63 : 512x771, 8 bits/pixel
        Mode 64 : 512x771, 16 bits/pixel
        Mode 65 : 512x771, 32 bits/pixel

    5.  On some machines 24 bits per pixel is the desired resolution.  
        An alternate invocation to achieve this would be:

        # 915resolution 38 1280 800 24

    6. My xorg.conf has the following screen definition :

        Section "Screen"
          Identifier  "Screen 1"
          Device      "device"
          Monitor     "LCD"
          DefaultDepth 16

          Subsection "Display"
            Depth       16
            Modes       "1280x800"
          EndSubsection
        EndSection

    7. 915resolution must run before the X server is started.  So I don't need to
         do this every time I put it in my startup scripts.  Where these scripts 
         are very from distribution to distribution.  I'm running SUSE 9.2, so I 
         put the definition in /etc/init.d/boot.local:

        #! /bin/sh
        #
        # Copyright (c) 2002 SuSE Linux AG Nuernberg, Germany.  All rights reserved.
        #
        # Author: Werner Fink <werner@suse.de>, 1996
        #         Burchard Steinbild, 1996
        #
        # /etc/init.d/boot.local
        #
        # script with local commands to be executed from init on system startup
        #
        # Here you should add things, that should happen directly after booting
        # before we're going to the first run level.
        #

        /usr/bin/915resolution 38 1280 800        
       
     8.  Start up the X server
        # startx


Disclaimer
----------

915resolution is free to use, distribute or modify. But please mention
my name and the names of the respective contributors.
I tried to make the programs as safe as possible but obviously I can't
guarantee that they'll work for you. So don't blame me if something bad
happens.

                                          Steve Tomljenovic
                                          stomljen at yahoo dot com



---

### Post by bscbrit on 2006-02-11
See my post #7.

---

### Post by mycroft on 2006-04-12
I have an Intel 915 graphics card and a 1280x800 display too. I have found this approach to work quite well for me:

Run 'dpkg-reconfigure xserver-xorg'.
At one point durings the setup proces, you will be asked to set the maximum resolution for your monitor - choose a resolution slightly above what you know to be your max, 1280x960 for instance. 

Later you will be asked to select which resolutions you want to be able to choose from in when changing resolutions. Provided you don't plan to use lower resolutions, the easiest choice is to simply deselect everything but your max. resolution.

Complete the setup process, restart X (Ctrl-Alt-Backspace), and you should be looking at things in a crisp 1280x800 resolution.

---

