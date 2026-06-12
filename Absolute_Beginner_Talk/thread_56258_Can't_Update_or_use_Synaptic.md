---
title: "Can't Update or use Synaptic"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-08-11
When I load up Synaptic or Uupdate manager, it says Your packages are out of date and tries to update and gives me these error message
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
E: Archive directory /var/cache/apt/archives/partial is missing.
I don't know whats wrong, everything was working fine this morning.

And I think my repositories thing is ok..
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by blind0wl on 2005-08-11
Close Synaptic and in a console type:

```
sudo apt-get update
```

What does the output say?

---

### Post by poofyhairguy on 2005-08-12
I think I know the problem. This line needs to be deleted:

> 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

Then run the command one post up!

---

### Post by Copter on 2005-08-12
i have got also this line
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```and similar sources.list file and everything works fine. also running from konsole to see what exacly kynaptic is doing.

copter :]

---

