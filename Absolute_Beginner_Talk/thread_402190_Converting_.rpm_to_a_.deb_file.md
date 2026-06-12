---
title: "Converting .rpm to a .deb file"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-05
I am following the guide to installing LimeWire on [this](http://torrentfreak.com/how-to-install-limewire-on-ubuntu-610-edgy-eft/) page, and I am up to the point where it tells me to :

 [b]convert the package from the .rpm it is to a .deb file.

alien -d limewire.rpm[/b]

I did everything else up to this point including updating Java, making Bash the default CLI, downloading LimeWire and installing 'alien'.

When I type 'alien -d limewire.rpm' in to the terminal, I get this message:

**Must run as root to convert to deb format (or you may use fakeroot).**

I tried typing 'sudo alien -d limewire.rpm' and I get this message:

**File "limewire.rpm" not found.**

I also tried using 'limewirelinux.rpm' instead of just 'limewire.rpm' (since that how the file is spelled on my desktop) and that also didn't work.

---

### Post by JamieC on 2007-04-05
Are you in the right directory? If it's on your desktop then you should do this:
```

cd ~/Desktop

```

Then:
```

sudo alien -d <filename>

```

---

### Post by x-ray vision on 2007-04-05
I still get the message : **Must run as root to convert to deb format (or you may use fakeroot).**

I tried typing in sudo first ( sudo alien -d limewire.rpm0 andI still get: **File "limewire.rpm" not found.**

---

### Post by x-ray vision on 2007-04-05
Ahh, wait- I tried LimeWireLinux this time like it appears on my desktop and a locked icon appeared. I'll follow the rest of the instructions now and see what happens. Thanks!!

---

### Post by x-ray vision on 2007-04-05
How do I get the terminal to not start with 'desktop:~$ ' ?

---

### Post by zvacet on 2007-04-05
desktop:~$ cd

---

