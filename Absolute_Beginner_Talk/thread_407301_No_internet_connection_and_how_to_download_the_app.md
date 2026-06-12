---
title: "No internet connection and how to download the applications and install them?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by kanna1620 on 2007-04-12
Hello all! 
                           This is Kanna. I installed Ubuntu few days back and I suggested and installed Ubuntu in my friends PC's. I have internet connection. But my friends does not. As you know the compilers and other applications like xmms music player etc. doesn't  come with Ubuntu installation CD, and have to download from the repositories. For that my friends has no internet connection. So I want to download them for my friends into my PC and copy them into a CD and install them in their Systems. But when I install them I don't know where they are installing i.e the location of the installed files. Now please tell me how to download all of them from repositories and copy them onto a CD.
                           
                         Thanks in advance.

---

### Post by RomeReactor on 2007-04-12
Hi. I suggest you look for the packages (and their dependencies [here]("http://packages.ubuntu.com/"). Make sure you also download the needed dependencies; check on your friend's Ubuntu installation (using Synaptic) to see which dependencies are installed, so you only download those that are not. For example, [this]("http://packages.ubuntu.com/dapper/sound/xmms") is the page for XMMS for Dapper; look at the dependencies listed and search for them on your friend's computer using Synaptic. Take note of those that are not installed, and get them from that page along with the main program. Then copy them to cd, and install them on your friend's pc (starting with the dependencies, and finishing with the program itself, XMMS).

---

### Post by kanna1620 on 2007-04-12
> **RomeReactor said:**
> Hi. I suggest you look for the packages (and their dependencies [here]("http://packages.ubuntu.com/"). Make sure you also download the needed dependencies; check on your friend's Ubuntu installation (using Synaptic) to see which dependencies are installed, so you only download those that are not. For example, [this]("http://packages.ubuntu.com/dapper/sound/xmms") is the page for XMMS for Dapper; look at the dependencies listed and search for them on your friend's computer using Synaptic. Take note of those that are not installed, and get them from that page along with the main program. Then copy them to cd, and install them on your friend's pc (starting with the dependencies, and finishing with the program itself, XMMS).

Thank you very much for the quick reply. Sorry to say that I don't know what to download as there are so many things and I don't understand which to download. Please tell me that also. And how to install after downloading? I downloaded the** xmms_1.2.10+cvs20050809.orig.tar.gz** package. I don't know what are the dependencies that I have to download and how to install them. Please tell me that also.         
                      Thank you very much.

---

### Post by RomeReactor on 2007-04-12
The package you downloaded probably contains a folder with scripts for command-line installation; the packages you download from **packages.ubuntu.com** come in .deb format, so installation is done by just double clicking on them. At this stage you probably don't want to deal with command line installation, so it would be best if get the program and dependencies from that page. Now, according to the ["packages.ubuntu.com" page]("http://packages.ubuntu.com/dapper/sound/xmms") these are some of the dependencies for XMMS:

> * libc6 (>= 2.3.4-1)
      GNU C Library: Shared libraries and Timezone data
* libglib1.2 (>= 1.2.0)
      The GLib library of C routines
* libgtk1.2 (>= 1.2.10-4)
      The GIMP Toolkit set of widgets for X
* libice6
      X11 Inter-Client Exchange library

For the moment, let's imagine that those are the only dependencies; what you do now is note them down and go to your friend's house, and on his Ubuntu system open Synaptic (System-->Administration-->Synaptic Package Manager); now search for **libc6, libglib1.2, libgtk1.2** and **libice6**. If those are all installed, then you only need to download the XMMS package: look for the download links near the bottom of the page, according to his system's architecture--meaning if he's using Ubuntu 32-bit (i386) or 64-bit (amd64), or Ubuntu on a Power pc(powerpc). You install the .deb packages by double clicking on them, which brings up a program called GDEBI to do it.

If after searching on your friend's computer you find it still needs some (or all) of the libraries, just download them from **packages.ubuntu.com**; note that **some of the program's dependencies have dependencies of their own**, so you must also download those; the page for each library (the dependencies) will tell you.

However, an easier workaround for all of this is to have your friend bring his computer to your place and use your internet to connect his computer and download the programs using Synaptic, which will automatically take care of all the dependencies.

---

### Post by kanna1620 on 2007-04-12
> **RomeReactor said:**
> The package you downloaded probably contains a folder with scripts for command-line installation; the packages you download from **packages.ubuntu.com** come in .deb format, so installation is done by just double clicking on them. At this stage you probably don't want to deal with command line installation, so it would be best if get the program and dependencies from that page. Now, according to the ["packages.ubuntu.com" page]("http://packages.ubuntu.com/dapper/sound/xmms") these are some of the dependencies for XMMS:

However, an easier workaround for all of this is to have your friend bring his computer to your place and use your internet to connect his computer and download the programs using Synaptic, which will automatically take care of all the dependencies.

Thank you very much., RomeReactor.

---

### Post by Bushfire on 2007-04-12
Yeah, dependencies get very painful, once you get to programs more involved than XMMS. It's very doable though.

---

### Post by kanna1620 on 2008-05-03
We can also do one thing. If we have an Ubuntu system with internet connection then we can download those package files with dependencies to the current directory using the following command.

```
sudo aptitude download <package name>
```

Now, the system will download all the package files and their dependencies and you can take them to the system which has no internet connection and install there.

---

