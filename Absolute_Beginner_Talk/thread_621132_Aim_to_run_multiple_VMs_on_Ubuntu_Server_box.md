---
title: "Aim to run multiple VMs on Ubuntu Server box"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by fritserasmus on 2007-11-23
I would like to get away from windows and want to do this on Linix and therefore picked Ubunto because of support:

I have installed Ubuntu Server to be the host OS. I would like to run 4 different WMWare environments on this box. 1) Web server for my photo galleries (I am a freelance photographer) 2) FTP server to make photos available 3) Normal home office apps like file server, print server and other apps 4) Windows XP environment to run those apps unavailable on Ubuntu and games for kids.

I would like to install VMWare Server, but I do not know what the correct package name is for VMWare Server. (apt-get install XXXXXXXXX)
I have also downloaded KDE package in the hope I will be able to configure Ubunto Server via a GUI interface. Did I do the correct thing, or am I stupid here? If I can how do I get to this KDE Windows from the command prompt.

Any pointers would be greately appreciated.

---

### Post by PilotJLR on 2007-11-23
I'm almost sure VMware Server is not in the repos... so just download it from VMware's site and register for a free serial number.

With gnome, you start the gui environment with "/etc/init.d/gdm start". I think with KDE, you just use kdm instead of gdm and you're all set.

Running these VM's at the same time, get lots of RAM and fast hard disks! Anything less than 2GB RAM on this will tank. 4GB would be preferable.

---

### Post by The Cog on 2007-11-23
I agree with PilotJLR - you will need to download the vmware from their site, and follow their install instructions. 

I don't know if you have the whole kubuntu install there. Installing package kubuntu-desktop will definitely give you the whole thing, but before doing that, try the command **startx** from the command line.

---

### Post by HermanAB on 2007-11-23
Agreed - just get it from the VMware web site and follow their instructions to the letter.  It should work.  I've done it many times.

---

