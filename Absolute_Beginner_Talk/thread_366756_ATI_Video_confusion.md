---
title: "ATI Video confusion"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by freebird54 on 2007-02-21
I am having lots of fun trying to get ubuntu to take over all my computing needs, but video is causing some of my hair to fall out.

I have 2 different installs of ubuntu on the go, with completely different results, both wrong, on the 2 setups.

This setup, i have the fglrx drivers installed (according to fglrxinfo) with this output
freebird@roost:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)

and

freebird@roost:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1745 frames in 5.0 seconds = 349.000 FPS
1789 frames in 5.0 seconds = 357.800 FPS
1792 frames in 5.0 seconds = 358.400 FPS
1789 frames in 5.0 seconds = 357.800 FPS
1791 frames in 5.0 seconds = 358.200 FPS

which is just fine - BUT - I cannot get any resolution higher than 1260x1024, nor a refresh rate higher than 60Hz.  The entries in the /etc/X11/xorg.conf are NOT reflected in the System->Preferences->Screen Resolution choices, and rarely change at all when changes are made in the conf file.  Where DOES it get its information?

Changes in the xorg.conf file, incidentally include try dpkg-reconfigure attempts.  On exit, it reports that no changes were written to file X - because it thinks that it was already modified - and I can't find a -force option that overrides this behaviour.


The OTHER system is stranger yet.  I have the xorg.conf file agreeing with the System->Prefs entries (and correct - running 1280x1024 @ 85Hz) - but fglrxonfo reports MESA drivers, and of course fgl_glxgears won't run.

Anyone know how to get one or the other to combine these attributes so I can get some work done? (and maybe play with Beryl, too:).   Thanks from another newbie...

freebird54

---

### Post by tgalati4 on 2007-02-22
Are these laptops?  What resolution are you trying to achieve?  Did you manually edit the xorg.conf file and include the highest desired resolution?
Did you reboot and see if this new resolution took hold.  Sometimes removing all lower resolutions is required to force a resolution.  Keep a live CD handy because it will either work or drop you to a console.  You will then have to copy back the original xorg file.  Make backups of xorg.conf before you edit.


You didn't mention what disto you installed.  For a beginner, you should start with 6.06.1 Dapper Drake LTS.  This way you get the feel of how Ubuntu works as a basic system.  Debugging video is easier under Dapper.  Edgy is a moving target so graphics will be more of a reliability issue.

If you can get your 3D graphics to work properly under Dapper then you will have better luck with Edgy and Feisty.  If you start with Feisty then you may end up pulling your hair out.  

Dapper has the biggest base and therefore the best resource to get video to work properly.  Once you have mastered Dapper then you can move on.

---

### Post by freebird54 on 2007-02-22
Sorry - not enough detail :)

AMD Tbird 1GHz, 512Mb RAM, 150Gb Drive, 40Gb Drive ATI Radeon 9550.  The 2 setups are on the 2 different drives - and 2 different tries to get Edgy to work.  I've been banging on PCs since before they had hard drives (anyone remember debug - g=c800:5  to format a 5 Mb HD?)

Found I had missed 1 trouble-shooting tip in the BinaryDriverHowTo - about blacklisting ati-agp - and that got the proper resolution version going with fglrx drivers.

I still don't understand why the preferences was getting its info from somewhere else though.. it even threw in resolutions that I never use (1152xsomething).

I normally like to run 1600x1200, but my eyes tell me that 1280x1024 makes more sense now... :)

Thanks for the help

freebird54

---

