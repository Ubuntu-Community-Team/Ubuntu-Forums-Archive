---
title: "Where do i find the root folder?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-17
I need to find the root folder of a game? where do i find it? there is a folder in my home folder..but that's not the root folder.

---

### Post by Flyingjester on 2008-02-17
in terminal type: locate "name of program" should bring up a list of associated file names, possibly leading the tree to the folder you need.

---

### Post by LaRoza on 2008-02-17
> **RadiationHazard said:**
> I need to find the root folder of a game? where do i find it? there is a folder in my home folder..but that's not the root folder.

The directory in your home is the configurations settings and save points and such. The program itself will most likely be in /usr/bin. Type "whereis <programName>" to find it.

---

### Post by Flyingjester on 2008-02-17
> **LaRoza said:**
> The directory in your home is the configurations settings and save points and such. The program itself will most likely be in /usr/sbin. Type "whereis <programName>" to find it.

hey that's handy, i'll have to remember that one.

---

### Post by Bachstelze on 2008-02-17
> **LaRoza said:**
> The directory in your home is the configurations settings and save points and such. **The program itself will most likely be in /usr/sbin**. Type "whereis <programName>" to find it.

/usr/bin, rather. Directories ending in "sbin" (/sbin, /usr/sbin and /usr/local/sbin) contain programs that should be used only by the superuser (thus the leading "s"), and are mainly system administration tools. Programs to be used by regular users reside in /bin, /usr/bin and /usr/local/bin.

---

