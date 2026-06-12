---
title: "Downloading apt files?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-03-01
Alright, so I'm setting up Ubuntu on my computer (fresh install), and I'm trying to set up my wireless adaptor (Linksys WUSB11v4), with help from [this]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") tutorial. But I'm trying to get online, so it's obviously impossible for me to use apt to get packages. I have a computer that's internet ready, is there any way for me to download the files I would get from apt, put them on a flash drive, transfer them, and install them? Thanks a lot.

---

### Post by Kateikyoushi on 2007-03-01
You could get packages from packages.ubuntu.com or use the aptitude download command.

---

### Post by Maestro23 on 2007-03-01
Ubuntu Packages: [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

---

### Post by chimerical_brio on 2007-03-01
Alright, so in the tutorial I mentioned, the package "linux-headers-`uname -r`" is referenced. First of all, on packages.ubuntu.com, there is nothing called linux-headers, and second of all, I have no clue what 'uname -r' references. Help?

---

### Post by Kateikyoushi on 2007-03-01
Try to copy the uname -r in terminal. It shows the linux kernel version you are currently using.
So should get the same version.

Here are some headers I found in edgy. [LINK]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=headers&searchon=names&subword=1&version=edgy&release=all")

---

### Post by chimerical_brio on 2007-03-01
Oi. Sorry. And thanks a bunch.

---

### Post by chimerical_brio on 2007-03-01
Alright, more problems:

When I try to install dpkg-dev, which is needed to install build-essential-11.3, which is needed to install the linux-source headers, which I need for ndiswrapper, everything seems to be fine except for one line, the final line, at which point it stops:

"Checking for C compiler default output file name... configure: error: C compiler cannot create executables."

What can I do to make this work? I'm pretty sure gcc is installed.

---

