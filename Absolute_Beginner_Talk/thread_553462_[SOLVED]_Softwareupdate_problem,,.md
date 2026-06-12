---
title: "[SOLVED] Software/update problem,,"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-09-17
I'm trting to update my Adobe Flashplayer plugin for Firefox. I have downloaded the tar.gz file and extracted it to desktop.
Adobes' instructions say to "Navigate to Directory in Terminal" and enter ./flashplayer-installer and hit enter.

Sad thing is, I have forgotten how to navigate to directory in Terminal.
Have read Stickys, Psychocats, How to install anything, and a few others and only became more confused.

Could someone help me with the right coding, please?

I'm still using Dapper Drake, btw.

Many thanks,

Jon

---

### Post by jamvegan on 2007-09-17
First, the easiest way to install that software, at least in Feisty (maybe not Dapper?) is to use Synaptic to install flashplugin-nonfree.

But, to answer your question, you want the cd command.  If the directory were "flashplayer", and it was on your desktop, you would get to it from your home directory (where you start when you open a terminal) like this:
```
cd Desktop/flashplayer
```

---

### Post by Romin-1 on 2007-09-17
Man 'O' Man,,, Terminal sure doesn't like me. cd Desktop/"directory" ./fp install all I get is, File or directory does not exist, even though I'm sitting here staring at it.

Tired of messing with this thing, will stick with the old version.

Thanks again, Jamvegan

Jon

---

### Post by Maestro23 on 2007-09-17
> **Romin-1 said:**
> Man 'O' Man,,, Terminal sure doesn't like me. cd Desktop/"directory" ./fp install all I get is, File or directory does not exist, even though I'm sitting here staring at it.

Tired of messing with this thing, will stick with the old version.

Thanks again, Jamvegan

Jon

File's on your Desktop?

> cd /home/username/Desktop

ls (lists files)


---

