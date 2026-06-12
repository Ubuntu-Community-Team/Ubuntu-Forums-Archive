---
title: "VMWare, login Screen, and dpkg"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Bob Sugar on 2007-02-14
I have 3 issues, 2 of which are tied together:

1. I can't upgrade vmware, or any other software - including ubuntu upgrade because vmware says it is missing a module, or can't start a module called vmnet. It repeatedly goes through a sequence searching for an open tunnel for vmware, and then fails after 2 or 3 tries and asking if I want to over write the existing directory.

2. Another part of the failure above, and also with upgrading other packages is a dpkg failure, and it gives me an instruction to configure dpkg, but I have no idea on how to do this.

3. last, but not least - I am getting notice at startup that my log in screen is crashing - it chooses another, and boots ok, but it's still a little annoying.

Thanks in advance for your assistance, this is my first real attempt at setting up a linux distro and I'm sure I'll have more questions - on the upside though - I was able to get pcmcia wireless working with an unsupported card after only 6 hours of jacking with it. ;)

(my version of Ubuntu is 6.06, and it's running on an HP Pavilion ZE4901US laptop with 1 gb of ram. I don't have the rest of the specifics, but if you need them I can dredge them up - the only things different from stock is that it has the PCMCIA wireless card, a new 80gb HD, and the RAM  upgrade from 256 to 1gb.)

---

### Post by Bob Sugar on 2007-02-14
Also - in Automatix, I can't find an option to upgrade Firefox, not sure if this is supported here, but it seems odd that they wouldn't have a simple Firefox updater instead of trying to divert ytou to something called swiftfox.

Does anyone know of a good, simple Firefox updater so I can get to 2.x from 1.5 without all the headaches?

All these install and setup issues begin to make one miss XP and OSX a little bit...

---

### Post by Bachstelze on 2007-02-14
You definitely shouldn't have installed Automatix. Can you afford a reinstall ?

---

### Post by Bob Sugar on 2007-02-14
afford a reinstall? I can do it, but I'd prefer not to if possible... The first time was brutal enough...lol.

Can I not just uninstall automatix and vmware, and then just use the install manager included with Ubuntu after that?

---

### Post by jvc26 on 2007-02-14
That dpkg thing is the instruction something like dpkg -configure -a or something? You need to type into terminal sudo x (where x is that command) and that will sort that issue.

Sudo apt-get --purge remove automatix2 (presuming you installed it by apt-get) to remove automatix
Il

---

### Post by Bob Sugar on 2007-02-14
Thanks, I'll try those suggestions tonight - anyone have any info on the vmware removal in addition to the "simple upgrade" route for firefox?

---

### Post by jackrobinson on 2007-02-14
has the OP and the folks who are trying to help ever realized that the package which is causing trouble is vmware-player, a broken package in Ubuntu Multiverse and has NOTHING to do with Automatix? The reason why this forum has started to suck is the extremely low quality of help that people get here.. its filled with newbies trying to help newbies and that compounds issues rather than solve them.
Removing and installing automatix will do nothing to solve any of these issues.
The OP needs to post exact errors from terminal on running dpkg/apt. For a much better quality of support, consider going to [http://www.getautomatix.com/forum](http://www.getautomatix.com/forum)

---

### Post by fakie_flip on 2007-02-17
> **Bob Sugar said:**
> Thanks, I'll try those suggestions tonight - anyone have any info on the vmware removal in addition to the "simple upgrade" route for firefox?

Open gnome-terminal Applications>Accessories>Terminal and type vmware. Then hit tab twice, and you will see something similar to this.

```
chris@ubuntu:~$ vmware
vmware               vmware-config.pl     vmware-serverd
vmware-authd         vmware-loop          [COLOR="Red"]vmware-uninstall.pl[/COLOR]
vmware-authtrusted   vmware-mount.pl      vmware-vdiskmanager
vmware-cmd           vmware-ping          
chris@ubuntu:~$ vmware
```

Notice what I highlighted with red.

To uninstall vmware, you need to run that with Admin privileges using sudo. Use this command to uninstall vmware.

```

sudo vmware-uninstall.pl
```

---

