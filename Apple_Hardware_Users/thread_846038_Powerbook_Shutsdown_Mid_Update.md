---
title: "Powerbook Shutsdown Mid Update"
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by ninjapenguin on 2008-07-01
Hello,

I just recently installed Ubuntu on my powerbook G4 1.33ghz, and every time I try to upgrade the software, my powerbook turns off randomly.  I have tried both the update manager gui and doing 
sudo apt-get update
sudo apt-get upgrade
but both ways it shuts down randomly.

I watched it once on the manual route of upgrading and notice that it was setting up the new version of gnome.  I think the last thing that I saw was 
setting up gnome-keymanager 
I couldn't be 100% sure, because it was setting them up pretty fast after it did the gnome-app-data.
I also noticed that on the update manager gui, that 32bit kernel and 64bit kernel updates were selected.  Should I deselect the 64bit one and try again?

---

### Post by stream303 on 2008-07-01
By shut-down do you mean it powers off, or does the process just hang?

From the sounds of it, you may be running Dapper, and you definitely want the 32-bit kernel on that G4.

If you ever envision upgrading to Hardy, it might be wise to write down your existing /etc/X11/xorg.conf file somewhere just in case. :)

---

### Post by ninjapenguin on 2008-07-01
I am actually running Hardy, and by shutdown I mean it powers off completely and I got to restart it, and I know I want the 32 bit, that's why I suspect it might be the install of the 64bit on the side that is doing the problem.

---

### Post by stream303 on 2008-07-01
Yikes, that's odd with the shutdown.

Hardy should automatically use and install the proper kernel even if it downloads both versions.  For instance, I have both 32 and 64 bit kernels on my system without any intervention, and the proper kernel is installed without having to do anything.

I've got a feeling that the problem is with the process of updating, not the actual updates themselves.

As a test, are you able to download and install single programs from either apt-get or Synaptic?  Maybe install Htop for example as a quick test to see if there is something related...

---

### Post by ninjapenguin on 2008-07-01
> **stream303 said:**
> Yikes, that's odd with the shutdown.

Hardy should automatically use and install the proper kernel even if it downloads both versions.  For instance, I have both 32 and 64 bit kernels on my system without any intervention, and the proper kernel is installed without having to do anything.

I've got a feeling that the problem is with the process of updating, not the actual updates themselves.

As a test, are you able to download and install single programs from either apt-get or Synaptic?  Maybe install Htop for example as a quick test to see if there is something related...

I will test that out as soon as I do a fresh install of ubuntu on it, because when I did that update, it corrupted network manager.

EDIT: I was able to do sudo apt-get install supertux before doing the update before hand if that's what you mean.

---

### Post by stream303 on 2008-07-01
I'm kind of blown away that an update procedure would shut down the machine, but stranger things have happened in ppc land. :)

I took a quick look at supertux, and noted that it said it may have critical bugs, so perhaps supertux-stable might be the way to go.  I'm not a gamer so I don't know...

Keep an eye on Network Manager- on my ibook it scarfed up 100% of the cpu time as shown by *top*, so I had to disable it (rather than remove it) from the NM wiki:
[https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

...just in case...

---

### Post by ninjapenguin on 2008-07-02
> **stream303 said:**
> I'm kind of blown away that an update procedure would shut down the machine, but stranger things have happened in ppc land. :)

I took a quick look at supertux, and noted that it said it may have critical bugs, so perhaps supertux-stable might be the way to go.  I'm not a gamer so I don't know...

Keep an eye on Network Manager- on my ibook it scarfed up 100% of the cpu time as shown by *top*, so I had to disable it (rather than remove it) from the NM wiki:
[https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

...just in case...

I also did sudo apt-get install firefox
and sudo apt-get install evolution
because I noticed firefox was still 3.0 beta 5.
They installed fine and it didn't shut down.  So I am guessing there's just got to be one of the setting up procedures that just does it for my laptop.

---

