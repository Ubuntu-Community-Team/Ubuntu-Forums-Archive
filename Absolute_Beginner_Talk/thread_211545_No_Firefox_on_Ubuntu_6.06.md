---
title: "No Firefox on Ubuntu 6.06?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by ebvt on 2006-07-08
I just downloaded ubuntu 6.06 for Intel processors and want to use it in LiveCD mode for awhile. In the forum I see Firefox being discussed but it did not seem to be part of my downloaded package. Konqueror works fine, but I am used to Firefox from Windows. Will I have to install and then get Firefox?
Thanks, ebvt

---

### Post by klytu on 2006-07-08
Sounds like you downloaded a Kubuntu ISO. Try the downloading the desktop CD and you should find firefox there.

---

### Post by shoot2kill on 2006-07-08
or use
> 
sudo aptitude update
sudo aptitude install mozilla-firefox

you may have to do this each time you run the live CD, but as far as i know, it should work

---

### Post by catlett on 2006-07-08
open the konsole and put in this command ```
sudo apt-get install firefox
```

---

### Post by user1397 on 2006-07-08
you probably downloaded the kubuntu desktop cd, which comes with the K Desktop Environment (KDE) by default.  KDE's default web browser is Konqueror, not firefox.  You would have to either install firefox everytime you boot-up the live cd (using shoot2kill's method), or you could download the ubuntu desktop cd, which brings the GNOME desktop environment by default, and which has firefox by default.

---

### Post by dhallar on 2006-07-08
I just installed Kubuntu this morning from a desktop ISO disk. [Is it OK for me to ask a Kubuntu question here?] After setup I had it install Firefox 1.5.0.4 The kookiest thing is happening: When I try to access certain tabs in FF preferences [advanced, content, privacy], Firefox shuts down when that tab's screen starts to appear.

The same thing is happening in the preferences for the extensions I've installed. If I access the extensions' "options," as soon as the options screen starts to appear, Firefox shuts down. Nothing else crashes.

Also, I installed the Reload on Double-Click extension, and it's not working at all. 

I haven't run into a problem like this in Windows or in Mac OS X. Solution, anyone?

---

### Post by aysiu on 2006-07-08
Try [this](http://www.ubuntuforums.org/showthread.php?t=103930).

---

### Post by dhallar on 2006-07-08
Ayisu,
That worked like a charm and was very easy to do. Thanks! I'm saving it just in case.

---

### Post by aysiu on 2006-07-08
I don't know why Firefox profiles become "corrupt" in the first place, but (unlike you) I've had it happen in Linux distros, Mac OS X, *and* Windows.

---

### Post by ebvt on 2006-07-08
Thanks Eric and everybody else for the help. I did indeed download K w/o
knowing that Konqueror was its browser. Best forum I have ever been on!
ebvt

---

### Post by dhallar on 2006-07-08
Aysiu,
As an FYI:
I found that it was the Silver theme that I downloaded that was the problem. Before I downloaded it [after I did your fix] I accessed preferences in FF with no trouble. Then I downloaded the Silver theme. The preferences shutdown problem began again. I uninstalled the theme, and everything was normal. Unfortunately, the Silver theme is my favorite.

---

### Post by aysiu on 2006-07-08
Yeah, it's usually the extensions and themes that do it. Grr. I love extensions and themes.

---

