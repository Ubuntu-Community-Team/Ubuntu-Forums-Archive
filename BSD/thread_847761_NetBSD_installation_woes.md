---
title: "NetBSD installation woes"
date: 2008-07-02
forum: BSD
---

### Post by MaxIBoy on 2008-07-02
Seemed to go okay, until I tried booting. Selecting my Ubuntu installation in the boot menu returned "Error 3," and booting my NetBSD installation failed and gave me a command prompt like this:
db>


Currently using an Ubuntu CD as a rescue distro; I'm installing Ubuntu over the NetBSD partition and letting it reinstall GRUB. That should fix the problem and let me get at my main Ubuntu installation so I can reformat this temporary installation. 


Did I do something wrong?

---

### Post by cardinals_fan on 2008-07-03
> **MaxIBoy said:**
> Seemed to go okay, until I tried booting. Selecting my Ubuntu installation in the boot menu returned "Error 3," and booting my NetBSD installation failed and gave me a command prompt like this:
db>


Currently using an Ubuntu CD as a rescue distro; I'm installing Ubuntu over the NetBSD partition and letting it reinstall GRUB. That should fix the problem and let me get at my main Ubuntu installation so I can reformat this temporary installation. 


Did I do something wrong?
A quick tip: if multibooting with NetBSD, use GRUB or LILO rather than the NetBSD bootloader.  When it offers to install the bootloader, say NO.

---

### Post by MaxIBoy on 2008-07-03
I don't remember being asked that, but I'm willing to try again.

---

### Post by cardinals_fan on 2008-07-03
> **MaxIBoy said:**
> I don't remember being asked that, but I'm willing to try again.
Did you read the NetBSD Guide, possibly the best documentation for any OS?  If not, check out the installation section [here]("http://www.netbsd.org/docs/guide/en/chap-exinst.html#exinst-system-configuration").  You'll be particularly interested in Figure 3.8 (which offers partitioning vs. whole disk install options) and Figure 3.11 (which shows the bootloader installation option).

---

### Post by MaxIBoy on 2008-07-03
No, and thanks for showing me that. *Print*

---

### Post by cardinals_fan on 2008-07-03
> **MaxIBoy said:**
> No, and thanks for showing me that. *Print*
I've installed NetBSD eight times now, so I know the figure numbers by heart ;)

---

### Post by adept_king on 2008-09-02
I cant tell if I installed freeBSD or not.  I edited my GRUB to offer the option of booting the slice i *think* i installed freeBSD, but i get an error and BSD doesnt boot.

im pretty sure i installed it.  i dont even know *how* to know yet.

alot of packages BSD 7 tried to install were missing, and i assume they were on discs 2 and 3.  the cd drive refused to eject during the sysinstall screen whatsoever. so i just skipped those 'packages?', but it was really annoying to sit there and hit cancel over and over during the install.

---

### Post by cardinals_fan on 2008-09-02
> **adept_king said:**
> I cant tell if I installed freeBSD or not.  I edited my GRUB to offer the option of booting the slice i *think* i installed freeBSD, but i get an error and BSD doesnt boot.

im pretty sure i installed it.  i dont even know *how* to know yet.

alot of packages BSD 7 tried to install were missing, and i assume they were on discs 2 and 3.  the cd drive refused to eject during the sysinstall screen whatsoever. so i just skipped those 'packages?', but it was really annoying to sit there and hit cancel over and over during the install.
Why did you post that in this thread?

---

### Post by mips on 2008-09-02
> **cardinals_fan said:**
> Why did you post that in this thread?

Desperation? Use Gag as a boot loader I say!

---

