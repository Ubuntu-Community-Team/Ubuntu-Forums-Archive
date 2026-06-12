---
title: "ubuntu will not boot...."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by matt_tee on 2007-05-08
I have installed ubuntu,everything went well, i have windows xp and pclinuxos on a tri boot.

restarted the computer, ubuntu is set as default, it boots up to a orange/pink screen, cursor is present and can be moved, but nothing happens. it just stays on that screen with no menus...

xp and pclinuxos work ok, but cannot get ubuntu to boot..

any ideas???

---

### Post by FurryNemesis on 2007-05-08
Lack of correct video drivers? X not configured properly? What's your videocard?

---

### Post by matt_tee on 2007-05-08
its a pny geforce 5700le.

---

### Post by matt_tee on 2007-05-08
ubuntu edgy eft worked fine, shouldn't fiesty?

---

### Post by FurryNemesis on 2007-05-08
And are you using the nvidia driver for it instead of the nv one? I ask because your X session seems to be starting (you've got colour and a mouse cursor) but seems to be hanging - which says to me wrong video drivers.

---

### Post by matt_tee on 2007-05-08
how do i install the correct drivers?

off the live cd terminal? or in diagnosis mode from boot option?

any ideas?

thank you.

---

### Post by FurryNemesis on 2007-05-08
Ok. Get yourself to a command line by hitting esc when Grub starts loading, selecting your most up to date kernel version and hitting e . Add the option - single -  minus dashes to the end of that line. Hit b. Log it at the command line prompt and do sudo aptitude install nvidia-glx nvidia-kernel-common nvidia-settings and the linux-restricted-modules for your kernel (uname-r to find that out)

Once you've got those packages installed, repeat the above procedure for getting yourself a command line and then do sudo dpkg-reconfigure xserver-xorg. Select Nvidia from the list of graphics drivers when it comes up and hopefully that should be it.

---

