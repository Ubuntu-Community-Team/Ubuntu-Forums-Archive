---
title: "Infinite Loop of dependencies!"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by SpacedMonkey on 2007-06-02
So all I'm trying to do is get ndiswrapper installed. However, I find that I need to install build-essentials. And it's not on the 7.0.4 CD. I figure something like build-**essentials** would be included but nope. 

So I'm on the hunt for the packages and their dependencies and ran into a paradox.

In order to install g++-4.1 I need to install libstdc++6-4.1-dev

In order to install libstdc++6-4.1-dev I need to install g++-4.1

How is this possible? And what is the work around?

---

### Post by taurus on 2007-06-02
Actually, it's build-essential (without an s at the end) and it is on the installer CD.  So, insert the CD into a drive, open a terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by SpacedMonkey on 2007-06-02
Cool thanks!

---

### Post by sloggerkhan on 2007-06-02
The precompiled ndiswrapper only needs libc6, perl, and ndiswrapper common. Are you wanting to install from source?

---

### Post by SpacedMonkey on 2007-06-02
Ok, I was able to get ndisweapper-common_138 and ndiswrapper-ustils-1.9_1.38 installed... and when I go to install ndisgtk it says "Dependency is not satisfiable: ndiswrapper-utils"

---

### Post by SpacedMonkey on 2007-06-02
> **sloggerkhan said:**
> The precompiled ndiswrapper only needs libc6, perl, and ndiswrapper common. Are you wanting to install from source?
No, I'm just trying to install the packages and one by one it's telling me what else I need to install. It seems I now have ndiswrapper installed, but can't get ndisgtk_0.5-1 to install.

---

### Post by SpacedMonkey on 2007-06-02
> **SpacedMonkey said:**
> No, I'm just trying to install the packages and one by one it's telling me what else I need to install. It seems I now have ndiswrapper installed, but can't get ndisgtk_0.5-1 to install.
Well, I did the install of the windows drivers manually and it seems to have worked... now to find Wireless Assistant and install it

---

