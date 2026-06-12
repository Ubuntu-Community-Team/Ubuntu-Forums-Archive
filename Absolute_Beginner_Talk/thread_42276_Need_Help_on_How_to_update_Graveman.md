---
title: "Need Help on How to update Graveman"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by Kapre on 2005-06-16
Hiyall!!

Could you please point me to a right direction on how I can update/upgrade my Graveman to the newest release? The one that I got from using apt-get install graveman was 0.3.10 and when I looked to the Graveman website, the latest release (which has less bugs) is 0.3.12.

Any help would be very much appreciated.

Kapre  :?

---

### Post by SGC on 2005-06-16
Add the following to /etc/apt/sources.list

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Then in the terminal:

sudo apt-get update
sudo apt-get install graveman

---

### Post by Kapre on 2005-06-16
[QUOTE=SGC]Add the following to /etc/apt/sources.list

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Then in the terminal:

sudo apt-get update
sudo apt-get install graveman[/QUOTE]


SGC - Thank you very much.  :smile:

---

