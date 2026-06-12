---
title: "developers version?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by dented42 on 2007-09-30
is there a distro or version of the ubuntu CD (for the PPC) that has the developers tools allready on it?
(mainly gcc)

---

### Post by dented42 on 2007-09-30
specifically, I just want to be able to compile sources from the net.  how do I go about doing this?

the reason I ask about a CD is that the computer that I want to put ubuntu on does not have internet acces, and therefore can't get the required packages.

I want to download the sources on my mac running OS X, put it on a flash drive, and then compile it on the ubuntu machine

---

### Post by Golyadkin on 2007-09-30
I don't think there is, but you can install them very easily with a single command:
> 
sudo apt-get install build-essential gcc


or simply select it in Synaptic. This is something you have to do anyway, because you have to update your system to get all the fixes and patches from after the CD image was made.

---

### Post by Golyadkin on 2007-09-30
Ah, we posted at the same time, ignore my statement above. You can also download packages  and updates on another computer as .debs and then move them on your USB stick. There are guides on this forum to do that, just do a search for "offline update" or something similar.

---

### Post by llamakc on 2007-09-30
> **Golyadkin said:**
> I don't think there is, but you can install them very easily with a single command:


or simply select it in Synaptic. This is something you have to do anyway, because you have to update your system to get all the fixes and patches from after the CD image was made.

Installing build-essential is not something one would  "have to do anyway..." in order to get all of the updates. Ubuntu delivers software via the package system via .deb files and these arrive to a fresh install via apt-get, Synaptic, Adept, or Aptitude.

Here's the Ubuntu documentation on the basics.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by bobplano on 2007-09-30
build-essential was on the cd in dapper at least. just put in the cd

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

---

### Post by wirelessmonkey on 2007-09-30
sudo apt-get install build-essential , or download build-essential w/ synaptic or aptitude.

---

### Post by coggins on 2007-09-30
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/") 
Search for what you want, download it for your system architecture.  The download page links to the download pages for any dependencies; you'll have to grab them as well.  It's a bit tedious, but at least you can get .debs from any browser.

---

