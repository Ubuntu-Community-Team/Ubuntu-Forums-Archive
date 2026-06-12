---
title: "cant install Ubuntu"
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by mikey34 on 2005-06-07
i looked all over for the answer to this simple question and can't find it. what are the **minimum specs** needed to run ubuntu? i have an old **233MHz with a fresh 8Gb hard drive ** in it. i know that is pretty beat but this is just for messing around.  When i let Ubuntu load it goes to the end of the progress bar and then restarts, it never actually loads to a desktop or a cmd prompt. thanks guys, and apologies if this question is beneath you.

-mike

---

### Post by emperor on 2005-06-07
The amount of RAM memory is the critical thing, at least with Gnome or KDE. I install Ubuntu on an old Dell Inspiron 3200 laptop over the weekend; PII 266 CPU, 4G hard drive, 64M memory. It only used about half the drive (1.9G's) for the installation and subsequent add's. The install took about 3 hours due to the limit amount of RAM memory. I just ordered 2 sticks of 64M SODIMM ram to upgrade the memory to the maximum of 144MB; replacing the 16MB and 32MB SODIMM's that are in the machine with the new ones. Since the laptop was using 40MB of ram and 50 MB of swap with 64MB of RAM, I think it will run Ubuntu OK in 144MB.. Most specs on modern Distro's recommend a minimum of 192MB if you are using Gnome or KDE. Other lite-weight GUI's like Xfce or Icewm require less ram memory.

A friend gave me the laptop, it had a broken keyboard and an internal support was cracked. However, I found a duplicate Dell Inspiron 3200 shell with a good keyboard for $10, a PCMCIA ethernet card for $7, and two sticks of 64MB SODIMM ram for $10 each. I'll have $50 in it or so when I am finished. It will make a nice laptop for my 13 year old daughter who also runs Ubuntu on her desktop!:)

---

### Post by az on 2005-06-07
The minimum specs are displayed before the install starts.  Press the F keys to see all the help pages.

Installing with 32 megs or less is problematic.  Everything runs from a ramdisk, you see...

If you are a real die-hard, you can install Debian Woody  and then dist-upgrade to Hoary,  You will not have a comfortable system with that small amount of ram, but it will install.

Install Debian Woody base system (find the netinstall cd)  Log in and do
apt-cdrom add 
to add the Hoary cd to your repository listing.

apt-get update

apt-get dist-upgradee

apt-get install ubuntu-desktop.

---

### Post by wvslkr on 2005-06-07
Ubuntu or Kubuntu will run fine on a 233.  I am using one to post this.

The critical thing, as already posted is ram.  I have 192meg and run both Gnome
and KDE.  It is not a speed demon, but usable as a web browser and word processor.
Stream music fine .  Pretty much forget video.

If you have 64meg ram and can't install I would suggest a bad cd burn.  Also if you 
only have that much ram any X programs are going to perform slowly if at all.

In short if you want to run X I would say 128meg minimum.

Good Luck :)

---

