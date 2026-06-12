---
title: "Bootclean failure cleaning /tmp"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by BLTicklemonster on 2008-04-13
I see this while booting, and it has a red mark next to it.

I'm running out of space on my hard drive, so it would be nice to know that stuff that ought to be getting cleaned is actually getting cleaned.

How can I correct this?

There was a post sort of like this from 07 that was not answered at all. This leads me to conclude that little is known about this.

---

### Post by Oldsoldier2003 on 2008-04-13
> **BLTicklemonster said:**
> I see this while booting, and it has a red mark next to it.

I'm running out of space on my hard drive, so it would be nice to know that stuff that ought to be getting cleaned is actually getting cleaned.

How can I correct this?

There was a post sort of like this from 07 that was not answered at all. This leads me to conclude that little is known about this.
well you could just do it manually

```
cd /tmp 
sudo rm -r *
```
along with 
```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by BLTicklemonster on 2008-04-13
Thanks! But what can I do to keep from getting the error, I wonder?

---

### Post by Oldsoldier2003 on 2008-04-22
to get rid of bootclean (not completely- just keep it from starting)
```
sudo update-rc.d -f bootclean remove
```
then after you do that you can decide to either debug the script or just leave it as is.

If you debug the script you can reanble it by running

```
sudo update-rc.d bootclean defaults
```
for more options see man update-rc.d

---

