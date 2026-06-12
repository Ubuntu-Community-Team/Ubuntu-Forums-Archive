---
title: "Getting Kubuntu Installed With Ubuntu"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-04-26
Hello,

I have the regular Kubuntu Feisty installation CD for 386 machines and I am trying to install it on Ubuntu Feisty system so that it can take advantage of a few programs that I have downloaded with a very slow modem and installed on Ubuntu. I am not interested in running Gnome centric applications on a Kubuntu desktop and vice versa, but I want to avoid installing Kubuntu separately on another partition and download programs that I already enjoy in Ubuntu.

I saw old advice on installing Kubuntu on Breezy 5.04 Ubuntu, but it does not work for me.  Here it is: 
To install kubuntu-desktop KDE 3.4 on existing Ubuntu 5.04
insert Kubuntu 5.04 CD
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
logout | end session
Session or Session Type choose KDE, then login.

When I use "sudo apt-get install kubuntu-desktop", it proceeds to download about 180 meg files from over my slow internet connection. How can I get terminal to install from the installation CD and not over the internet? Hanging up the modem does not work, because it can not find the repositories over the internet.

Any help is appreciated? Do I need the alternate install disk for Kubuntu?

Paul M.

---

### Post by nunomiguelmota on 2007-04-27
Hi, 
 
On synaptic you can add a cdrom as repository and that should do what you want....

---

### Post by zvacet on 2007-04-27
Yes you need alternate disc.

---

### Post by pmueller on 2007-04-30
Hello,

Thanks to you I now have Kubuntu. The alternate install disk worked using terminal commands instead of synaptic. Now I guess I will try Xubuntu to see how much faster that distribution is for me.

Paul

---

