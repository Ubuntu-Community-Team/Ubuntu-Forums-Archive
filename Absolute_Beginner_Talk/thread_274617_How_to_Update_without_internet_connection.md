---
title: "How to Update without internet connection"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by UseOf on 2006-10-10
Hello all ubuntu user

I am a linux newbie & i need your help. I using Dapper Drake at my PC at home. My PC is Athlon 64 processor based. The problem is i  Connected to the internet only at my University Computer labs. 
So how do i Update & install Ubuntu software repository without internet connection?

Thanks before for your support.

---

### Post by Jussi Kukkonen on 2006-10-10
That's quite difficult, there's no easy way to do it.  Some projects are underway to fix this:
[https://features.launchpad.net/distros/ubuntu/+spec/offline-updater](https://features.launchpad.net/distros/ubuntu/+spec/offline-updater)

New software installs can be done this way manually: run 
```
sudo apt-get install <package-name>
```
The install won't work of course, but you get the list of needed packages. Use the list and packages.ubuntu.com to download everything you need on the connected machine. Not very handy, but probably works.

---

### Post by hpp3 on 2006-10-18
Isn't there a way to download packages from a location that holds *just* updates (like where apt-get finds updated files) and download those for burning to a CD? I am in a similar fix as I have just installed Xubuntu at home (where there is only dialup) and 97 megs of updates is not going to be easy. However, at work I have a 1.5 M cable connection at a Windows workstation (so the offline-updater would not work for me)

---

### Post by rccharles on 2006-10-18
> **hpp3 said:**
> I am in a similar fix as I have just installed Xubuntu at home (where there is only dialup) and 97 megs of updates is not going to be easy. 

I let my update run overnight.

In case the connection goes down, you can just restart the update. The information downloaded already will be read from a disk cache.

Robert

---

### Post by hpp3 on 2006-11-20
Ok, here's what I now do to get updates for my dial-up connected Ubuntu at home with my cable internet at work on a Windows workstation. I start an update with Synaptic, but instead of going through with it, go File > Save Download Script. Then email that script to myself at the office, where I have a windows port of wget installed (the download script is a shell script with a list of "wget <package>" lines). Convert the .sh to a .bat and download away. Burn to CD and take home. Done.

---

