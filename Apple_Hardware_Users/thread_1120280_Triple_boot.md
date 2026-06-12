---
title: "Triple boot?"
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by 311005901 on 2009-04-08
Ok. This is what I would like to do.

I want to buy an iMac and triple boot Ubuntu, Vista, and OSX.
Has anyone tried this? Is it worth it?

I don't want to shell out a grand or two and find out I'm missing a million drivers.

---

### Post by cyberdork33 on 2009-04-08
yes.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by 311005901 on 2009-04-09
So it is worth it?
Do I use Bootcamp, Parallels, or VMWare?

---

### Post by cyberdork33 on 2009-04-09
> **311005901 said:**
> So it is worth it?
That is a personal question. If you need all three to run native then sure.
> **311005901 said:**
> Do I use Bootcamp, Parallels, or VMWare?
Well, Bootcamp is really just a set of tools to help you partition your hard drive and install windows.

Parallels and VMWare makes virtual machines. Installing in one of those is not the same as "triple booting". If you are just playing with Ubuntu, or if you need access to windows / Linux without having to reboot, then a VM might be right for you. (Of course, I would recommend the use of VirtualBox, which is free, over the two commercial applications you mentioned).

---

### Post by 311005901 on 2009-04-10
Thanks cyberdork33! :popcorn:

What I meant by "is was worth it" was if finding the drivers (bluetooth, DVD read/write, camera, audio, network) for Ubuntu or Windows was difficult or if they were ready out of the box?

Anyway, I want to triple boot, so I guess that VMWare , Vitrualbox and Parallels won't work for me. Thanks for clearing that up! That could have been an expensive mistake.

Does Bootcamp support ext4, NTFS, and HFS or will I have use other partition programs (like gParted)?

---

### Post by cyberdork33 on 2009-04-10
> **311005901 said:**
> What I meant by "is was worth it" was if finding the drivers (bluetooth, DVD read/write, camera, audio, network) for Ubuntu or Windows was difficult or if they were ready out of the box?
The windows drivers are provided by apple. They are on your Leopard Install DVD (part of "bootcamp").

You can get an idea of the work needed for Ubuntu on your Mac by checking out the documentation for your hardware revision:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

> **311005901 said:**
> Anyway, I want to triple boot, so I guess that VMWare , Vitrualbox and Parallels won't work for me. Thanks for clearing that up! That could have been an expensive mistake.
Again, VirtualBox is free, so if you want to just try something out, that is a good way to go.

> **311005901 said:**
> Does Bootcamp support ext4, NTFS, and HFS or will I have use other partition programs (like gParted)?
bootcamp only supports windows, and I think it uses FAT32 by default. For more details on the options avaialble to your for partitioning, please read the Installation Documentation I linked to in the second post of this thread.

---

### Post by 311005901 on 2009-04-11
Thanks again!
I'm going to order one and try it.
Can I PM you if I have any problems?

---

### Post by cyberdork33 on 2009-04-11
> **311005901 said:**
> Can I PM you if I have any problems?
Please post in the forums so that others can help.

Good Luck

---

### Post by raymondh on 2009-04-11
> **311005901 said:**
> Ok. This is what I would like to do.

I want to buy an iMac and triple boot Ubuntu, Vista, and OSX.
Has anyone tried this? Is it worth it?

I don't want to shell out a grand or two and find out I'm missing a million drivers.

Try virtualization first.  On my Linux boxes, I use VirtualBox to learn/play with an OS before "going for it".  

On my mac, I use VMWare.

Try virtualization.

---

### Post by cyberdork33 on 2009-04-11
> **raymondhenson said:**
> Try virtualization first.  On my Linux boxes, I use VirtualBox to learn/play with an OS before "going for it".  

On my mac, I use VMWare.

Try virtualization.
I really agree. Before jumping into the hard stuff, you should see if you even want the end result.

VirtualBox recently added support for 3d acceleration on Linux guests even!

---

### Post by 311005901 on 2009-04-12
> **cyberdork33 said:**
> I really agree. Before jumping into the hard stuff, you should see if you even want the end result.

VirtualBox recently added support for 3d acceleration on Linux guests even!

Ok! I'll give it a try!

---

### Post by pafufta503 on 2009-04-12
I use rEFIt on my MacPro, when I startup my computer it checks what OS's I have installed and lets me choose which to load.  It's very easy to set up, and feasible for most anyone without alot of computer know how.  You can double/triple/quadruple boot with rEFIt too. It probably took me less than 20 minutes to get triple boot going.

---

### Post by rapsball4 on 2009-08-05
Weird problem.  I installed following the instructions at: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Triple%20Boot:%20Mac%20OSX,%20Windows,%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Triple%20Boot:%20Mac%20OSX,%20Windows,%20and%20Ubuntu).
Loaded fine into OSX (Leopard) and Vista (Home Premium 64).  When I tried to load into Ubuntu, it went into Vista.  Tried it again and got the same thing.  Redoing the Ubuntu install now but I followed the instructions the first time as well so I'm pretty sure nothing will be different.

Second attempt at Ubuntu install gave me a "missing operating system" error instead.  Turned it off and back on again, stalled at the tux logo.  Turned off and back on another time and went back to "missing operating system".

....Now I'm really confused.  After about 5 boots of "missing operating system" it went back to loading into Vista on the most recent try.

---

