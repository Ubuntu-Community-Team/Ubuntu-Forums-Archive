---
title: "Kubuntu screen problem live CD? Menus and Fonts gigantic cannot navigate."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by esteckis on 2007-12-04
Total newbie here.  Hello everyone. I wanted to give Kubuntu a shot ( I want to get more eye candy). I have tried the live cd of Ubuntu Gutsy  in 32 and 64 bit architecture no problem there. The problem I am having with Kubuntu in both flavores 32 or 64 is this.  I run the live cd and Kubuntu loads no problem. But what happens is the bottom taskbar seems an ok size but the clock font size spans 5 inches across the screen. The far left button if I click on it, a menu opens up full screen and the fonts are like 2 inches big and it lists only 4 items (I am sure there are more items listed but I cannot scroll down ) I am trying to locate how to define font size/what my screen resolution is. But because the menus are so big I cannot move the cursor fast enough to try to locate where the  configuration options are. I have also tried running the live CD in safe mode with the same problem.

Where do I navigate to set screen resolution or font size?  :confused:

Thanks for your help

---

### Post by khurrum1990 on 2007-12-04
Hi, open up a konsole in Kubuntu and type in:
"sudo dpkg-reconfigure xserver-xorg"
Now I suggest u try the vesa driver and set a resolution u like. After configuring xserver press:
Ctrl+Alt+Backspace
Now it should be ok.
Good Luck!

---

### Post by ARhere on 2007-12-04
Sounds like Kubuntu does not like your video card, odd that Ubuntu live worked fine though.

If you are trying to install it, just use the alt-install CD for Kubuntu.  That way, when the screen comes up like that again, you can modify the xorg.conf file and restart X.

I don't know if this will work in a live session, but when you get KDE up, hit CTRL+ALT+F2.  this will switch to a terminal.  Modify xorg.conf to show a better resolution and/or correct the detected monitor.  Save xorg.conf and restart X with CTRL+ALT+Backspace.

Sorry I was not more specific, but never tried to edit files on a live session so I am not sure that will work.

-ARhere

---

### Post by ARhere on 2007-12-04
> **khurrum1990 said:**
> Hi, open up a konsole in Kubuntu and type in:
"sudo dpkg-reconfigure xserver-xorg"

He booted up with the live CD so wouldn't the video setting be the same, which don't work?  Not being a smart @ss, just curious.

-AR

---

### Post by esteckis on 2007-12-05
Thanks for the help but I could not configure it.  But the Ubuntu Gutsy 64 bit runs ok using the flgx driver, now I was also able to download and install the ATI driver under Ubuntu Gutsy 64 bit, the only problem was that since I was using 64 bit, There is a known problem with the ATI driver and the gnome acpi?. If an   opengl screensaver started running, the screen would go blank and I would bet a very fast line item saying battery error something and Ubuntu would reboot from scratch. What is strange is that my computer is a plugged in desktop (not a laptop) lol.  So here is my proposal:

If I reinstall Ubuntu Gutsy i386 (not 64 bit) then allow the flgx driver for the ati video can I then switch over to KDE per this webpage [http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

Will that give me a basic Kubuntu with also the video designation staying the flgx?

Thanks again for your help.  :)

---

### Post by esteckis on 2007-12-05
OK, scratch the above idea of trying Ubuntu gutsy with Gnome and then switching over to KDE. I tried it, and the logon screen was doing the same thing as Kubuntu. I was able to log on and then at the main screen it corrected itself. But I don't want to chance it.

---

