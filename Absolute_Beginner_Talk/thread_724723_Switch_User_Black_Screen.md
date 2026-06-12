---
title: "Switch User Black Screen"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-14
I know this is a fairly widespread problem, but of the few soltuions I've tried, they don't seem to be working...

First:
"If I can save someone the time of searching it out...

type this in a terminal:

sudo gedit /etc/X11/gdm/gdm.conf

find the line that begins with
#AlwaysRestartServer=false and change it to read
AlwaysRestartServer=true

reboot and you should now be able to log out."

I tried that, but believe it or not, there is NO DATA in my gdm.conf file. So, I'm not exactly sure what to do.
But in any case, yes, pressing log out of switch user will give me a black screen and force me to reboot

---

### Post by dokdoom on 2008-03-14
hmm, what if you were to run the live cd and copy that gdm.conf and just paste it into the blank gdm.conf

I'm not sure what the live cd gdm.conf file will look like or if it will work but it's worth a shot.

---

### Post by Literati on 2008-03-14
But wouldn't like, not having a GDM file in the first place, shouldn't that make Ubuntu just...not work?

---

### Post by Literati on 2008-03-15
Bump

---

### Post by glennric on 2008-03-15
Your gdm.conf file is located in /etc/gdm/ not /etc/X11/gdm.  So try
```
sudo gedit /etc/gdm/gdm.conf
```

---

### Post by Literati on 2008-03-15
> **glennric said:**
> Your gdm.conf file is located in /etc/gdm/ not /etc/X11/gdm.  So try
```
sudo gedit /etc/gdm/gdm.conf
```

Okay I found the file, edited it. I'm going to try and switch user now. :) Wish me luck!

---

### Post by Literati on 2008-03-15
No go :(
I can't even restart Xorg (Ctrl Alt Backspace)
The damn thing just locks up completely.

---

