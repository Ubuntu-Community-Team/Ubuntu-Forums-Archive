---
title: "kubuntu-desktop package"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by w33mhz on 2006-08-14
I have installed the server version on my machine and I want to use the KDE desktop enviorment with it.  I found after great length the x-window-core package, which is a pre-requisite for the kubuntu-desktop package to run.  Well I am at the point now where I need the kubuntu-desktop package, I can't seem to find where I can download it.  I can find the full installation of kubuntu, but not the package.  Important Note, my machine is NOT hooked an internet connection so I am needing to download and install via CD, not via a repository.  If someone could get a link to me to download it, this would be cooL.

---

### Post by linear on 2006-08-14
Well, "kubuntu-desktop" is a meta-package. It doesn't really contain anything, but depends on a lot of other packages that make up Kubuntu. So there isn't a one "thing" that you can download. :(

---

### Post by aysiu on 2006-08-14
You would have way too many packages to download individually.

Get ahold of the Kubuntu **Alternate CD**.

Then type these commands in the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by w33mhz on 2006-08-14
Really.  Well I guess thats why i'm having a hard time with it.  All the documentation I've read leads me to believe that I can/should install that, and that it in fact is all that really needs to be install versus downloading and installing the CD ISO.  I guess I'm stuck between a rock and a hard place then.  Well I'll have to do it all from scratch on the basic kde installation, is this what you are saying?

---

### Post by w33mhz on 2006-08-14
ok how do i get the alternative cd ?  I don't know what it is, just me I guess, I seem to always have a rough time finding stuff on ubuntu's website.  The only way i find the info on their site is to google it then I get a link with the info on their website.

---

### Post by aysiu on 2006-08-14
[http://ubuntu-releases.cs.umn.edu//kubuntu/6.06/](http://ubuntu-releases.cs.umn.edu//kubuntu/6.06/)

---

### Post by w33mhz on 2006-08-14
Thank you very much.  I apreciated it.  :)

---

