---
title: "Absent minded mistake"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by darweth on 2007-01-11
I removed a package not knowing it would remove ubuntu-desktop!  Yikes!  I just hit 'y' reflexively.  I know this doesn't impact the ability to run my OS, but i know that it hampers upgrades or something.  How can I re-install it without having to redo Ubuntu all over again?  Is there anyway?  I tried apt-get install ubuntu-desktop and it did not work.  

Save me from a re-install!

---

### Post by shanepardue on 2007-01-11
What did it say when you typed "sudo apt-get install ubuntu-desktop"?

---

### Post by darweth on 2007-01-11
Is the repos just down now or something?

```
Err http://us.archive.ubuntu.com edgy/main libsdl1.2debian 1.2.10-3ubuntu2
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main libpt-1.10.0 1.10.2.dfsg-0ubuntu3
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main libopal-2.2.0 2.2.3.dfsg-0ubuntu2
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main libpt-plugins-alsa 1.10.2.dfsg-0ubuntu3
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main libpt-plugins-v4l 1.10.2.dfsg-0ubuntu3
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main libpt-plugins-v4l2 1.10.2.dfsg-0ubuntu3
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main ekiga 2.0.3-0ubuntu3
  502 Bad Gateway [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main ubuntu-desktop 1.30
  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.10-3ubuntu2_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.2.dfsg-0ubuntu3_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/opal/libopal-2.2.0_2.2.3.dfsg-0ubuntu2_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.2.dfsg-0ubuntu3_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.2.dfsg-0ubuntu3_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.2.dfsg-0ubuntu3_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_2.0.3-0ubuntu3_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.30_i386.deb  502 Bad Gateway [IP: 146.137.96.7 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by shanepardue on 2007-01-11
I'm assuming you're on the internet with that computer as you post on here?

---

### Post by taurus on 2007-01-11
Just edit /etc/apt/sources.list and remove the **us.** in front of the repos.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by darweth on 2007-01-11
thx,  i got it all back

---

