---
title: "Vexing Video"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-20
In my attemps to get my S3 unichrome pro IGP video chipset working in kubuntu I have tried using dkpg-reconfigure xserver-xorg in order to select the higher resolution (my original problem was that I could not select higher than 800x600 in system settings).  Before I get to the part about screen resolution, I go through a bunch of other steps which presumably cause some fatal change because this course of action always ends up in kubuntu booting to a text screen (I have reinstalled 3 times now).  So my questions are:

1)  Is there some way to edit the xconf or xorg file so that I can edit only the part about screen resolution so I don't end up messing up other settings?  I've tried a kate command a while back but that required me to be logged on as "root". (?)

2) What is "xserver", "xorg" & "xconf"  and how do they relate?  One of my problems with all this is that I am a complete newbie and don't understand what these commands mean on a fundamental level.

One other point:  The splash screen (the one with the progress bar) is in perfect resolution, as is the logging off splash screen.  The login screen is pixelated and in poor resolution

Many thanks,
keno

---

### Post by magicfab on 2007-11-20
xserver is the software that drives the graphics ("X"). xorg.conf is the configuration file.

If you go to command line (Applications > Accessories > Terminal) you can issue the following commands to find out more (much more, really) about both:
man xserver
man xorg.conf

To edit the configuration file as "super user" issue this command:
sudo nano /etc/X11/xorg.conf

... then CTRL-X to exit .

Search for a section of that file similar to the following:
        SubSection "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

The line "Modes" specifies the possible resolutions. 

An easier way to have that file generated would be to use:
sudo dpkg-reconfigure xserver-xorg -phigh 
(which is the same that happens at install time, so no need to keep reinstalling)

Removing the -phigh parameter will ask more questions. I would experiment with resolutions around 1024x768 and color depth of 24 or 16 if low on memory.

Unfortunately sometimes it's just trial and error when configuring X, although in Gutsy it is much better than it used to be.

Good luck.

---

