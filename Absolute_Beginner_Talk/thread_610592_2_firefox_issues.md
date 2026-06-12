---
title: "2 firefox issues"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by shplog on 2007-11-12
1) Everytime I watch a youtube (or google.video ect.) firefox freezes up after the video is done.  My cpu graph says that everything is fine, but firefox won't close, or do anything.  I then reboot.  

2) I've noticed that the resolution in youtube vids (and the web in general) is higher than it was when I used Internet Explorer.  I've searched through options on the firefox toolbar because I want to lower the resolution, or clarity because I only have 128mb ram.  I haven't found any options.

Thx in advance!

---

### Post by shplog on 2007-11-12
For a temporary fix, so that I don't have to reboot whenever I have this problem, what would be the command line in Terminal to stop firefox?

---

### Post by kpkeerthi on 2007-11-12
killall firefox-bin

or

killall firefox

or

Press Alt+F2 and then type xkill and press <enter> and click on firefox window

---

### Post by alienexplorers on 2007-11-12
As for the lockups, are you running the latest version of Flash.  I found with older versions I had lockups.  After putting on the newest version the majority of lockups went away.  This is not to say all lockups are gone, but they are not as bad as they were before.

---

### Post by adam.tropics on 2007-11-12
> **kpkeerthi said:**
> killall firefox-bin

or

killall firefox

or

Press Alt+F2 and then type xkill and press <enter> and click on firefox window

...or add the 'Force Quit' applet to your gnome-panel. When you click on it, it allows you to click on whatever window you want closed, et voila!

(right click on a space in panel, Add to panel, Force Quit)

---

### Post by dondad on 2007-11-12
> **adam.tropics said:**
> ...or add the 'Force Quit' applet to your gnome-panel. When you click on it, it allows you to click on whatever window you want closed, et voila!

(right click on a space in panel, Add to panel, Force Quit)

You can also go to the system monitor , select the processes tab and either end task or kill all of the firefox instances you find there. I find that once in awhile, I will get a situation where I try to open FF and it will tell me that there is another instance already open, but it doesn't show anywhere. going to system monitor and killing the instances of FF fixes it.

---

### Post by philinux on 2007-11-12
Even if you fix this you still need more ram urgently.

---

### Post by akadruid on 2007-11-12
Try running firefox from a terminal, that way when it crashes it might give you a message in the terminal that might help?  Also then you can stop firefox by doing ctrl-c in the terminal.

I have a laptop running Ubuntu 6.06 with 128mb and I find it works but its pretty slow.  Might be worth trying Opera instead of Firefox?

---

