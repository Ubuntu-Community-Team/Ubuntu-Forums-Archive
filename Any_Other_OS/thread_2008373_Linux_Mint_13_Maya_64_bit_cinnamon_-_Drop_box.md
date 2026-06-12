---
title: "Linux Mint 13 Maya 64 bit cinnamon - Drop box"
date: 2012-06-22
forum: Any Other OS
---

### Post by shanep-server on 2012-06-22
I tried to install drop box via software manager and it wouldn't complete.. so I exit restart computer and it says to run sudo dpkg --configure -a.. now it just reloads dropbox and hangs at 99% downloaded. So i tried to go into synaptic and it says I need to run sudo dpkg --configure -a.. so I went into software manager and attempted to remove dropbox and its hanging at 12%.. wtf is going on an how do i get drop box off my computer so its back to business as usual?

---

### Post by howefield on 2012-06-22
Thread moved to "*Other OS/Distro Talk*"

---

### Post by sffvba[e0rt on 2012-06-22
I feel your pain... having exactly the same issue with Ubuntu 12.04 32-bit... basically the proprietary part of dropbox downloads to 99% and then nothing happens.

I haven't found a way to make it work yet :(


404

---

### Post by shanep-server on 2012-06-22
Yah exept now I can't use synaptic / software center / update manager... looks like a reinstall is gonna have to happen.

---

### Post by nkbielst on 2012-06-22
> **not found said:**
> I feel your pain... having exactly the same issue with Ubuntu 12.04 32-bit... basically the proprietary part of dropbox downloads to 99% and then nothing happens.

I haven't found a way to make it work yet :(


404

I had that issue with 64bit Ubuntu 12.04. I solved it by downloading the deb directly from dropbox. The version in the repos seems to be broken.

---

### Post by sffvba[e0rt on 2012-06-22
> **shanep-server said:**
> Yah exept now I can't use synaptic / software center / update manager... looks like a reinstall is gonna have to happen.

I was able to get Software Center to stop its nonsense eventually (by accident)... so there is a way I am sure...

> **nkbielst said:**
> I had that issue with 64bit Ubuntu 12.04. I solved it by downloading the deb directly from dropbox. The version in the repos seems to be broken.

I also tried the deb file and still no luck (the only time it worked was when I used wget to download the installer and run it from terminal which is less than ideal because I then didn't have it configured for Nautilus...)

Something odd has happened since a week ago when it installed fine :/


404

PS - I think it is time to report a bug perhaps...

---

### Post by tonyjc on 2012-06-23
I'm having exactly the same issue, I've been setting up 2 new PCs with linuxmint and can not get dropbox to work, I'm having the 99% issue and if I install from command line then nautilus doesn't work.

I am writing this on a mint machine I installed about 2 weeks ago that has dropbox working fine so something has gone wrong somewhere.

---

### Post by sffvba[e0rt on 2012-06-23
> **tonyjc said:**
> I'm having exactly the same issue, I've been setting up 2 new PCs with linuxmint and can not get dropbox to work, I'm having the 99% issue and if I install from command line then nautilus doesn't work.

I am writing this on a mint machine I installed about 2 weeks ago that has dropbox working fine so something has gone wrong somewhere.

I went home and even re-installed Ubuntu and tried installing Dropbox before I ran any updates, same problem.

Installed Xubuntu 12.04, same problem (doesn't matter if I use Software Center, apt, or the deb file from the Dropbox website).

I am not a happy camper at the moment :(


404

---

### Post by tonyjc on 2012-06-23
So we have the issue on ubuntu, linuxmint & xubuntu - which would indicate a wider issue than just a few of us having install problems.

Whilst this doesn't fix the issue it does help narrow down where the root cause is.

---

### Post by howefield on 2012-06-23
[http://ubuntuforums.org/showthread.php?t=2008400](http://ubuntuforums.org/showthread.php?t=2008400)

---

### Post by sffvba[e0rt on 2012-06-23
> **howefield said:**
> [http://ubuntuforums.org/showthread.php?t=2008400](http://ubuntuforums.org/showthread.php?t=2008400)

Sometimes Linux can really make me question the point of using it when something as simple as this that worked so well only a few days ago now requires one to jump through hoops...


404

---

### Post by malaprohibita on 2012-06-24
> **not found said:**
> Sometimes Linux can really make me question the point of using it when something as simple as this that worked so well only a few days ago now requires one to jump through hoops...


404
Definitely frustrating.

---

### Post by buzzingrobot on 2012-06-25
This 99% thing has been reported on a variety of distributions. 

The command line instructions on Dropbox's Linux page work just fine, and they correctly set it up as a startup app.

I've never been able to install Dropbox from the Ubuntu repos.  Always complains its in the wrong location.

---

