---
title: "libgpod 0.7.90 on Jaunty?"
date: 2010-04-19
forum: Apple Hardware Users
---

### Post by Bq32 on 2010-04-19
Hi,

On Ubuntu 9.04, "Jaunty", I have a problem with getting libgpod 0.7.90 to run. [I'd upgrade to karmic to use backports, but it doesn't show as an updatable-to system]. It says that libplist is missing, but a) it's not in the Jaunty repositories, and b) compiling from source comes up with an error that libxml2 is missing, which isn't in the repositories, either. Can I somehow get a version that will work for Jaunty?

Thanks in advance.

EDIT: Forgot to say I'm on a PowerMac G4 "AGP edition" [400?MHz CPU, 1GB RAM].

---

### Post by linuxopjemac on 2010-04-20
Maybe you have to use the Karmic Koala source repository and build it in your Jaunty environment...

Or upgrade to Koala.

---

### Post by Bq32 on 2010-04-21
> **linuxopjemac said:**
> Maybe you have to use the Karmic Koala source repository and build it in your Jaunty environment...

Or upgrade to Koala.

I will try using the source for Karmic, but the upgrading is where problems occur. It doesn't load anything for saying "New version of distribution available", it just says "Your system is up-to-date".

---

### Post by linuxopjemac on 2010-04-21
You cannot update things which are not in the binary repository. Things which are only available as a binary in Lucid, you can only compile yourself in Karmic, unless there is a backport. There is nothing to update.

---

### Post by Bq32 on 2010-04-21
> **linuxopjemac said:**
> You cannot update things which are not in the binary repository. Things which are only available as a binary in Lucid, you can only compile yourself in Karmic, unless there is a backport. There is nothing to update.

What I mean is that I'm in Jaunty, and can't upgrade to Karmic.

---

### Post by linuxopjemac on 2010-04-21
whz can't you upgrade when you are in Jaunty. It's just a matter of updating and then upgrading. But I am not sure if that will work out so well....if you try, backup all your data and be prepared to install from scratch.

If you dare:

```
sudo apt-get update
sudo apt-get upgrade
```

then you edit your /etc/apt/sources.list file and replace every jaunty by karmic
```
sudo nano /etc/apt/sources.list
```
ctrl/x and "y" to save

then update and upgrade:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Good luck

---

