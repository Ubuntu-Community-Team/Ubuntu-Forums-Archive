---
title: "problem with upgrading to feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ilovebombay on 2007-04-20
Allright guys, I don't have much experience.

When I try to upgrade through the upgrade manager to the new system: feisty fawn,

I get the following error:
[B]Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)[/B]

I tried to upgrade normal updates but it gives a similar error...

What to do???

Does anyone know?

---

### Post by Nik_Doof on 2007-04-20
The error itself says what you can do...

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

The Ubuntu servers are being hammered due to Feisty, so you might have to keep trying :)

---

### Post by ubunter1 on 2007-04-20
instead of update manager can we do it through the terminal?,i have the same problem.

---

### Post by rosswmcgee on 2007-04-20
Same thing on two computers. How to fix? Can you up grade with the CD?

---

### Post by serfcx on 2007-04-20
Probably best to do a clean install. Download and burn the iso and back up your personal stuff.

There are several threads to look at

---

### Post by Nythain on 2007-04-20
you could either try changing the country code to something less popular... wait a while... or back up your /home directory, download the feisty cd and reinstall ubuntu all together

---

### Post by Seisen on 2007-04-20
To upgrade in from the terminal you need to do this:

```
sudo apt-get dist-upgrade
``` or
```
sudo aptitude dist-upgrade
``` just make sure that all of source list points to feisty.

---

