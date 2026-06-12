---
title: "Installing build-essential from Install CD?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-06
I feel retarded, but I'm stuck getting build-essential installed from the Ubuntu installation CD. (I need it to compile my wireless card drivers to get on the Internet to use the REAL repos :D)

I added the CD into Synaptic, reloaded, and checked build-essential to be installed. It then told me I was missing dependencies (g++ and libc6-dev, maybe more).

I checked the CD, under /pool (where build-essential and the other .debs were) and couldn't find either one of them. Am I going to have to go through dependency hell, slowly transferring debs to my desktop via thumbdrive? Eek!

Please help. :D

EDIT: I also went through /etc/apt/sources.list and commented out all the web repos, just in case it was trying to get packages from there - the only repo that Synaptic is using is the CD.

---

### Post by aysiu on 2007-01-06
As far as I know, *build-essential* is on both the Desktop CD **and** the Alternate CD.

You're not using the Server CD, are you?

---

### Post by tonyr1988 on 2007-01-06
No, I'm using the Alternate CD, the same one I installed it with.

I see build-essential on there as a .deb *and* in the repos (if I add the CD, of course). The problem is that the CD is missing some dependencies. I could download those, but I'd have to download their dependencies too, and then I'd be entering dependency hell.

Man, I wish they set build-essential to be automatically installed upon Ubuntu installation.

---

### Post by taurus on 2007-01-06
Insert the CD into the drive and open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Bachstelze on 2007-01-06
Do you istall the DEB manually or use apt-get ? I had no problem installing build-essential from my Dapper alternate, I guess it's the same in Edgy.

(to Aysiu, it's on the server CD too - in Dapper at least)

---

### Post by tonyr1988 on 2007-01-06
The first time I used synaptic (I didn't know that the command-line for adding CDs was apt-cdrom add), and now it seems to work.

This time I tried the Edgy AMD64 Desktop instead of Edgy AMD64 Alternate. I don't know what happened earlier, but it seems to work now - thanks a ton.

---

