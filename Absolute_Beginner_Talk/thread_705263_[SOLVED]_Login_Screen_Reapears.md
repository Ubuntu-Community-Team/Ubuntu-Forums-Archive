---
title: "[SOLVED] Login Screen Reapears"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by skozzy on 2008-02-23
I'm not sure what has happed to my new install of ubuntu, but after a good install and a 450mb updates I setup my screen (Nvidia 7600GT with a BenQ 22inch wide screen), I got that done then changed my Firefox over to the 32 bit version from the 64 bit version so I could get sun java working for one of my online games. Setup some other software and left it on/running for a day or so.

Tonight I turn the computer off and go out. I come home, power up the computer, boot Ubuntu, it asks for my username and password, then screen blanks, displays a few line of stuff with [OK] after it then jumps back to the login sceeen. After 6 or so attempts to log in I get a text based screen apear saying something about the display failing 6 times.

I have no idea what to do apart for formatting it again and reinstalling it all. This would be annoying as I have done this nearly everday during the week only to find I couldn't install Ubuntu when I have any drives plugged into my SATA ports.

I can't quite offer much explaination to the messages on the screen at the boot time as it flashes up too fast then blanks out.

I can still boot my Windows XP (thats what im using now). Ubuntu Intel version on my laptop worked first time and is still working great, my desptop (this computer) is an AMD and I installed the AMD version. Its about the 10th install on this computer since last weekend. Few days ago I found all my problem trying to get it installed was something to do with my SATA drives, when I unplgged them the install went fine.

This computer is an AMD 3800+ Dual Core socket 939, 1gig of ram, and untill the unbuto install was 8 hard drives (2 on the main IDE) 3 on a PCI IDE Card and 3 on SATA and 1 DVD Burner and 1 DVD Rom. The main board is an Asus, Video is Nvidia 7600 GT 256mb.

Can someone throw some idea how to debug this install and why I can't get to the main desktop screen. If not I will probably give up on Ubuntu on this computer and just stick to using it on the laptop only.

---

### Post by ajgreeny on 2008-02-23
I suspect that you will need to reinstall the nvidia driver.  If you installed the proprietary driver first then did the 450 MB updates, my guess is that a new kernel was included in the updates which will need the driver installation again.  I don't have or need proprietary drivers, but I believe this is a constant problem with kernel updates and nvidia drivers.

So after booting use Ctrl+Alt+F1 to get a console and login.  Then use sudo dpkg-reconfigure xserver-xorg and chose the appropriate driver for your card (nv or vesa?) then when you have at least got a gui you can reinstall the restricted proprietary driver again.

---

### Post by skozzy on 2008-02-23
I will reboot it soon and try what you suggested. At the moment what I found I could do to log in was select the OPTIONS link on the bottom left of the login screen, change the login session to failsafe gnome and my desktop would apear. To get my network start I had to disable and re-enable it and now I can use it to reply (as I am doing now)

The screen resolution is correct, 1680x1050 but the nice looking video effects are not enabled. I looked at the list of drivers being used for my video and its gone back to what looks like is a default nvidia driver. I might tinker about with the drivers and see what happens.

But apart from this. How and where do I find the startup scripts?, as this failsafe gnome said it is starting without the scripts. So maybe something in these scripts is worth me looking at if anything looks out of place.

As for the updates.. I install a fresh ubuntu, waitied till the system detected the updates then run the updates. after a reboot I setup the screen and video card. The only software I installed was Firefox32, Sun Java, Xchat for IRC, File Zilla for FTP and Mplayer. After that I enabled the extra GFX Effects for the Desktop. So it's still a mostly fresh setup.

---

### Post by skozzy on 2008-02-23
ajgreeny looks like your advice worked. I can now log in after reselecting the driver for the video card

I had originaly selected the 7 series driver, but this time I selected the FX series driver. Rebooted and logged in normaly.

Thanks mate.

---

