---
title: "Incorrect screen resolution at logon"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Comco on 2007-11-07
G'day guys,

I work in IT but am admittedly a newbie when it comes to Linux. I have messed around very simply with a couple of different distros over the last couple of years but put it down fairly early on. I found, as someone who knows Windows so well, it was frustrating to be back at the stage where I had no idea how to do simple tasks. (Lame excuse, I know).

Anyways, Ubuntu 7.10 grabbed my interest again and made me want to jump back into learning the ropes.

I currently have Ubuntu running on a virtual machine using VMware. Unfortunately, I am now at a stage where I cannot log back in to the system because the resolution set on the logon screen is incorrect. I am quite literally only seeing the top 1/4 of the screen, and I can't see enough to log in. Can anyone give me a few pointers here?

If I recall correctly, I should be able to sort this out by changing a line or two in the xOrg config files somewhere? Maybe I'm wrong there...

Any help on this would be greatly appreciated.

---

### Post by JohnSGruber on 2007-11-07
I've had a similar problem. It turned out that the Virtual line in the screen section of the xorg.conf file gave a virtual screen size larger than the resolution of my monitor.

If that's the case you should be able to logon by moving your cursor with your mouse to the edges of the screen to scroll around. Often the problem goes away once you log on, but it comes back next time you get the logon screen. You could comment out the line in xorg.conf in /etc/X11 by putting a "#" in the beginning of that line, or you can adjust it to match your monitor's screen resolution.

If your screen's resolution is too small and that is the basic problem it would be handy to see your xorg.conf file and the /var/log/Xorg.0.log file. The latter file contains a line listing each rejected screen resolution and the reason.

Good luck and g'day.

---

