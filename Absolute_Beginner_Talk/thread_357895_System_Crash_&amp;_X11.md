---
title: "System Crash &amp; X11"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-02-10
Twice after reinstalling Edgy my system failed to boot, citing something about X not being able to run. It appeared to be a basic video problem. I had been installing lots of programs via the terminal so I don't know what the offending step was that caused the resolution problem.

SuperGrub couldn't solve the problem as boot up got past this hurdle. Selecting system repair/restore off the CD didn't seem to work, nor did running "sudo dpkg-reconfigure xserver-xorg". Both times I had to completely reinstall Edgy (something I'm getting really good at on my test machine).

My question is: since it's a resolution problem and something to do with xorg, can I make a copy of a working X11 directory or portions thereof and simply recopy a stored copy to restore things if it should happen again? I know Windows won't see a Ext3 disk but I can get to a prompt and figure from there I might be able to copy or move directories around.

Thanks.

---

### Post by taurus on 2007-02-10
Reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by drs305 on 2007-02-10
As I mentioned, I tried that but didn't get it to work. It's possible I didn't understand some of the requests but I mostly used defaults. Unfortunately, I can't remember the exact details but I seem to recall that during the running it ended up forcing me out of the script and back to a command prompt. This happened around the 15th step or so, I believe it was asking me a question with a default answer of "24"...  [Unless that was the last step and kicking me back to a prompt was what it was SUPPOSED to do.]

---

### Post by taurus on 2007-02-10
If you're not sure about a question, take the default and for a video driver, use **vesa**.

---

### Post by shane634 on 2007-02-10
If you did the latest kernel update chances are you need to reinstall your video drivers. Which video card are you using?? Either way nvidia or ati get the Envy script. Let us know your card and we can get ya up and running again.

---

### Post by drs305 on 2007-02-10
shane 634 et al,

Thanks for the replies. I actually have my system running again but I did it with a complete reinstall. I ran Envy - I thought it would list my driver but it actually only gave the options to reinstall various drivers (ATI & nvidia). Of course, I can find the driver via System, Admin, Device Mgr. (NV20 - GeForce3 Ti 200, I guess).

I'm still wondering if copying a backup of etc/X11/xorg.conf would restore the system as long as it was to the same computer/configuration.

---

