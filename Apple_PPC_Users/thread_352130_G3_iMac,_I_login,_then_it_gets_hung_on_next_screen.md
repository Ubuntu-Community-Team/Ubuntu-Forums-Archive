---
title: "G3 iMac, I login, then it gets hung on next screen..."
date: 2007-02-02
forum: Apple PPC Users
---

### Post by humboldthead on 2007-02-02
HI, I installed Ubuntu from the alternative disk, (and after watching the Ubuntu install on YouTube) I found out my install (languages, keyboard,) options, were done by command line during the install, not the GUI. 
I finally got it to boot up the GUI, and after the Ubuntu  login screen, immediatly it seems to hang at the next screen (solid maroon in color) and never goes anywhere...
Any suggestions on this G3 B/W imac?
Thanks!

---

### Post by 3rdalbum on 2007-02-03
At the login screen, go to the "Options" menu and choose "Session". In the box that appears, choose "Failsafe terminal".

Log in. You will be brought to a terminal where you can type commands. Type:

```
sudo date -u 020312352007
```

When it asks you for your password, type it (it will not appear on the screen).

Now log out with the command "exit", change the session back to "Default System Session", and log in again. Now it should log in correctly.

(This is what is referred to as "the date bug" - on some versions of Ubuntu, it won't log into Gnome if your computer's clock is set too far in the past)

---

### Post by humboldthead on 2007-02-04
Thank you very much for the info... I did the time change as you suggested, step by step, but whenever I changed the session back to default session, it seemed to still get hung...but I was learning from it, and knew I wasnt far from firing up this thing...
So, I used the date command without the -u , then after exiting and logging out, I logged back in, this time I chose Gnome, and it went into the GUI screen for the first time...! Is this what I was looking for? or is there another UI in here besides the Gnome environment that was shooting for? Again it only would work if I chose Gnome from the session list.
I went ahead and did the software updates and everything is up to date...it does run rather slow on this G3 B/W, is there another version of Linux that maybe I should have installed since I am working with 64 megs of ram? Xubuntu maybe?

I do want to thank you folks for assisting me with getting Linux installed, Ive been on Macs for 3 years now, and want to test the Linux waters that I have been so curious about for the past few months...
Thanks again!

---

### Post by grazie on 2007-02-04
humboldthead,

I run xubuntu by choice, even though I have quite a high spec. machine. If you use xubuntu, you will definately see an improvement, but only 65M of ram is on the low side. However, adding an even lighter window manager like FluxBox may give your machine a new lease of life. I added FluxBox to an old B&W 350mhz with 256M ram and the performance increase was massive. Also, some of the older releasestend to be quicker on older machines, but I'd recommend going with xubuntu. 

Incidently, I'm a bit confused about what machine you have. If you have an iMac, what colour it is doesn't really matter or maybe you do have a B&W G3?

---

### Post by humboldthead on 2007-02-05
Thanks for the suggestions and advice. I was trying to install Xubuntu-desktop in Synaptic after doing the software updates, but it kept asking for the disk, and I gave it to a friend, so, I burned another,and am doing a fresh install from the start...  
I typed "install xubuntu-desktop" at the prompt and everything seems to be installing correctly.
It's a Blue/white/350 mhz/64mgs/10G HD/ iMac...
:-) Thanks

---

### Post by 3rdalbum on 2007-02-05
Wow, you must be running quite an old Ubuntu. Glad my advice helped!

---

### Post by humboldthead on 2007-02-05
Thanks everyone, I am up and running Xubuntu! It is running way faster than Ubuntu was on my G3.Thanks again for your time,advice and suggestions! Im sure I will be asking for more tips and troubleshoots in the near future!
Tony, Humboldt Co. California

---

