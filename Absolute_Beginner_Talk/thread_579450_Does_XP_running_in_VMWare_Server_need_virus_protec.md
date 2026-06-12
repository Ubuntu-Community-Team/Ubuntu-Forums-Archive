---
title: "Does XP running in VMWare Server need virus protection?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by encryptkeeper on 2007-10-18

Hey everyone I have a question (and I'm sure it won't be the last).  When I add an install of XP Pro running under VMWare server, do I need to take all of the precautions to protect my data just like I would  if XP ran natively on the PC?  Things such as antivirus software?

Amd Athlon 64 X2 4400+
2G
320G Seagate SATA
NX 7600GS AGP
MSI K9MM-V
Lite-On 20x SATA DVDRW
AOC 193P+ LCD

---

### Post by blop on 2007-10-18
XP in VM is just as vunerable as XP standalone....so yes.

---

### Post by toddward on 2007-10-18
Yup.

I believe that you can keep a backup image, though, of the install.  In this case, if you do get a virus, simply destroy the old image and start a new one.

---

### Post by encryptkeeper on 2007-10-18
> **toddward said:**
> Yup.

I believe that you can keep a backup image, though, of the install.  In this case, if you do get a virus, simply destroy the old image and start a new one.

Cool, how do I do that?

---

### Post by toddward on 2007-10-18
I think this guide may help.  I've never made an image...yet.  So please let me know how it goes if you end up doing it.

[http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php]("http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php")

---

### Post by compiledkernel on 2007-10-18
I believe that VMware supports snapshots , just use that and rollback when bad things happen. 

[http://www.petri.co.il/virtual_vmware_snapshot.htm](http://www.petri.co.il/virtual_vmware_snapshot.htm)

---

### Post by toddward on 2007-10-18
> **compiledkernel said:**
> I believe that VMware supports snapshots , just use that and rollback when bad things happen. 

[http://www.petri.co.il/virtual_vmware_snapshot.htm](http://www.petri.co.il/virtual_vmware_snapshot.htm)
Interesting.  This seems like it may work better for you encryptkeeper.

---

### Post by tech9 on 2007-10-18
> **encryptkeeper said:**
> Hey everyone I have a question (and I'm sure it won't be the last).  When I add an install of XP Pro running under VMWare server, do I need to take all of the precautions to protect my data just like I would  if XP ran natively on the PC?  Things such as antivirus software?

Amd Athlon 64 X2 4400+
2G
320G Seagate SATA
NX 7600GS AGP
MSI K9MM-V
Lite-On 20x SATA DVDRW
AOC 193P+ LCD

yes

---

### Post by tech9 on 2007-10-18
> **compiledkernel said:**
> I believe that VMware supports snapshots , just use that and rollback when bad things happen. 

[http://www.petri.co.il/virtual_vmware_snapshot.htm](http://www.petri.co.il/virtual_vmware_snapshot.htm)

correct, but you lose any data/apps installed since the snapshot - so it's a good idea to update the snapshots after installs

---

