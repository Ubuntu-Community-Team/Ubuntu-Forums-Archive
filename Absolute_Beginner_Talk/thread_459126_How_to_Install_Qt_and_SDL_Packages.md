---
title: "How to Install Qt and SDL Packages"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-05-30
Hi I'm playing around with the virtualization software "VirtualBox" so that I can run Windows inside my Ubuntu Installation. It tells me to make sure that I have the following packages installed before  I continue:>  In any case, the following packages must be installed on your Linux system:
•   Qt 3.3.5 or higher;
•   SDL 1.2.7 or higher (this graphics library is typically called libsdl or similar).
When i search for them in synaptic package manager it brings up a lot of different possibilities. when I search for "libsdl" in the name I get 33 results. I don't know which ones to go for. The same is true for "Qt", it brings up around 130.

Could anyone clarify this for me, and maybe explain what VitualBox refer to with that description?

---

### Post by Warbo on 2007-05-30
A good way of getting around this kind of thing is to install some small program which also needs those packages, for instance installing SDLJump will install the most important SDL packages, and installing kpat will probably get relevant QT packages (although kpat might also need a lot of KDE stuff you might not want).

If you are compiling it from source code (usually known as "configure, make, make install") then you should get all of the build dependancies of those packages (the things needed to compile them) using a command like "sudo apt-get build-dep sdljump"

Hope that helps :)

---

### Post by bpill on 2007-12-20
No it does not help...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for sdljump

---

