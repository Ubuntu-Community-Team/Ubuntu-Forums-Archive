---
title: "Screenful of dots"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by heiowge on 2008-04-12
Tried to play an avi file that works in Windows Media player just fine.

File is an avi file.  When I play it with Totem or VLC, it plays fine, but there is a grid layer of dots on the viewing window.  I can't seem to turn it off.

The same issue with other media files.

Any ideas?

---

### Post by Michael.Godawski on 2008-04-12
What are your specs? 
What version of Ubuntu are you using?

---

### Post by heiowge on 2008-04-12
Ubuntu 7.10, dualbooted with XP

Dell Desktop 2.8Ghz P4, 1.25Gb RAM not Graphic card other than that supplied on motherboard

---

### Post by Michael.Godawski on 2008-04-12
Let's make sure you have the needed codecs installed:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by heiowge on 2008-04-12
I think it probably is a codec problem, but my restricted drivers are up to date and it doesn't want to install any more, even when I'm playing an avi.

It doesn't seem to think I have a problem.

---

### Post by Sukarn on 2008-04-12
Do you have desktop effects enabled?

I remember a similar issue when I had desktop effects enabled. It used to randomly happen to me.

If you've got desktop effects enabled, then try changing the screen resolution and then changing it back to what it was before. Now try playing the video again.

Alternatively, you could relogin.

You could quickly change your resolution and change it back by pressing <Ctrl><Alt>- and then <Ctrl><Alt>+

---

### Post by heiowge on 2008-04-12
Tried login and Ctrl Alt - / +.  No luck.:(

Desktop is set to middle level effects - nothing flashy.  Set to no effects and it cured the dots.

I'm putting in a 256MB graphics card next week. Do you think that'll help.

---

### Post by heiowge on 2008-04-13
bump

---

### Post by Sukarn on 2008-04-13
> **heiowge said:**
> Tried login and Ctrl Alt - / +.  No luck.:(

Desktop is set to middle level effects - nothing flashy.  Set to no effects and it cured the dots.

I'm putting in a 256MB graphics card next week. Do you think that'll help.

It might help, but I do not really know.

I am on a 256 MB card, and I used to face that issue. It stopped happening a couple of months ago for some reason.

---

### Post by heiowge on 2008-04-14
Could it be the fact that you are on Hardy?

I'm still on Gutsy, but am upgrading with the official release.

---

### Post by Sukarn on 2008-04-15
> **heiowge said:**
> Could it be the fact that you are on Hardy?

I'm still on Gutsy, but am upgrading with the official release.

I think the upgrade to hardy might have been what fixed it (and it most probably was), but (and I'm not sure about this as it has been a couple of months now) I think that I stopped having the issue a few days before I upgraded.

It happened quite randomly to me though, so it might have just not happened for a few days before I upgraded.

---

### Post by heiowge on 2008-04-19
I turned off the middle level effects and all worked.

Put in a Nvidia GeForce 6 6200 Graphics card and drivers.

Problem solved.  Fancy graphics and films play just fine.

Have to wait and see what Hardy brings...

---

