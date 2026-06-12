---
title: "Uninstall &quot;slab&quot; via automatix"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by mbstrlbstr on 2006-10-21
I'm running edgy, and I intalled "Slab" via automatix before I upgraded. Now I can't uninstall slab, automatix gives me an error. I have upgraded to the automatix for edgy btw. How can I uninstall it?
automatix error
Fatal Error:
An apt-based error occured and unistallation was unsucessful

---

### Post by jordanmthomas on 2006-10-21
try
```
sudo aptitude remove slab
```
from a terminal and see what errors it gives you

---

### Post by SWAT on 2006-10-21
You can also use dpkg to remove the package
```
dpkg -r slab
```

Personal note: Don't use automatix in the future, it's not officially supported anyway.

---

### Post by mbstrlbstr on 2006-10-21
I did the sudo aptitude remove slab and got this:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "slab".  However, the following
packages contain "slab" in their description:
  garlic-doc procps bristol nco ntfsprogs garlic 
The following packages have been kept back:
  libggi2 mplayer 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I think it may be listed as main menu in my pannel list. but that didn't work either

---

### Post by SWAT on 2006-10-21
What does this 'slab' application/program do? I couldn't find it in my repository either. You could try a 
```
dpkg -l | grep -i slab
```

---

### Post by jordanmthomas on 2006-10-21
Slab is the new menu Novell developed for SuSE.
Someone ported it to Ubuntu, though.

---

### Post by arnieboy on 2006-10-21
> **mbstrlbstr said:**
> I'm running edgy, and I intalled "Slab" via automatix before I upgraded. Now I can't uninstall slab, automatix gives me an error. I have upgraded to the automatix for edgy btw. How can I uninstall it?
automatix error
Fatal Error:
An apt-based error occured and unistallation was unsucessful
```
sudo apt-get remove gnome-main-menu
```
The error was being thrown as a security measure because of an obsolete package called gcontrol which AX could not find. AX aims at the highest levels of security and consistency. The repositories have been updated to fix this bug.
Updating to the latest version of AX2 and trying to remove slab from AX2 will also work.

---

### Post by mbstrlbstr on 2006-10-22
Hey thanks arnieboy. It worked!

---

