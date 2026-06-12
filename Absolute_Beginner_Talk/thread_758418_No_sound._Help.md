---
title: "No sound. Help?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Pasty-Flawss on 2008-04-18
Hi, i just installed linux and sound isn't working but it works in windows vista. Anyone know how to fix? 

Thanks in advance. :)

---

### Post by spiderbatdad on 2008-04-18
Please tell us something about your computer, and which version of ubuntu you are running.

---

### Post by Pasty-Flawss on 2008-04-18
Gutsy 7.10 i think.. and  it's an Acer laptop. What else would you like to know?

---

### Post by spiderbatdad on 2008-04-18
open synaptic package manager. Install linux-backports-modules-your kernel.
Find your kernel running ```
uname -r
``` I think it is 2.6.22-14...not sure.
Reboot after install the backports.

---

### Post by Pasty-Flawss on 2008-04-18
I cant download packages from synaptic. Do you know any site where i can download the file and install it?

---

### Post by spiderbatdad on 2008-04-18
[http://packages.ubuntu.com/gutsy/source/linux-backports-modules-2.6.22](http://packages.ubuntu.com/gutsy/source/linux-backports-modules-2.6.22)

---

### Post by spiderbatdad on 2008-04-18
you still need to check uname -r to find out if you need the generic or i386...or whatever.

---

### Post by Pasty-Flawss on 2008-04-18
Sweet, thanks for the help! ^^

---

### Post by Pasty-Flawss on 2008-04-18
I installed the file and rebooted computer.

Where do the Installed files go? And how do i open them.

Sorry im a newbie at Linux ><.

---

### Post by kpkeerthi on 2008-04-18
> **Pasty-Flawss said:**
> I cant download packages from synaptic. Do you know any site where i can download the file and install it?

Enable the [backports]("https://help.ubuntu.com/community/UbuntuBackports") repository from System -> Admin -> Software Sources

---

### Post by Pasty-Flawss on 2008-04-18
er.. i cant download repositories i have to download them from the site which i have done. They are installed but where do i find the program?

---

### Post by kpkeerthi on 2008-04-18
linux-restricted-module contains drivers as kernel modules. kernel modules cannot be run like traditional programs by user instead they are loaded by kernel.

For packages that contain 'program' (those that can be run by user), you can check where the files are installed using this command.

```

dpkg -L <packagename>

```

**Example:**
```

dpkg -L rhythmbox

```

**For your apetite:**
1. [What is a kernel module?]("http://www.faqs.org/docs/kernel/x41.html")
2. [Standard places where linux stores programs]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

