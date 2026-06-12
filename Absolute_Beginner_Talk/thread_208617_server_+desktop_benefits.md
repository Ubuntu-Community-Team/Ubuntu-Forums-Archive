---
title: "server +desktop benefits?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Bob Walsh on 2006-07-03
Just installed Ubuntu Server on a new box. Want to use said box for private dev/testing using VMware, LAMP, Subversion, etc. Haven't used a command line prompt since DOS.
How do I:
a) install Gnome desktop from command prompt (bob@PE1800:~$ bash?) and
b) make desktop run on boot.

(I realize I could have just installed Ubuntu desktop, but the box has 8 GB of RAM and I *think* Ubuntu desktop cannot address it all.

---

### Post by az on 2006-07-03
[QUOTE=Bob Walsh]Just installed Ubuntu Server on a new box. Want to use said box for private dev/testing using VMware, LAMP, Subversion, etc. Haven't used a command line prompt since DOS.
How do I:
a) install Gnome desktop from command prompt (bob@PE1800:~$ bash?) and
b) make desktop run on boot.

(I realize I could have just installed Ubuntu desktop, but the box has 8 GB of RAM and I *think* Ubuntu desktop cannot address it all.[/QUOTE]
sudo apt-get install ubuntu-desktop

Also, install a kernel for your architecture (686, k7 smp...)
ex:

sudo apt-get install linux-686

---

### Post by Bob Walsh on 2006-07-03
AZZ - thanks for the help! Being a windows desktop kinda developer, I'm confused re "install a kernel for your architecture (686, k7 smp...)" - I thought the Linux kernal was already installed when I installed Ubuntu Server...

---

### Post by brentoboy on 2006-07-04
a kernel is installed when you installed the "server" install.
but, the default kernel (the one it installed) is compiled so that it runs on any 386 or better.

by using apt-get install linux-686 you get a kernel that needs a P2 or better in order to run, but is much faster becuase it drops backward compatability.

if you use an amd, maybe the linux-k7 kernel is for you.

they are all built from the same source, its just that the compile flags are changed for each one.
--
If im not mistaken, you seem to believe that the server and the desktop versions of ubuntu are somehow different.  That is a windows phinominon (spelling?), in ubuntu, all the same stuff works whether it is a server or a desktop.

you could start with a desktop install, and add LAMP components, or start with the server install and add a GUI desktop.  same end result.  except, the new server cd makes it easy to add LAMP without doing a bunch of extra hand editing of config files.

I have a suspicion that 2GB of ram is all it really uses no matter how much you have.  my box has 4GB and I dont think it knows how to get up there.  I could be mistaken on this though.

if you use the package manager (synaptic:  system>Administration>Synaptic...) you will notice down in the area where all the kernel binary's are listed there is a package named "linux-image-2.6.15-25-server",  I believe it is compiled with the preemptive threading set to switch processes at a slower rate.  that will allow "services" (aka daemons) to be more responsive.  becuase the processor spends less time switching processes, and more time running them.  but, it makes the desktop seem less responsive, because apps dont get a cut of the processor as often.

anyway, you can add "all" of the kernels that interest you, and your boot menu will offer them all to you.  You can select the one you want to try out when you reboot, and then, once you have one you like you can uninstall them the same way you added them.

---

