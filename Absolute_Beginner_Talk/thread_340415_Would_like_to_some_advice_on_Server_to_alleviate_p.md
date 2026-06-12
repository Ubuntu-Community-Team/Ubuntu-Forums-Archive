---
title: "Would like to some advice on Server to alleviate problems."
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by peejaygee on 2007-01-17
Dear All, 

I'm currently running a Windows Server on a small home network, and I'm having a mess around with linux, and stumbled across Ubuntu Server. So here is my questions (as I've searched around a bit and have come across a few possible stumblig blocks)

On my server now I have a few things running, mIRC, Emule, NetLimiter, uTorrent, Email Server, SquidNT, Print Auditer, PeerGuardian 2, TightVNC.

I would like the same all running on a Linux box, but I'm coming across one main thing, Server doesn't come with a GUI as default.

I've downloaded Ubuntu 6.10 Server and installed it on a box I'm planning on using as the server (wanting it all set up, before I start using it). I've gone through the setup, usernames, passwords, etc. Logon fine, changed root password, etc. 

Then I've tried to use aptitude to install a few things, mainly Gnome, but what ever route I go through I can't seem to get a GUI installed.

I know (from various websites) it is advised to use the command line, if I'm running as a server, but as this is a home network, and I'm not running a webserver or FTP, I'm not that worried about major security issues, plus I'm behind a router/hardware firewall. But I'm guessing that with no GUI, I won't be able to run the required programs?

There is a lot of technical stuff out there on the web, lots of tutorials, and explanations, but all of them come across to me as if you need a certain level of knowledge on linux systems.

Can anybody point me in the right directions, tips, examples, own experiances?

Thanks in advance for any info recieved.

Regards
Paul.

---

### Post by [S|G] on 2007-01-17
Hello,

Since you're new to linux, I don't think you should worry so much as not using GUI tools to get the job done. Servers traditionally don't have a GUI in order to reduce security risks: the less things you have running, the better, since you'll have less chances of exposing ports and having vulnerable software.

Also, when you learn to deal with command line tools you get to know how the system works, how to fine-tune the services and you have a degree of flexibility that you'll never have with packaged tools. But sometimes that is a pain; configuring a nice firewall, for example, along with routing and filtering rules would make you wish you never had to touch its script again.

If security and the increased flexibility (and, of course, the knowledge you'd gain) aren't really that important at the moment, it might be better to use a GUI (you don't even have to keep it running, just start it when you need it).

You don't really need a GUI to get things like a webserver and FTP running, since those are usually daemons (system services).

A quick way to have X working would be installing x-window-system-core and gnome packages. To have a more complete environment, you could install ubuntu-desktop (that would leave you with a desktop similar to ubuntu (gnome).

---

### Post by Tomosaur on 2007-01-17
The package you need to install is called 'ubuntu-desktop', although there are variants. I wolud highly recommend you use xubuntu-desktop, since it is more ilghtweight than the ordinary GUI:
```

sudo aptitude install xubuntu-desktop

```

---

### Post by peejaygee on 2007-01-18
Thanks for all the info guys, I've now got an up and running Linux box, with a nice GUI for ease....

I have another question if you don't mind....

On Windows 2000 Server I can add users, and set up privleges with Group Polices, etc so when they log in from another machine, it sets everything up?

Can this be done with Linux too?

---

### Post by peejaygee on 2007-01-20
> **Tomosaur said:**
> The package you need to install is called 'ubuntu-desktop', although there are variants. I wolud highly recommend you use xubuntu-desktop, since it is more ilghtweight than the ordinary GUI:
```

sudo aptitude install xubuntu-desktop

```

I've done a couple of re-installs (as it is so quick, and if I break it, or want to see a cariant, it's dead easy) and tried xubuntu desktop, but there is no remote desktop sharing? as I'm lazy and connect from my main machine. I've got TightVNC on my machine, but I can't seem to find/install the equivilant on Linux? I've been to the TightVNC page, and there is a Linux version, but I can't get it on my box...

Can anybody help?

Regards
Paul

---

