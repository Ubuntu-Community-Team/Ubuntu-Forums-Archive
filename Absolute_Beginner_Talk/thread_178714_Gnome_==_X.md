---
title: "Gnome == X ??"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Absolute Zero on 2006-05-18
Hello everyone,
     I jumped on #ubuntu lastnight to seek some direction from the people on there and everyone was quite helpful!  I asked how I could get ubuntu to display deeper resolutions, and one individual said to modify the xorg.conf file and then to restart X.

So I opened up the terminal did ```
sudo gedit /etc/X11/xorg.conf 
``` added my resolution to all 4 lines in the file (each line corrosponded to a different monitor mode?) and then restarted Ubuntu.  I logged back in and my Screen Resolution properties had not changed, it was still only displaying options for 1024x768 800x600 640x480 but I had added 1152x864.

So I guess the question is does GNOME == X? The the question becomes if GNOME isn't X how would I add a new screen resolution to GNOME and also how to start X.  

If GNOME is X can anyone explain why the new resolution did not show up?

---

### Post by Rinzwind on 2006-05-18
X is the server that shows you your desktop envirenment (DE): gnome in your case. So X is not Gnome. X is what starts Gnome (or KDE or any other DE). 


What you could do is type this in console-mode:

**sudo dpkg-reconfigure xserver-xorg**

Press enter for all the questions asked until somewhere at the end it will ask what resolutions should be added. Mark all the ones you want. 

After that you need to restart your PC.

When rebooted you should be able to select the new resolution.
(this is the automated version of editing your xorg.conf file and where you could make crucial typo's this works mosttimes flawlessly (unless you answer  any of the questions asked with bogus answers it should be safe)).

This worked for me a while back :) :

Your xorg.conf should be something like this:
> Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
Monitor "NEC LCD1712"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

---

### Post by 23meg on 2006-05-18
Gnome is your desktop environment, which runs on top of the X window system. See below for definitions of and some info about both:

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

For screen resolution issues, refer to [heimo's guide]("http://ubuntuforums.org/showthread.php?t=83973").

---

### Post by mostwanted on 2006-05-18
[QUOTE=Absolute Zero]Hello everyone,
     I jumped on #ubuntu lastnight to seek some direction from the people on there and everyone was quite helpful!  I asked how I could get ubuntu to display deeper resolutions, and one individual said to modify the xorg.conf file and then to restart X.

So I opened up the terminal did ```
sudo gedit /etc/X11/xorg.conf 
``` added my resolution to all 4 lines in the file (each line corrosponded to a different monitor mode?) and then restarted Ubuntu.  I logged back in and my Screen Resolution properties had not changed, it was still only displaying options for 1024x768 800x600 640x480 but I had added 1152x864.

So I guess the question is does GNOME == X? The the question becomes if GNOME isn't X how would I add a new screen resolution to GNOME and also how to start X.  

If GNOME is X can anyone explain why the new resolution did not show up?[/QUOTE]

Could be a problem with the video driver not detecting all available screen resolutions. I guess you could try installing the official Nvidia/ATI/whatever drivers and see if it helps.

And Gnome is not the same as X. X is the graphics server, it represents the screen as one big canvas. Gnome is a bundle consisting of the Metacity window manager + several setup and behind-the-scenes configuration utilities + a lot of graphical applications made with the toolkit GTK+.

---

### Post by tseliot on 2006-05-18
And remember to press CTRL+ALT+Backspace after you log out to make sure that the Xserver is restarted.

---

