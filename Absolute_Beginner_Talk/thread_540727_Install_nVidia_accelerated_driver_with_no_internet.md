---
title: "Install nVidia accelerated driver with no internet connection?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by jamieh on 2007-09-01
How do I install the nVidia Accelerated Driver on a computer without an internet connection? Can I download a .deb on my other box and transfer it to the no-internet box with my flash drive, and then install it?

---

### Post by Altarbo on 2007-09-02
> **jamieh said:**
> How do I install the nVidia Accelerated Driver on a computer without an internet connection? Can I download a .deb on my other box and transfer it to the no-internet box with my flash drive, and then install it?
Pretty much, it would be easier to burn it to a data cd, but a flash drive should work.

First, download the driver package with:
apt-get install <package name> --download-only

Put the drivers on whatever media you want.  A cd is easiest because you can just run the command "apt-cdrom add" to automate the process of editing sources.list.  If you use any other media you'll have to edit sources.list by hand.

Finally install the package:
apt-get install <package name>

If the computer that has internet access, does not have linux, here are online man pages for the commands I mentioned:
[http://ccrma.stanford.edu/planetccrma/man/man8/apt-get.8.html](http://ccrma.stanford.edu/planetccrma/man/man8/apt-get.8.html)
[http://ccrma.stanford.edu/planetccrma/man/man5/sources.list.5.html](http://ccrma.stanford.edu/planetccrma/man/man5/sources.list.5.html)
[http://ccrma.stanford.edu/planetccrma/man/man8/apt-cdrom.8.html](http://ccrma.stanford.edu/planetccrma/man/man8/apt-cdrom.8.html)

---

