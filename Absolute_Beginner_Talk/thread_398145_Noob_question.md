---
title: "Noob question"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by denysy1 on 2007-03-31
Hi,

I just installed ubuntu, I haven't ever used linux before am running into a bunch of trouble. I'm trying to install ndiswrapper to help me get my wireless card working, but when making the link to the kurnel source i get the following

ln: creating symbolic link `/lib/modules/2.6.17-11-generic/build/linux-2.6.17-11-generic' to `/usr/src/linux-2.6.17-11-generic': Permission denied


Am i doing something wrong?

---

### Post by steve.horsley on 2007-03-31
precede the command with the wird sudo like this:
**sudo ln -s whatever-it-was**
It will ask for your password, just to confirm it's still you at the keyboard.

sudo allows you to run commands with superuser privileges - SetUserandDO

---

