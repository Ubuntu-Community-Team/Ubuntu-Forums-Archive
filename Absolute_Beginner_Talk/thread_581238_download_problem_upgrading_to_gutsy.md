---
title: "download problem upgrading to gutsy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by ratchevs on 2007-10-19
I get this error, when I run the distro upgrade from the update manager:

```

Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 302 Found

```

---

### Post by hyper_ch on 2007-10-19
I guess you'll have to manually change 3rd party repos like the medibuntu ones.

---

### Post by FredB on 2007-10-19
> **ratchevs said:**
> I get this error, when I run the distro upgrade from the update manager:

```

Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 302 Found

```

Just deactivate these mirrors, they're not useful to your upgrade.

And medibuntu will soon - or already - have gutsy repositories.

---

### Post by ratchevs on 2007-10-19
> **FredB said:**
> Just deactivate these mirrors, they're not useful to your upgrade.



erm, how exactly do i do this?

---

### Post by Sef on 2007-10-19
> Just deactivate these mirrors, they're not useful to your upgrade.

It would be more helpful to detail how to do it.

> get this error, when I run the distro upgrade from the update manager:

Code:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

You need to comment out that source list.  To comment it out put a # before it.

Applications > Accessories > Terminal

then type or copy and paste this command:

```
gksudo gedit /etc/apt/sources.list
```

Then find the line and comment it out.  Click Save and then quit.

---

### Post by FredB on 2007-10-19
Oups :(

You can also use synaptic, repositories menu.

I will whip myself with a windows vista box for such a mistake ](*,)

---

