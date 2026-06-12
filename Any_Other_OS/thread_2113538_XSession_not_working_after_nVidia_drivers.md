---
title: "XSession not working after nVidia drivers"
date: 2013-02-07
forum: Any Other OS
---

### Post by Kinetic_lord on 2013-02-07
Hello,

My XSession fails to start after installing the nVidia drivers from their website.

It simply says: "Cannot load session: ubuntu"

I am running Linux Mint 13, my graphics card is nVidia GeForce 525M.

I would like to know how I can solve this problem and get my system to work with the graphics card.

For some reason the xorg.conf file seems to be ignored by the system as I have tried to modify it before (and ended up adding some xrandr commands at startup to get my external monitor to work at the appropriate resolution).

Thank you very much.

---

### Post by Perfect Storm on 2013-02-09
Moved to Other OS/Distro Talk.

---

### Post by Kinetic_lord on 2013-02-09
Since Mint is the same thing as Ubuntu except for the desktop environment that I like, I assumed that I could just post it under Hardware were more specialized people would be capable of replying.

Cheers for the pointless change.

---

### Post by Perfect Storm on 2013-02-09
Mint is not supported by Canonical. If you wish to get support for Mint they have an excellent forum at [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by Kinetic_lord on 2013-02-10
> **Artificial Intelligence said:**
> Mint is not supported by Canonical. If you wish to get support for Mint they have an excellent forum at [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Excellent is quite an overstatement.

---

### Post by Kinetic_lord on 2013-02-10
Hello,

My XSession fails to start after installing the nVidia drivers from their website.

It simply says: "Cannot load session: ubuntu"

I am running Ubuntu 12.04, my graphics card is nVidia GeForce 525M.

I would like to know how I can solve this problem and get my system to work with the graphics card.

For some reason the xorg.conf file seems to be ignored by the system as I have tried to modify it before (and ended up adding some xrandr commands at startup to get my external monitor to work at the appropriate resolution).

Thank you very much.

---

### Post by Toz on 2013-02-10
Duplicate threads merged. Please do not create duplicate threads - it dilutes the community effort.

---

### Post by drawkcab on 2013-02-11
> **Kinetic_lord said:**
> Hello,

My XSession fails to start after installing the nVidia drivers from their website.

It simply says: "Cannot load session: ubuntu"

I am running Ubuntu 12.04, my graphics card is nVidia GeForce 525M.

I would like to know how I can solve this problem and get my system to work with the graphics card.

For some reason the xorg.conf file seems to be ignored by the system as I have tried to modify it before (and ended up adding some xrandr commands at startup to get my external monitor to work at the appropriate resolution).

Thank you very much.

You might be better off purging the driver you installed and installing the latest driver from the repositories or using a stable ppa.

---

