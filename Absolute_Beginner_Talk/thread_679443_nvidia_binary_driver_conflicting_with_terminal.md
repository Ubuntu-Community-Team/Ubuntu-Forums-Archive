---
title: "nvidia binary driver conflicting with terminal?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by zachrey on 2008-01-27
I recently installed the binary nvidia driver, and I am running the most recent stable release of Ubuntu at the moment...

Problem is, after completing the install, I can no longer open and view the terminal. It opens, but is a blank white window.

Is there something I forgot to do?

---

### Post by swoll1980 on 2008-01-27
if you have the nvidia setting set up just do this```
 sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by dcstar on 2008-01-27
> **zachrey said:**
> I recently installed the binary nvidia driver, and I am running the most recent stable release of Ubuntu at the moment...

Problem is, after completing the install, I can no longer open and view the terminal. It opens, but is a blank white window.

Is there something I forgot to do?

If you installed some driver not from the Ubuntu repositories then you can have problems like this, just use what is in the repositories (and is known to work).

---

### Post by swoll1980 on 2008-01-27
> **dcstar said:**
> If you installed some driver not from the Ubuntu repositories then you can have problems like this, just use what is in the repositories (and is known to work).

I disagree I would install the latest drivers from nvidia.com using these instructions [http://ubuntuforums.org/showthread.php?t=679424](http://ubuntuforums.org/showthread.php?t=679424)

---

### Post by swoll1980 on 2008-01-27
using nvidias drivers solved a bunch of issues I was having

---

### Post by zachrey on 2008-01-27
I would love to try that command.

Problem is, I can't see the terminal.

In other news: I'm fairly sure the installed drivers came from the repositories. Restricted drivers and whatnot.

---

### Post by swoll1980 on 2008-01-27
cntrl+alt+F2 after you do the command hit F7 to get back to your gui upgrade to the nvidia drivers from nvidia.com when you update your kernel you will have to reinstall them but it's worth it

---

### Post by zachrey on 2008-01-27
Thanks! Every thing is working smoothly.

---

