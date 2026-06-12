---
title: "Customizing ubuntu, compiling my own kernel, etc...."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-10-25
Yeah, I've used Ubuntu with Gnome for a while, but I got bored and installed Kubuntu. I think it's pretty cool, but it doesn't seem like the best experience I can get out of a distro. I've tried like 50 distros so far, and Ubuntu is by far the most stable and capable distro. My friend recommended that I compile my own kernel if I want to have the best possible distro for me, personally, but I started reading an article on how it's done, and it looks really complicated. Another suggestion I got was that I should install a minimalist version of Ubuntu and "build it up" from there. First, how do I actually install a minimalist version? And, how do I "build it up" ? All I've thought about is changing the desktop manager and the windows manager. Right now I'm liking Konqueror, and KDE/Gnome seem to be the only good desktop managers. Any suggestions on what I can customize, what windows + desktop managers are the best, or if I should just compile my kernel? Or is there a kick-*** distro out there that I should try???

Thanks

---

### Post by OptimusPrime on 2006-10-25
Really, I would go with Gnome if you want to start minimalist. I don't recomend Kubuntu unless your computer is kind of outdated.  It's just a light version of Ubuntu.

---

### Post by kbsuperstar on 2006-10-26
K, but what can I add on/customize once I get a minimalist system?

---

### Post by bodhi.zazen on 2006-10-26
No, No, No .....

Minimalist = server install.

I did this by downloading the "alternate" cd. Boot the CD and at the command line type "server".

This will install a minimal base (NO X so be prepared for the CLI baby).

Then, ```
sudo vim (or nano) /etc/sources.list
``` and remove the # in front of the repositories, save and exit.

Now:```
sudo aptitude update
sudo aptitude install x-window-system-core <window-manager> gdm (if you want a graphical log-in) eterm firefox (or dillo) gaim mousepad abiword synaptic
```

<window manager> = LIGHT = gnome-core, kde-core, xfce4, fluxbox, icewm, or openbox.

Now you will have a very light base. Should be faster, leaner.

By "build up", what else do you want? Add it with synaptic (search for light weight alternated to the heavy weights).
> **kbsuperstar said:**
> K, but what can I add on/customize once I get a minimalist system?

Whatever you want.

If you want to make it easy, try Fluxbuntu.

---

### Post by raqball on 2006-10-26
Read this:

[http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560)

Say a few prayers and hope it come out how you want it :)

---

### Post by kbsuperstar on 2006-10-26
K, thanks for the minimalist outline, I'll definitely try it. I've been looking at kernel compiling tutorials, but it doesn't look like what I want. 

Thanks :)

---

