---
title: "Xubuntu crashing!"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by xyeovillian on 2007-11-26
I have just installed Xubuntu on my old garage PC which is [http://h10025.www1.hp.com/ewfrf/wc/d...288&lang=#N341](http://h10025.www1.hp.com/ewfrf/wc/d...288&lang=#N341)

And when I go to the terminal it crashes back to the login page again I'm dual booting with ME is there any diagnostics that I can perform ie freeware to try and find the problem? I have 192MB RAM!

I did have problems trying to load win XP just kept going to blue error screen so thats why I went back to ME.  I installed Xubuntu with the alternative CD as it wouldn't read the live CD one.

My original problem was trying to get Firefox working as I have the error message that its already runnig and needs to be closed!

---

### Post by Daveski on 2007-11-26
> **xyeovillian said:**
> And when I go to the terminal it crashes back to the login page again I'm dual booting with ME is there any diagnostics that I can perform ie freeware to try and find the problem? I have 192MB RAM!

Are you saying that you get the graphical login which works. When you are at your desktop, if you run a Terminal it 'crashes'? Can you describe what happens in more detail?

> I did have problems trying to load win XP just kept going to blue error screen so thats why I went back to ME.  I installed Xubuntu with the alternative CD as it wouldn't read the live CD one.

XP installs giving a blue screen of death is usually a sure sign of a hardware problem - either faulty hardware or a driver misbehaving. This could be a dodgy ram chip.

---

### Post by gn2 on 2007-11-26
With 192mb RAM you would not be able to install from the Live CD.

Have you got the xubuntu-desktop installed?

When you get the message that Firefox is already running, click Applications>System Process Manager> right click on firefox-bin and select Kill, confirm Yes in the dialogue box.

You should now be able to open Firefox.

---

### Post by mali2297 on 2007-11-26
> **xyeovillian said:**
> 
And when I go to the terminal it crashes back to the login page again 

This is a known bug, see
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)

The link gives you tips on how to get the terminal working. 

See also this post:
[http://ubuntuforums.org/showthread.php?t=605869?post=#8](http://ubuntuforums.org/showthread.php?t=605869?post=#8)

An alternative is to simply to use another terminal., there are plenty to choose from. For example: **xterm** (preinstalled), **rxvt-unicode** or **aterm**.

> 
My original problem was trying to get Firefox working as I have the error message that its already runnig and needs to be closed!

Open xterm, and try
```

killall firefox-bin

```
or
```

pkill firefox

```

---

