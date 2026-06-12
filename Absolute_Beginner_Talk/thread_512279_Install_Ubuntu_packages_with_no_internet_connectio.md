---
title: "Install Ubuntu packages with no internet connection?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by jamieh on 2007-07-29
I have two ubuntu PCs, one with an internet connection, and one without, using the PC with a connection, is there a way to get packages on the one without a connection? Can I just get some from Get-Deb and copy the .deb files to a flash drive, and run them, or do I need a connection to install them?

---

### Post by livingtarget on 2007-07-29
EDIT: Of course I didn't really read the post

If it's just packages from Get-Deb then yes you can take them over to the other computer no problem with a flashdrive. Just save the .deb files and launch them on the other computer (assuming it doesn't require the latest versions)

If you want to install a lot of packages then maybe this'll come in handy:
It is something called apt-on-cd, I don't know much about it so I'll just give you the link [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I hope it helps out.

---

### Post by shafin on 2007-07-29
> **jamieh said:**
> I have two ubuntu PCs, one with an internet connection, and one without, using the PC with a connection, is there a way to get packages on the one without a connection? Can I just get some from Get-Deb and copy the .deb files to a flash drive, and run them, or do I need a connection to install them?
On the PC you have internet connection,open synaptic and from the options, make sure all downloaded packages are stored locally in the cache.Then download and install all the packages you need.After that,go to /var/cache/apt and copy everything to the other PC.Then you should be able to click the debs/use command line/make a local source and install them.

---

