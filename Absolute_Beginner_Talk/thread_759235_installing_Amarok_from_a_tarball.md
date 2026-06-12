---
title: "installing Amarok from a tarball?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by ConsumingFire783 on 2008-04-18
Hey,
I'm trying to install the newest version of Amarok.  It's not in the repositories, so it has to be installed from a tarball.  How do I do this?

---

### Post by Shazaam on 2008-04-18
Look here........
[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

---

### Post by oldos2er on 2008-04-18
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ConsumingFire783 on 2008-04-19
I got to the point of typing ./configure, and I get an error message.

Here's what it says:
configure: error:  Can't find X libraries.  Please check your installation and add the correct paths.

From other sites, I got advice to make sure build-essentials, gcc, libX11-dev and xlibs-dev are installed.  They all are, but I still get the error message.

Any advice of what to try next?

---

### Post by stchman on 2008-04-19
> **ConsumingFire783 said:**
> Hey,
I'm trying to install the newest version of Amarok.  It's not in the repositories, so it has to be installed from a tarball.  How do I do this?

Amarok website gives you instructions on building from source.

[http://amarok.kde.org/wiki/Download:Source](http://amarok.kde.org/wiki/Download:Source)

---

### Post by ConsumingFire783 on 2008-04-19
Yes, I saw those directions.  But I keep getting an error message, as shown in above post.  so I need to know how to remedy the error message before I can finish that walkthrough.

---

### Post by forestpixie on 2008-04-19
Did you use this command to make sure you have dependencies

```
sudo apt-get build-dep amarok
```

---

### Post by Bodsda on 2008-04-19
enable all of your repositories, amarok **is** in synaptic

---

### Post by Paqman on 2008-04-19
Check all the dependencies carefully. You might have one which needs to be upgraded to a version higher than what the repos can give you.

---

### Post by forestpixie on 2008-04-19
> enable all of your repositories, amarok is in synaptic

The newest version isn't in the feisty/gutsy repos nor in backports as far as I can see. Feisty has 1.4.7-0ubuntu1~feisty1 and gutsy has 1.4.8-0ubuntu3~gutsy1 in backports.

---

### Post by stchman on 2008-04-21
> **forestpixie said:**
> The newest version isn't in the feisty/gutsy repos nor in backports as far as I can see. Feisty has 1.4.7-0ubuntu1~feisty1 and gutsy has 1.4.8-0ubuntu3~gutsy1 in backports.

Is there a HUGE difference in the 1.4.8 and the 1.4.9?  If no then save yourself the headache.

---

### Post by Oldsoldier2003 on 2008-04-21
> **stchman said:**
> Is there a HUGE difference in the 1.4.8 and the 1.4.9?  If no then save yourself the headache.

As best I can remember there isn't a huge difference between the two versions. If he really really wants 1.4.9 it is in Hardy, and Hardy does run a lot better than Gutsy... and feisty too (I just realized the OP has feisty)

---

### Post by forestpixie on 2008-04-21
Think there's only a difference if you want to have the covers - Amazon changed something apaprently - same deal hit Exaile.

Personally I couldn't give a stuff about the pretty pictures as I have OSD turned off :)

I'd agree with the sentiment though - if you don't need the covers don't bother and wait for hardy.

---

### Post by stchman on 2008-04-21
> **Oldsoldier2003 said:**
> As best I can remember there isn't a huge difference between the two versions. If he really really wants 1.4.9 it is in Hardy, and Hardy does run a lot better than Gutsy... and feisty too (I just realized the OP has feisty)

I cannot speak about Hardy, but Feisty runs EXCELLENT on my machines.  I tried Gutsy and it booted SSSSLLLLLLOOOOOWWWWWWW.

---

### Post by Oldsoldier2003 on 2008-04-21
> **stchman said:**
> I cannot speak about Hardy, but Feisty runs EXCELLENT on my machines.  I tried Gutsy and it booted SSSSLLLLLLOOOOOWWWWWWW.
. On my system fastest > slowest = Hardy>Fiesty>Gusty but like anything else I guess individual hardware and configurations are what makes the big difference.

---

