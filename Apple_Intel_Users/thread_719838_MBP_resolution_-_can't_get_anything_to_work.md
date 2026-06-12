---
title: "MBP resolution - can't get anything to work"
date: 2008-03-09
forum: Apple Intel Users
---

### Post by gui3 on 2008-03-09
i know this issue has been asked before but i've done a lot of searching, and i can't seem to find an answer that works on my machine.
i'm also an absolute linux beginner.

i have hardy running in virtualbox on my macbook pro (2nd gen, not the most recent model)

install and update went flawlessly.

i installed virtualbox guest additions and it seemed to go fine.

when i go to preferences --> screen resolution, the max is still 800x600.
when i go to administration --> screen and graphics, its listed as "plug n play" with max res 800x600.
if i change "plug n play" to "LCD Panel 1440x900", nothing happens after reboot.

so, based on info i found on the web, i went into xorg.conf.
under "Screens" **there were no resolutions listed**

i tried coping  a "Display" subsection from someone else's xorg.conf into mine. it looked like this:
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection

when i do that, and reboot, the screen goes nuts and becomes unusable.

i saved a snapshot of the guest OS with updates and guest stuff installed and before any monkeying with the xorg.conf.

what should i do now?

---

### Post by cyberdork33 on 2008-03-09
Try posting in the[ Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum

---

### Post by zxcv501 on 2008-03-17
gui3, I had the same problem with my MBP.  I've got the 17" so my native resolution is 1680x1050.  Here's what I did to get my Ubuntu 7.10 virtual box to run at 1680x1050 (YMMV):

 - I added my resolutions to the xorg.conf file (just like you did)
 - I installed the Virtual Box additions (took me forever to find this, not sure if it's hidden while the server is running or in full screen mode)
 - restarted 
 - went into screens and graphics and chose the LCD 1680x1050, and I checked the box for widescreen display
 - After that I could select 1680x1050 as a screen resolution

hope this helps,
Jared

---

