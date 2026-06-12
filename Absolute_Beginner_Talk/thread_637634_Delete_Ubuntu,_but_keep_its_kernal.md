---
title: "Delete Ubuntu, but keep its kernal"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by travismh on 2007-12-11
I'm trying to uninstall the environment for ubuntu (it's too slow).  Basically, I want to be able to use a pure openbox environment.  I don't mind uninstalling the packages that are embedded on ubuntu desktop-- i.e. openoffice, because I can always install them from the terminal emulator later.

But what's the safest way to do this?  And please, for you Arch users, I'm more comfortable with this than with pacman.

---

### Post by SupaSonic on 2007-12-11
There is an app called debfoster - basically it will ask you about every package on your system - whether you want to keep it or remove it. 
Be careful though, you might remove something valuable.

It's in the repos.

---

### Post by jaybombalous on 2007-12-11
uninstall the ubuntu-desktop package and install any window manager of your choice.

easy enough...

> But what's the safest way to do this? And please,** for you Arch users,** I'm more comfortable with this than with pacman.

what does this mean???

---

### Post by jaybombalous on 2007-12-11
> **SupaSonic said:**
> There is an app called debfoster - basically it will ask you about every package on your system - whether you want to keep it or remove it. 
Be careful though, you might remove something valuable.

It's in the repos.

u are giving him a way to break dependencies and cause a system wide failure. Not the greatest of advice.

---

### Post by travismh on 2007-12-11
hmmm... perhaps I could do a fresh server installation, and from there install openbox.  Would this be okay?

---

### Post by jaybombalous on 2007-12-11
if u really wanna format the drive, then so be it! I chose to take the easy road and just uninstall the ubuntu-desktop package.

---

