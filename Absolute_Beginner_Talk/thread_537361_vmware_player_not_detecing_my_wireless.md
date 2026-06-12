---
title: "vmware player not detecing my wireless"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by qfwills on 2007-08-28
Hi

I have Feisty on my Compaq nx8220

I've just used [www.easyvmx.com](www.easyvmx.com) to create a virtual drive, installed vmware player from the repository and installed Windows XP Home Edition. Problem is that it doesn't pick up my wireless. Am I being stupid? Can vmware player only access the internet via an ethernet connection?

---

### Post by aspen_dv on 2007-08-28
Open your virtual machine setting in VMware, change Ethernet to NAT (not bridge). That should pick up the ip address from your host (Ubuntu).
You might need to restart you VM machine after the change.

---

### Post by qfwills on 2007-08-29
Thanks but.... hmmm:

I have 5 things in the tool bar, it is showing:
[B]CD-ROM
Serial Port (failing to detect)
Parallel Port (failing to detect)
Ethernet (it is on NAT)
Sound Adapter (sometimes fails to be detected, mmmm)[/B]

Any help would be superb. I've already faffed around a lot with this and am at wits end :)

---

### Post by qfwills on 2007-08-30
anybody?

---

### Post by spupy on 2007-08-30
Im using vmware server but i hope things aren't that different.
With ethernet you can use NAT or Bridged internet connectio. With wireless you can have only NAT, bridged is not supported for wifi. I also think that for the guest os the connection will not be shown as wifi but as cabled, no matter what it really is. 
Make sure to install VMware tools in the Guest OS, they improve things ALOT!

---

