---
title: "Oneiric 11.10: Epic Fail on Powerbook G4"
date: 2011-11-27
forum: Apple Hardware Users
---

### Post by serpetiello on 2011-11-27
I have a Powerbook G4 (Feb.2005). I already had problems with 11.04:
[http://ubuntuforums.org/showthread.php?t=1770355](http://ubuntuforums.org/showthread.php?t=1770355)


I just tried to install Ubuntu 11.10 Oneiric. Burnt a DVD with the 700+Mb PPC ISO and booted.

Installation went almost flawless; only 2 points needed attention.


1)  swapspace was set to 3+Gb, while I have only 1Gb RAM; I think the swap area should be no larger than RAM size.

So I used the advanced partition management (instead of just pressing "Install") but found that the first two partitions had to be reassigned to "Newworld boot" type and "newworld" type respectively. The onscreen label still says "undefined".

Then I erased the swap area, enlarged the root partition by more than 2Gb, and then re-created the swap area. Installation went OK.


2)  I had no internet at the moment. At the end of the installation it tried to access some "mirror" but failed and presented some error dialogs.

Just ignored them, and clicked on "Restart".


Real pain begins here.

Alas, it did not reboot. The display became full of junk pixels and hang there. After manual reboot, Ubuntu did not start. I had to enter OpenFirmware (cmd-alt-O-F at boot), enter reset-nvram and reset-all commands, then enter OpenFirmware again and boot using:

```
 boot  hd:2,\\yaboot
```But it did not start the Linux kernel. After some investigation I found it did not install anything in the yaboot partition (the "800k newworld" partition, actually larger than 800k).

So I booted again the UbuntuPPC install CD, opened a terminal and mounted the root partition on a local directory:
```
 sudo mount /dev/sda3 /mnt
```and then recreated the yaboot configuration:
```
 sudo yabootconfig -b /dev/sda2 -r /dev/sda3 -t /mnt
 sudo umount /mnt
```Finally, the yaboot was loaded and able to start the kernel.

Real BIG pain starts here. The yaboot configuration uses an UUID instead of /dev/sdaXXX, thus the kernel 3.0.0-12 was not able to mount the root directory.

I rebooted with the install CD again and edited the  yaboot.conf adding the missing line "root=/dev/sda3" but the kernel still panics at boot complaining that it cannot find a root partition and that does not know any partition (as if the Mac-partitions support was not in the kernel).

I am now stuck at this point...:guitar:
Last working release was Ubuntu/PPC 10.10.

---

### Post by serpetiello on 2011-12-11
I was finally able to boot in Ubuntu 11.10 PPC.

I did not get results neither with *rootwait* nor using *root=08:03* on kernel command-line.

I  casually found that the installer always failed to setup correct links to  kernel and *initrd*. The *initrd* file is not in */boot*, neither anywhere on the  root partition. Also, the root link to */boot/vmlinux-3.0.0-12* was broken  (pointed to ppc64), and -worse- the *yaboot.conf *pointed to the 3.0.0-12  kernel (thus next security release would never be used). So I just  restarted the install disk, threw in the kernel/initrd found on the  install CD (in the */casper* directory) and finally was able to boot.

Sadly all settings  (language, user, timezone, etc) were not there: only a guest account was  available, thanks to that braindamaged installer. Forget sudo and anything privileged. I had to start again  the installer (to have a working command-line and mount the root partition) and  manually "chroot" on the root partition and then *useradd* myself and  then reconfigured everything (I had even to specity that my shell is */bin/bash*). Great, like our first Linux installations  back in 1994...

Some of the first long-term bugs recognized:

- my Wacom Graphire4 is not recognized (on x86 Ubuntu it works), "Wacom tablet" menu does not show anything (I bet the current driver doesn't work on big-endian machines)

- the "dancing external display" bug is also there (never, NEVER try to change the default "mirror screen" setup!), probably a bug in the Xorg stuff

- Powerbook keys (volume, LCD brightness, keyboard brightness, etc) do not work; funny, the multimedia keys on the external USB keyboard do work;

-  the Powerbook LCD display is always ON with brightness maxed out, even when the external display goes to sleep  mode. This is not a bug of the powermanagement or screensaver: the brightness keys do not work: on Ubuntu PPC 10.10 they worked;  PPC 11.04 introduced the bug, 11.10 does not solve it. Apparently it is a  problem with ***pbbuttonsd*** (whose configuration keeps "commented" by  default the *TAG_LCDBRIGHTNESS*; using *pbbctl* on the same tag always  reads "-1").

- NetworkManager does not work anymore on any wired  interface except *eth0*, even specifying the correct MAC address. I have  to manually configure *eth1* (an USB ethernet interface). Adding a WiFi dongle just works.

Funny: the internal Broadcom wifi requires b43-fwcutter; an external 802.11n Ralink USB wifi dongle worked out of the box.

The Opera browser (the latest PPC build: Opera 10.63 build 6450) works; had to install it using [I]dpkg -i

[/I]I also had to create a brand new */etc/apt/sources.list *because it was absent. Now it contains:```
deb http://ports.ubuntu.com oneiric-backports main restricted universe multiverse
deb http://ports.ubuntu.com oneiric main restricted
deb http://ports.ubuntu.com oneiric multiverse
deb http://ports.ubuntu.com oneiric-security main restricted
deb http://ports.ubuntu.com oneiric-security multiverse
deb http://ports.ubuntu.com oneiric-security universe
deb http://ports.ubuntu.com oneiric universe
deb http://ports.ubuntu.com oneiric-updates main restricted
deb http://ports.ubuntu.com oneiric-updates multiverse
deb http://ports.ubuntu.com oneiric-updates universe
deb-src http://ports.ubuntu.com oneiric-backports main restricted universe multiverse
deb-src http://ports.ubuntu.com oneiric main restricted
deb-src http://ports.ubuntu.com oneiric multiverse
deb-src http://ports.ubuntu.com oneiric-security main restricted
deb-src http://ports.ubuntu.com oneiric-security multiverse
deb-src http://ports.ubuntu.com oneiric-security universe
deb-src http://ports.ubuntu.com oneiric universe
deb-src http://ports.ubuntu.com oneiric-updates main restricted
deb-src http://ports.ubuntu.com oneiric-updates multiverse
deb-src http://ports.ubuntu.com oneiric-updates universe

```Thus, once on-line, I was able to run *apt-get update && apt-get upgrade* and also install some 1Gb extra software (mainly *lyx* *gimp* *mplayer *and other stuff). To install Arduino environment, I had to fetch the* librxtx-java *Debian package and install it manually before installing Arduino.

Anyway, the ugly bug of the **LCD display brightness always maxed out **makes the Powerbook less than a little useful, because I'll have to shutdown it every time I don't need it for a few hours.

---

