---
title: "Deleted xorg.conf, also, how do I setup dual monitors or SLI? (Nvidia)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Ruined on 2007-07-05
Hello, decided to switch from windows to Ubuntu and it's a very... strange,,,, experience.

Anyways I'll get right down to it.

Computer:
Dual Geforce 6600GT
AMD Athlon 64 4000
Running hard drive on SATA (with 2 of my hard drives unplugged to install ubuntu)
2 monitors, 24" widescreen hooked up to main graphics card, 16" CRT hooked up to secondary graphics card
Ubuntu x86, 7.04 gnome thingy


Original Problems:
Ubuntu was loading on my main graphics card, then when I got to the login screen and further it would display on my second graphics card and output nothing to the main one.
Also, was low resolution


What I've done (in order):

Updated all my packages that were recommended from a clean install

Ran the restricted drivers manager to update linux nvidia drivers. This didn't fix my original problems and I couldn't find any form of "display properties" equivalent to configure my display outputting.

I then proceeded to download the latest x86 drivers from nvidia's site and try to install them by double clicking on the file, typically what I would do on windows :P (it opened gedit?). (link to driver page [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html))

I had no idea what I was doing and I was reading the install instructions and discovered some xconfig file on that page.

I was fiddling around and found out that I needed root, and to exit X server to install the drivers.
I used the xconfig file to reconfigure my xorg.conf (which created a backup in the same folder 
called xorg.conf.backup

I restarted and display was going through my main graphics card, but wasn't on the right resolution. Half the basic problem solved.

I was browsing through the absolute beginner forum and found a fix for the resolution by doing what was in here [http://ubuntuforums.org/showthread.php?t=493433](http://ubuntuforums.org/showthread.php?t=493433) (except putting the resolutions at 1920x1200 1280x1024 etc

Restarted computer, would show any form of graphics whatsoever.

Thinking I'd fubared my system I decided to see if I could fix it by restoring the backup xorg.conf file.

I entered recovery mode with grub and navigated to /etc/X11/

Remembering the rm command I got rid of xorg.conf but I couldn't figure out what the rename command was, giving up after about 5 minutes of playing around I restarted.
I'm now running at 1920x1200 on my main graphics card

ANYWAYS, I was wondering, what should I do about xorg.conf, also how would I go about setting up dual monitors or SLI.

Oh and another thing, when I go into restricted drivers manager it shows up the nvidia accelerated drivers... they're enabled but "not in use" O_O

---

### Post by PCFascist on 2007-07-05
Try this how-to on Xinerama. Haven't used it in FBSD and it worked good but that was about a year ago. You might want to search for TwinView if you use a nVidia card.
[http://ubuntuforums.org/showthread.php?t=301951&highlight=Xinerama](http://ubuntuforums.org/showthread.php?t=301951&highlight=Xinerama)

---

### Post by Ruined on 2007-07-05
will give it a chop, thanks

---

