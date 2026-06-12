---
title: "help with printer install-samsung scx-4725fn"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by nm newbie on 2007-05-30
i have downloaded the drivers from samsung. when i extract the tarball it gives the following:
gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

i then go and try and install following their(samsung) instructions:
[Ubuntu OS Installation]
1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer

upon execution of sudo cdroot/autorun it says it says the following files not found:
libstdc++V3
libtiff.so.3

the install continues till 95% then hangs with the message: cups restart OK.

i close the install. next time i try to boot it's a no go.

 i have reinstalled ubuntu7.04 three times.  :popcorn:


nm newbie

---

### Post by 67GTA on 2007-05-30
Try to install them using the Synaptic package manager and then install the driver.

---

### Post by nm newbie on 2007-05-30
thank you for your info.

tried what you said, it worked!!!

still curious about the tarball error.

nm newbie:popcorn:

---

### Post by 67GTA on 2007-05-30
When you install software from outside of the debian repositories they often are distro neutral and won't contain all of the dependencies required for your application. Then you hope that they are actually in the repositories so you can install them. If they are not then you have to go hunt them down and hope that they don't have unmet dependencies. This used to be called rpm hell, because most rpm distros had this problem. With Debian/Ubuntu  you have deb packages that are built just for your system and should contain all the dependent files needed to install something. Glad you got it going.

---

