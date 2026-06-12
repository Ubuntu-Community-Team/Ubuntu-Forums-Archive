---
title: "Virtualbox - again"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-16
i have successfully installed XP with virtual box.

but is there a way i can install my graphixcs card drivers?
or anything?

i trie dmy drivers and it said my pc does not have the minimum requirements

i have given it 550mb of RAM
and 5GB drive - expanding

---

### Post by colo on 2007-06-16
You want to install your Guest OS's Guest Additions, Check the VirtualBox docs on that topic.

---

### Post by Golyadkin on 2007-06-16
Will installing Guest Additions allow you to use your graphic cards original drivers in Virtualbox? That seems strange... because then you would have full 3D acceleration with Catalyst drivers.

---

### Post by skymera on 2007-06-16
so whats is guest additions?

---

### Post by Midahed on 2007-06-16
It provides stuff like mouse integration, better video support (but not 3D), time sync to the host, shared folders, etc.

It's covered in the user docs.  There's a link on the downloads page [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Mike

---

### Post by Golyadkin on 2007-06-16
Or just click on "Install Guest Additions" in the Virtualbox menu when running the virtual machine, much easier.

---

