---
title: "Ubuntu in a Virtual Machine VMware"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by sng_ on 2007-02-09
Hello, 
I've intalled VMWare workstation edition in my laptop and works great with the VM I have running XP.

Now, I've tried to boot Ubuntu in a new Virtual Machine (360 Mb RAM, 4 GB disk) but I got stuck after loading the  initial drivers. After the first line that appears below the Ubuntu logo, the CD drive stops and nothing happen.

I/ve tried different configurations in the virtual machine but nothing seems to be working.

If I boot the CD in the REAL machine, Ubuntu works perfect.

What I am doing wrong?
:confused: 

Regards 

sng_

---

### Post by brpadington on 2007-02-09
Vmware has a boot menu just like most computer bioses do. I think it is F2 that you hit to go nto the menu. On my windows pc i had to disable daemon tools before it would boot. It may also be possible to go into the settings on the virtual machine and make sure it is pointing to the proper device.. I hope this helps. I am at work and don't have my vmware in front of me.

---

### Post by Seaker on 2007-06-07
> **brpadington said:**
> Vmware has a boot menu just like most computer bioses do. I think it is F2 that you hit to go nto the menu. On my windows pc i had to disable daemon tools before it would boot. It may also be possible to go into the settings on the virtual machine and make sure it is pointing to the proper device.. I hope this helps. I am at work and don't have my vmware in front of me.
Actually, the trick is to <click> inside the VM just after you power it on.  This gets the focus inside the VM.  Then you hit <Esc>.  If you do it soon enough, VMware will bring up a boot menu from which you can select the virtual CD to boot from.

---

