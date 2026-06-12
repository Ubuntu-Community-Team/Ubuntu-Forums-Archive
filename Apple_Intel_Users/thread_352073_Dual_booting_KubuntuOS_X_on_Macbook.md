---
title: "Dual booting Kubuntu/OS X on Macbook"
date: 2007-02-02
forum: Apple Intel Users
---

### Post by galvatron1983 on 2007-02-02
In april Im planning on upgrading from my Powerbook G4 to a Macbook. Im hoping to run Kubuntu on it in some form or another, either by dual booting or using parallels desktop software. I was just wondering which one would be the better option.

Is it easy to partition the macbooks hd? And if so is the Kubuntu install procedure easy on a Macbook? Are there issues with drivers due to the intel chipset? Can you mount the OS X partition easily?

Or is running in parallels a better option?

Any help you guys could give me would be appreciated.

---

### Post by Hendrixski on 2007-02-03
I just installed Ubuntu on a Mac with a friend.  The installer has some querks where if you used OSX to partition it then the ubuntu installer won't recognize the remaining partition, so you have to create it as a new partition with gparted, and then click back and it'll detect it :)

I'll know more later, but it looks like there's a problem with the screen

---

### Post by pauljwells on 2007-02-04
Parallels has excellent support for Windows XP, but it's rubbish for Linux.

I have a Macbook Pro. I used Bootcamp to set up a partition for ubuntu (you need bootcamp to give BIOS emulation, which is essential for 3D graphics support) and the installation was easy - the only complication was the need to install rEFIt in both OSX (easy .dmg install) before the installation, and also in the Ubuntu live machine (easy .deb install) during the ubuntu install.

Keep Parallels for windows XP (check out coherence mode - amazing!)

If you don't mind waiting a few months for VMWare Fusion to come out of beta, that will be a far superior product for linux support in VMs on OSX

---

### Post by galvatron1983 on 2007-02-04
I know I want to have OS X and Kubuntu as theyre the OSes I use the most, and it seems like Id be better off dual booting to maximise the speed of the core 2 duo processor. As you are installing with a standard x86 Kubuntu disc does this mean that you can install all of the multimedia codecs in kubuntu, as well as java, flash? This was one of the big limitations Ive had with Kubuntu on my PowerPC Mac.

---

