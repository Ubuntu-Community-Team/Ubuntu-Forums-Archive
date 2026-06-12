---
title: "imac g4 eject cd in single user mode from osx"
date: 2010-07-12
forum: Apple Hardware Users
---

### Post by coolman98 on 2010-07-12
I would like to install ubuntu on my imac g4 but osx won't boot so I wanted  to
to use ubuntu is there any way to eject cd from single user mode?:P

---

### Post by TechBeastie on 2010-07-12
Tried "drutil eject" yet?

---

### Post by coolman98 on 2010-07-12
thanks ill try that

---

### Post by coolman98 on 2010-07-12
I get a bus error "Bus error".

---

### Post by coolman98 on 2010-07-12
and when I boot into single user mode I get hard drive I/O
 errors , I think it is corrupted.

---

### Post by Legal Beagle on 2010-07-12
Software method:

You'll need to get into terminal.

```

df -l

```Copy the /dev/diskxx info, where xx is the disk number for your cdrom and try this:

```

disktool -e /dev/diskxx

```If that doesn't work, try:

```

hdiutil eject /dev/diskxx

```

Hardware method:

First, try rebooting and holding down the mouse button (WIRED mouse) during startup.

If that doesn't work, check out [http://support.apple.com/kb/HT2285](http://support.apple.com/kb/HT2285)

There's a graphic showing where the paperclip goes to pull it out.

...I'd be more comfortable trying it in the command line before I busted out the office supplies. Good luck.

---

