---
title: "error installing applications"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by CPImmanuel on 2007-09-08
I have somehow got my system into a state where it appears to think that it is running a software management application such as Synaptic Package Manager or Update Manager.  I downloaded the latest version of VirtualBox (version 1.5 for the Fiesty release of Ubuntu) and when I try to intsall it, I get an error message, "Only one software management tool is allowed to run at the same  time.  Please close the other application , e.g. "Update Manager", "aptitude" or "Synaptic" first. " When I looked as the processes that are running, I do not see anything that I can readily identify as a software management tool. Can anyone help? Thanks, Paul Immanuel.

---

### Post by Beggar on 2007-09-08
Alright so the error your getting means that it thinks there is another update manager is running, the way the system keeps track of this is with a lock file. If that file get stuck on the system and not removed by the program that added it you would need to manually remove it.

```

sudo rm -f /var/cache/apt/archives/lock

```

Then try and install updates again.

---

### Post by CPImmanuel on 2007-09-08
Thanks.. That appears to have fixed the problem... However I am wondering if I got into this state because I had tried to install VirtualBox 1.5 and I already have version 1.4 on my machine. Do I need to un-install it before I install the new version? Although I have Windows 2000 installed as a guest OS under the virtualbox, I don't mind losing it, since I have not installed any windows applications yet.  This was just a trial ...once I decide which viirtual environment I want to use, I will install the OSes that I want....(Windows XP, OS/2  (--yes OS/2) ) etc. 

Thanks,

Paul Immanuel

---

### Post by Beggar on 2007-09-09
This state is generally caused by a system crash, or one of the update programs crashing. I.E. If synaptic package manager crashed, or your computer crashed, or even lost power while synaptic was open. This will cause synaptic to never properly close, leaving that lock file stranded on your system.

---

### Post by andremariz on 2007-11-01
Hi, i had the same problem and solved like u describe it.But now it wont connect to the pacages they all fail.Can you help me.

[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Não foi possível ligar a pt.archive.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-pt_PT.bz2:](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a pt.archive.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-pt_PT.bz2:](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a pt.archive.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-pt_PT.bz2)
[http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-pt_PT.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-pt_PT.bz2)
[http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:) Não foi possível ligar a archive.canonical.com:80 (1.0.0.0), a conexão expirou
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-pt_PT.bz2:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a archive.canonical.com:80 (1.0.0.0), a conexão expirou
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Não foi possível ligar a security.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-pt_PT.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a security.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-pt_PT.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a security.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-pt_PT.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-pt_PT.bz2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-pt_PT.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Não foi possível ligar a archive.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-pt_PT.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a archive.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-pt_PT.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-pt_PT.bz2:) Não foi possível ligar a archive.ubuntu.com:80 (1.0.0.0), a conexão expirou
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-pt_PT.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-pt_PT.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-pt_PT.bz2)
they all fail...

---

