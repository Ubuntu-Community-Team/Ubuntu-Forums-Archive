---
title: "Unable to install Ubuntu 6.06 due to the resolution being stuck at 640x480"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by DigitalDaiquiri on 2006-10-03
Hello, I would like to start off by by introducing myself, and stating that I'm am 100% new to Linux. I am excited about learning more about this amazing operating system, as well as joining the Ubuntu community. I have primarily been a Windows user, although I'm no stranger to OSX (I'm currently typing this on a Mac). Although I have quite a bit of experience with both XP and OSX, I have little to no experience using the command prompt on either platform. I only know a few basic DOS commands.

When attempting to install Ubuntu 6.06 Dapper Drake off of a live CD I stumbled into a resolution problem. The resolution on the live CD seemed to be stuck at 640x480, with the drop down box under 'System>Preferences>Screen Resolution Preferences' lacking any other choice. The refresh rate appeared the same way, staying at a constant 60 Hz. I assumed that this was because the live CD might have lacked the video drivers compatible with my ATI Radeon 9500 Pro. I restarted and tried to change the resolution before booting into the live CD within the boot menu.**Although the boot process was affected by the resolution change, the live CD environment was not. After going through a terribly painful process of pressing tab in order to access buttons found in the installation that were inaccessible due to them being off of the screen, I finally got Ubuntu installed (in a separate partition next to my Windows XP Media Center Edition 2005 partition). I then went online in order to download "Easy Ubuntu" (after reading on Digg.com that it was an easy solution for beginners looking for official ATI drivers), and began to install it. I'm on a college campus and have to manually connect to the network, but I forgot to connect before installing. In response to the lack of a connection, I received an error message from "Easy Ubuntu". I connected to the Internet and went to reinstall it only to come across the following error: "Could not apply changes! Fix broken packages first.". At this point I am entirely out of ideas. I was wondering if anyone out there knew how I could fix this problem. Thanks for the help.

---

### Post by harry555 on 2006-10-03
When you use the live CD is there any option to do a text install?   This would be about the third option on the first screen you see after booting up.
I too am new to Ubuntu.  I used the text install option as the live DVD seemed sluggish on my ageing Duron system.

Doing a text install might not solve your problem but if you have an hour or so to spare it's worth a go.

---

### Post by Bachstelze on 2006-10-03
As always, "use the Alternate CD".

Stupid idea of Ubuntu's devellopers', those "Desktop CDs". They never ever work...

---

### Post by bigken on 2006-10-03
you could just done the install then in a terminal type dpkg-reconfigure xserver-xorg and manually select your video driver and screen resolutions by using the space bar ;)

---

### Post by tribaal on 2006-10-03
> you could just done the install then in a terminal type dpkg-reconfigure xserver-xorg and manually select your video driver and screen resolutions by using the space bar

In other words, you can follow [this howto]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

- trib'

---

### Post by Tom Amos on 2006-10-03
I had the same problem during install. I found that, instead of blindly tabbing around trying to get to the next menu, you can hold ALT, click and hold anywhere in the window, and drag the window around with the mouse. It doesn't matter then if the menu doesn't fit the screen, you can drag it up off screen until the menu buttons on the bottom show.


-Tom

---

### Post by mixmaster on 2006-10-03
Yeah, I've had this problem trying to install onto an ATI powered box.  On nVidia you can get up to 1024x756 resolution.

Strangely, I've found that the resolution that the live CD runs at is sometimes affected by how you boot it.  With an nVidia based system booting with the CD in the drive will give you 1024x756 max, but rebooting from an existing running system at higher res will sometimes allow you to run at that resolution (I have a 1920x1200 monitor and rebooting from windows gives me 1600x1200 running in the middle of the monitor, not stretched to size).  I've not tried this with an ATI card but it might be worth a go.

Failing that, the text-mode installer is not intimidating although downloading and burning the CD is a bit of a pain.

---

### Post by DigitalDaiquiri on 2006-10-03
I really appreciate the quick response from everyone, and all of the suggestions.  Thank you bigken for the idea of manually running the Autodetect script, and triball for linking me to a walk through.  I would also like to thank Tom Amos for pointing out the keyboard command for being able to click within the middle of a window in order to move it.  Unfortunately neither the Autodetect script nor running 'sudo aticonfig' as suggested in the "Ubuntu Community Documentation" seemed to solve my problem.  Actually after typing 'sudo aticonfig', other than being prompted to type in my password, I receive a "command not found" error.  Is it possible that I need to download and install an ATI driver packet, or that I am not using the command prompt correctly in order to run the 'aticonfig' command? 

[SIZE="1"]*mixmaster, I was indeed able to complete the install, but after rebooting naively from the HDD I still have the resolution error[/SIZE]

---

### Post by bigken on 2006-10-03
did select ati as driver when you ran the dpkg-reconfigure xserver-xorg

---

### Post by bodhi.zazen on 2006-10-03
Try this:

[Bodhi's Monitor How-to](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

If that does not work, Monitor and videocard ?

---

### Post by epistemaniac on 2006-10-03
thanks for starting this thread... I am a TOTAL newbie to linux and nearly gave up on trying this OS out because of the very problems you describe so well in the OP... I figured it was a matter of a lack of geekiness on my part and I was somewhat embarrassed to ask about this problem.... glad you did!!!

I have started to go through the howto... but unfortunately I have a very obscure monitor it seems.... its a shamrock C509 d and I cannot find the info it appears I need in order to resolve this problem... this may be stupid to say... but I have the same problem with the install of both ubuntu (I was sent the cd's in the mail) and kbuntu (dnloaded iso)... eventually I was able to do a complete install of kbuntu in hopes that it was just the live cd that was causing me problems such that I could see only a fraction of the top of the button I needed to click to get through the installation... but no... the problem is still with me... when I go to system stettings/monitor the "normal" box is selected at 640/480 and all other choices are greyed out.... so I guess this means that the install did not recognize the monitor... does this mean that its back to windows until I can afford another monitor?

---

### Post by bodhi.zazen on 2006-10-03
> **epistemaniac said:**
> thanks for starting this thread... I am a TOTAL newbie to linux and nearly gave up on trying this OS out because of the very problems you describe so well in the OP... I figured it was a matter of a lack of geekiness on my part and I was somewhat embarrassed to ask about this problem.... glad you did!!!

I have started to go through the howto... but unfortunately I have a very obscure monitor it seems.... its a shamrock C509 d and I cannot find the info it appears I need in order to resolve this problem... this may be stupid to say... but I have the same problem with the install of both ubuntu (I was sent the cd's in the mail) and kbuntu (dnloaded iso)... eventually I was able to do a complete install of kbuntu in hopes that it was just the live cd that was causing me problems such that I could see only a fraction of the top of the button I needed to click to get through the installation... but no... the problem is still with me... when I go to system stettings/monitor the "normal" box is selected at 640/480 and all other choices are greyed out.... so I guess this means that the install did not recognize the monitor... does this mean that its back to windows until I can afford another monitor?


[Shamrock specifications](http://www.nix.ru/autocatalog/displays/15_Microvision_C509-D_Shamrock_3264.html)

Use:>     HorizSync   30-57
    VertRefresh 47 - 120

---

### Post by DigitalDaiquiri on 2006-10-03
> **bigken said:**
> did select ati as driver when you ran the dpkg-reconfigure xserver-xorg

Thanks bigken, I finally got it to work.  For some reason the first few times that I tried the "dpkg-reconfigure xserver-xorg" it listed the prompt in the CLI, but after trying it yet again I was able to get it to randomly pull up its GUI.  I went through the prompt and finally was able to change my resolution.  I still have a few questions however.  The first involves the volume, date/time, log off/on, and Trash icons hovering in the middle of both my top and bottom panels.  Before changing the resolution these icons were pushed nicely over to the right of each of their respective panels.  The Trash icon is especially problematic, as it decreases the size of usable space on the task panel.  Is there anyway to keep my new resolution (1024x768 ) without the misplaced icons?  Secondly I am still having trouble trying to install "Easy Ubuntu", as I keep receiving the following error: "Could not apply changes! Fix broken packages first."  I don't even know where to start in relation to fixing the broken packages in order to install it.  Thanks again for the help.

---

### Post by bigken on 2006-10-04
to repair or remove broken packages go to system/administration and select synaptic package manager from there you can remove broken packages I would also try this in a terminal sudo apt-get update then sudo apt-get upgrade ;)


As for the icons have tried to right click and move ?

---

### Post by DigitalDaiquiri on 2006-10-11
Thanks for everything mate, I appreciate all of the good help.  I"m sorry for not knowing to "right click and move" the Panel icons, but I'm slowly learning the basics and I've now got everything to work just fine.  (I apologise for the not so hasty reply, for I'm a college student and had quite the busy week last week.) (^_~)

---

### Post by bigken on 2006-10-11
Hope have loads of fun using ubuntu :D

---

### Post by Tunemonkey on 2006-10-11
I had the same problem. I did this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

and answered all the default questions. Then hold down "cntl, option (alt), and delete" (this is on a Mac Powerbook). 

The screen rebooted, and I had 1152x768. Then, when going to screen resolutions, I could pick different resolutions.

It worked.

T

---

