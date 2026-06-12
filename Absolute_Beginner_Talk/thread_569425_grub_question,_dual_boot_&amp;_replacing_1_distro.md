---
title: "grub question, dual boot &amp; replacing 1 distro"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-10-07
I dual-boot Ubuntu and Suse on a single hard drive. The partitioning
scheme is very simple, as follows:

/dev/sda1       Fat16
/dev/sda2       Fat32
These first 2 are factory pre-installed by Dell, I don't know what they
are so I leave them alone.
/dev/sda3       Linux swap
/dev/sda4       Extended
/dev/sda5       Ubuntu
/dev/sda6       Suse 10.2

I installed Ubuntu first, used it for a while, then later installed Suse.
Since Suse was installed last, it looks like grub boot files are being located
under the /boot directory of sda6. That is ok for now, when I boot and want to
run Ubuntu I just select it from the menu and away we go, no problem.

However - now I would like to keep Ubuntu, get rid of Suse, and install some
other distro on /dev/sda6. I assume the cleanest way to do this will be to use
gparted live cd to re-format sda6 as ext3 and erase it before installing the
next distro.

Question - since this will wipe the grub files currently used to boot into
Ubuntu, I'm a little worried about this. What is the correct way to free up
sda6 for another distro without losing the ability to boot into Ubuntu? (Hope
I do not need to do a full re-install of both Ubuntu and the new distro!!)

Thanks   -- Bob

---

### Post by meierfra on 2007-10-07
You just need to reinstall grub so that it uses  ubuntu's  menu.lst  rather than suse's. If you google "reinstall grub" you will find lots of guides how to do that. For example:

[Hermanzone]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Actually all you need to do is:

```
sudo grub

```

and at the grub prompt:

```
root (hd0,4)

setup (hd0)

quit
```

The only problem with this is,  that  you wont have "suse" on your grub menu. To fix this

```

gksudo gedit /boot/grub/menu.lst
```

and add  this to the end of the file:


title Suse 10.2
root (hd0,5)
configfile /boot/grub/menu.lst


Then if you select Suse 10.2 at boot up your current "Suse grub menu" will reappear.

---

### Post by logos34 on 2007-10-07
cancel

---

