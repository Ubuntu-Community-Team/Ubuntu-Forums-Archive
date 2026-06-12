---
title: "Help. Can't install with 640x480 screen resolution"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by Tunemonkey on 2006-09-25
All,

I'm attempting to install Dapper on my G4 667 Titanium. In Live CD mode, I'm unable to change the screen resolution from 640x480. There is nothing else to choose from in the Ubuntu monitor prefs. 

When I change the xorg.conf to 1152x768 (which is what I would like), getting rid of the other resolutions listed under the "Monitor" section and save and restart, it boots again at 640x480 and the xorg.conf is back to where it was, showing 1024x768, 800x600, and 640x480 resolutions.

I thought that if I could install Ubuntu instead of running off the CD, then perhaps I would be able to change resolutions, but I can't see the whole install screen to make my choices.

What's the easiest way to get the monitor to display my 1152x768?

I've had KDE and Gnome running off and on over the years, but it's been a while, so go easy on me.

T

---

### Post by Gotterdammerung on 2006-09-25
Try Ctrl+Alt+**+** to change resolution.

---

### Post by Tunemonkey on 2006-09-25
Are these all individual keystrokes or combinations?

T

---

### Post by avtolle on 2006-09-25
Since you are running from the "live CD", any changes are not saved to disk, but are in RAM, and thus lost when restarting the system. To see if the changes are effective, instead of restarting the system, at the CLI, after you edit xorg.config, do Alt+ctl+F7 as a combination. To answer your second question, once installed, you may change your resolution by editig the /etc/X11/xorg.conf file, using gedit or other editor of your choice, and saving the changes. HTH.

---

### Post by Tunemonkey on 2006-09-26
Thanks. I'll try that.

T

---

### Post by Tunemonkey on 2006-09-26
When I save, do I then hit cntl+option (alt)+f7 while in the gedit window or do I go back to the terminal?

How does the file save when it's on the install CD?

T

---

### Post by Tunemonkey on 2006-09-26
I did manage to get to the login screen but I'm still stuck at 640x480 at 60 hz.

My xorg.conf remained the way that I edited it, which is 1152x768 for the 6 different pixel depths that were listed, but when I attempt to change the resolution at the Screen Resolution pref, only 640x480 is listed. Additionally, I notice that all the radio buttons in the prefs have lines of dots running through them until I move the cursor over them. Then the dots go away.

Do I need to edit the xorg.conf file differently or perhaps a different driver?
My machine is a Powerbook G4 667 and the "Device" is identified as a Radeon Mobility M6 LY [Radeon Mobility 9000]. The "Monitor" section is Identifier "Generic Monitor" and Option is listed as "DPMS"

Any ideas?

Thanks,

T

---

### Post by meyerfun on 2006-09-26
I don't know if this will work off the live cd, but here is my post on fixing a resolution issue on an iBook.

[http://ubuntuforums.org/showthread.php?t=261241](http://ubuntuforums.org/showthread.php?t=261241)

jm

---

