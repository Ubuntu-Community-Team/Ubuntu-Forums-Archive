---
title: "Could someone please tell me an easy way to download &amp; install programs"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by FOBBEDOFFWITHCRAP on 2007-09-28
HELLO PEOPLE
I have been learning linux and i love it all apart from trying to install programs.
I have downloaded firestarter onto my pc and i need to know how i can get firestarter to boot up with the pc.
I also need to know how i set up a folder for downloaded programs.
Many Thanks
Dave

---

### Post by bruce89 on 2007-09-28
Linuxes tend to use Package management, see [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

If you have any issues, just ask.

---

### Post by Malibu Illusion on 2007-09-28
You should check out:

System > Administration > Synaptic Package Manager

That makes it easy to select and install programs from the repositories, in case you were unaware of their existance and nature.

In regards to Firestarter: you do not need it to boot up with your PC.  Firestarter is a GUI frontend for the firewall that comes built in to the Linux kernel: netfilter (iptables).  You should only be requiring to launch Firestarter when you wish to make configuration changes to your firewall.  Having it always running is actually a potential security risk as it would require to run with root permissions all of the time and minimizing on the applications you execute as root is always a good idea.

I'm unsure as to what you mean when you talk about setting up a folder for downloaded programs.  If you just want a folder under your home directory that you wish to put programs that you download in, that's as simple as navigating to your /home directory, right clicking and selecting "create folder."  Otherwise, anything you install through Synaptic. or the repositories generally, is automatically installed within your system folders which exist to house programs, such as /usr/bin

Take care.

---

### Post by bruce89 on 2007-09-28
```
sudo aptitude
``` is my preferred way of installing packages.

---

### Post by FOBBEDOFFWITHCRAP on 2007-09-28
thank you 
How do i get to my home directory to add a folder please

---

### Post by Conradle on 2007-09-28
> **Malibu Illusion said:**
> You should check out:

System > Administration > Synaptic Package Manager

That makes it easy to select and install programs from the repositories, in case you were unaware of their existance and nature.

In regards to Firestarter: you do not need it to boot up with your PC.  Firestarter is a GUI frontend for the firewall that comes built in to the Linux kernel: netfilter (iptables).  You should only be requiring to launch Firestarter when you wish to make configuration changes to your firewall.  Having it always running is actually a potential security risk as it would require to run with root permissions all of the time and minimizing on the applications you execute as root is always a good idea.

I'm unsure as to what you mean when you talk about setting up a folder for downloaded programs.  If you just want a folder under your home directory that you wish to put programs that you download in, that's as simple as navigating to your /home directory, right clicking and selecting "create folder."  Otherwise, anything you install through Synaptic. or the repositories generally, is automatically installed within your system folders which exist to house programs, such as /usr/bin

Take care.

How, then, do you get iptables to start on boot? I have VNC on my server, if I use any old computer with a client I can access it unless I start Firestarter, which I have a rule in to block that port (I tunnel through SSH otherwise). So evidently iptables isn't starting until I start Firestarter.

---

### Post by bruce89 on 2007-09-28
> **FOBBEDOFFWITHCRAP said:**
> thank you 
How do i get to my home directory to add a folder please

```

cd ~
mkdir <folder name>

```

Respectively.

Packages aren't installed to your home directory though, their files are scattered about in /usr.

---

