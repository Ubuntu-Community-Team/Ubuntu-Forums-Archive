---
title: "codecs"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by jesterjoker on 2008-01-29
Hi 

Need to know which codecs to install to play mp3 and videos.

Any suggestions?

Thanx

---

### Post by ibizatunes on 2008-01-29
download and install automatrix
[www.getautomatix.com/](www.getautomatix.com/) 
then install the codecs for there....
easy
vlc + firefox plugins u need to do from
 system > admin > sytmaic > then vlc install all plugins etc and vlc will run almost everything

---

### Post by RomeReactor on 2008-01-29
Hi. This functionality isn't enabled by default due to [some licensing and patent restrictions]("https://help.ubuntu.com/community/RestrictedFormats"). If after reading the previous link you agree to install the necessary packages, search Add/Remove (Applications->Add/Remove) or Synaptic (System->Administration->Synaptic) for **ubuntu-restricted-extras**; or, to install from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install ubuntu-restricted-extras
```

Automatix is not recommended since it has been known to break package installations and corrupt software sources.

---

### Post by viciouslime on 2008-01-29
I would recommend against automatix. It's bound to cause you problems later. All the functionality you require is built in. Simply double click an mp3 file and ubuntu will prompt you regarding the codecs.

Another way to do it, would be to open add/remove programs and search for "codec" this will bring up the package you need to install.

If you'd prefer something slightly more techincal, open synpatic package manager (System/Administration/Synaptic Package Manager) and scroll down to packages starting with gstreamer-plugins-* if you click each one the description at the bottom will tell you which codecs it includes. :)

---

### Post by p_quarles on 2008-01-29
I don't recommend Automatix at all. The developers have corrected some of the earlier problems with that application, but it is still one that is unsupported by these Ubuntu and by these forums.

The best way to get the various codecs that don't ship with Ubuntu is to open a terminal and run the following:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
Getting some DVDs to play will take an extra step, which you can read more about here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by AlanR8 on 2008-01-29
I'm with Ibizatunes on this one.

I've been using Automatix for about a year now and installed Kubuntu on 10 machines and NEVER had any problems.

Its quick and easy and never broken anything.

Just my experience, you be the judge.

---

