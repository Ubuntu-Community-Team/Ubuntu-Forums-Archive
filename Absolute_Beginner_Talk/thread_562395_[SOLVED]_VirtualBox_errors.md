---
title: "[SOLVED] VirtualBox errors"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-28
Hello.
I just installed the Command Line of Ubuntu, via the alternate cd, I am running it, I installed xorg and firefox, that is how I am here now.

I downloaded VirtualBox from the VirtualBox website, as a debian, I tried installing it. It said it was installed, but yet it wasn't because it didn't have all of the dependencies, so I ran "sudo apt-get -f install", which installed the dependencies.

I added myself to vboxusers via "sudo addgroup drsmall vboxusers",
VirtualBox opens fine, but it will not boot a new virtual system.

It is complaining that the VirtualBox kernel driver is not installed.
It says that /dev/vboxdrv was not created for some reason. I need to figure out how to install that, so I can run VirtualBox, and then run /etc/init.d/vboxdrv setup as root to solve the problem.

Any assistance could be helpful, as I am running this off my other hard drive, and have to open the box and switch SATA wires around to get back to my other hard drive.

Thanks!

Dr Small

---

### Post by bodhi.zazen on 2007-09-28
LOL

Stop Virtualbox, enter these commands :

sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup

(for some reason I usually have to run this command twice)

Re-start virtualbox

---

### Post by Dr Small on 2007-09-28
Same thing.
It told me that "Something went wrong", and told me to read /var/log/vbox-install.log, and it said:
> /usr/share/virtualbox/src/build_in_temp: 61: make: not found

---

### Post by AndyCooll on 2007-09-28
I usually install VirtualBox by double clicking on it and allowing the GDebi Package Installer to take over. It might be worth reinstalling.

:cool:

---

### Post by bodhi.zazen on 2007-09-28
> **AndyCooll said:**
> I usually install VirtualBox by double clicking on it and allowing the GDebi Package Installer to take over. It might be worth reinstalling.

:cool:

The best way to install VirtualBox is to install from the innotek repositories with apt-get or synaptic

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

The method of using GDebi will work just fine as well, but it is somewhat outdated as innotek now maintains a repository.

---

### Post by Dr Small on 2007-09-28
I added the repositories, installed it that way, and still no luck.
I even double checked and made sure my username was in the vboxusers group.

I even tried it as root and still get the error. I have no idea what to do... :|

Dr Small

---

### Post by n3tfury on 2007-09-28
> **AndyCooll said:**
> I usually install VirtualBox by double clicking on it and allowing the GDebi Package Installer to take over. It might be worth reinstalling.

:cool:

OP: i had the same error, so i uninstalled, then reinstalled letting Gdebi installer handle the .deb file from Virtualbox's download page just like AndyCooll

---

### Post by Dr Small on 2007-09-28
Wouldn't it be the same as using dpkg -i ?
I tried that, and it didn't work either, because I first attempted to install it like that, and it didn't work that way either.

Getting gDebi seems like a hassle, since there is alot to download to get all of the dependencies to get it to work.

Dr Small

---

### Post by bodhi.zazen on 2007-09-28
Dr Small : Did you install the dependencies ?

Others: Thanks for the info, good to know. I installed from the innotec repos with no problem (I have also used dpkg and GDebi). My advice is innotec repo > GDebi > dpkg

---

### Post by Dr Small on 2007-09-28
Install the dependencies ?
How would I do that ?

I just tried "sudo apt-get -f install", but there was none found.
Is there another method, or something else I should do to install the dependencies ?

By the way, it keeps saying it is a "VirtualBox kernel driver error", so there lies the problem. Any reinstallation or uninstalling does not seem to be affecting it.

Dr Small

---

### Post by Jose Catre-Vandis on 2007-09-28
Check out my thread about VRDP and command line system install. If this doesn't sort you out, come back to me, I have it working fine. You need linux-sources and headers etc

[http://ubuntuforums.org/showthread.php?t=555996](http://ubuntuforums.org/showthread.php?t=555996)

---

### Post by Dr Small on 2007-09-28
Yahoo! Thanks a million man! That worked flawlessly like a charm. It compiled the kernel, and I no longer get any more errors!

I've been at this all evening, so this is a great relief.
I did install xfce4 so I could do some multi-tasking, and be able to easily copy and paste from the tutorial, so that was was an advantage.

Thanks again man!

Dr Small

---

