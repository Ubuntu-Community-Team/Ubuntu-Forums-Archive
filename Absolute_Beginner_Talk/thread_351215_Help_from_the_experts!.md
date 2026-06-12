---
title: "Help from the experts!"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by adamballa on 2007-02-01
Hello my fellow ubuntuians,

This is going to be my first post. I have been running desktop version 6.10 on two test machines. I freaking love it myself. I also just ordered some copys of 6.06. Now is the part where I setup a question for the experts. I'm currently working on setting up a fileserver using samba. This server will be used to save artwork for our production department. These file  formats will include .jpg, .eps, .ai, .psd, and so on. I also wanted to set it up for "fakeraid" using dmraid. My question is kind of a three parter. 

1. Which version would you guys/gals suggest I use 6.06 or 6.10?

2.  I'm still learning so I'm more comfortable with a gui frontend. I know there is a server and desktop distro of both versions. Would it be ok to use the desktop version for this type of setup?

3. I've done a little bit of reading about dmraid. However it seems fairly tricky to setup. Is it really that hard to setup?


Below are the specs of the machine that i'm working on. I'm currently just working off the 6.06 live cd. 

Asus A8N-E
amd64 (not sure)
1 gig of ram
2x 120g western digital drives
1x pci-e video card

Thanks for reading this post. Thanks in advance for your responses. Note that I'm currently just running the 32 bit version. 

P.S.
UBUNTU ROCKS!:guitar:

---

### Post by Sef on 2007-02-01
> 1. Which version would you guys/gals suggest I use 6.06 or 6.10?

For a business, I would recommend 6.06.  1) 6.06 (Dapper Drake) is Long Term Stable, so there is support for the desktop until 6 2009 and for the server until 6 2011.    For 6.10 (Edgy Eft), the support for both only lasts until 4 2008.

> 2. I'm still learning so I'm more comfortable with a gui frontend. I know there is a server and desktop distro of both versions. Would it be ok to use the desktop version for this type of setup?

Yes, though there may be commands that you need to do from the command line.

---

### Post by glabouni on 2007-02-01
I'm far for being an expert but I'd say:

1. 6.06 LTS dapper drake suits more a production platform:

> Note:If you have no compelling reason to upgrade to Edgy, please consider staying with your current version. As with ANY Operating System upgrade, it is important to fully back up your system before attempting the process.

"Compelling reason" here does NOT mean "well, I want to be as up-to-date as I can be." If you can't think of a single thing that's in Edgy that you can't live without, then you probably don't have a compelling reason. 

Also note that Edgy 6.10 is considered a development platform for testing new ideas,and technology. Use of this version,and coming versions there after are at your own risk. 

First Time Linux/Ubuntu users are advised to use dapper,and not edgy as their frist step into Linux.
[http://ubuntuforums.org/showthread.php?t=286209](http://ubuntuforums.org/showthread.php?t=286209)

2. server version does not provide a GUI by default and offer many features not needed for your intended usage. IMHO a desktop version should suit your needs. (actually the differences between server and desktop is a matter of what packages are on the cd and installed by default.)

3. I can't help with this one. never looked into it.

---

### Post by adamballa on 2007-02-01
Heya thanks Sef and galbouni for such a quick response. Looks like I'll go ahead and use dapper. However Sef would you recommend any other raid solutions? I really don't have the extra cash to spend on scsi drives and a controller.

Thanks,
Adam

---

### Post by tomm3h on 2007-02-16
True S-ATA hardware RAID is available on a wide range of products from companies such-as [3Ware]("http://www.3ware.com"), but you could easily spend £200 (270-300USD?) on an adapter card, before even considering drives.

Other posters have probably quite-rightly suggest Dapper for a business environment, however take it from me; Edgy's support for dmraid is a *nightmare* to setup. I'm not unfamiliar with Linux from a command-line, and I struggled greatly.

There is no way you'll manage it with a GUI. Dapper's configuration extends complication because the version of grub is even less tolerant of dmraid setups (read: manual setup required).

I'd strongly urge you away from using fakeraid, to either software RAID from within Linux or to using a dedicated hardware RAID solution; the latter of which would eliminate any issues, and provide the greatest performance/reliability available.

I'm lead to believe software RAID and fake RAID aren't too dissimlar in performance and both are essentially free -- but the headache(s) involved with fake RAID just aren't worth it.

Good luck :)

---

