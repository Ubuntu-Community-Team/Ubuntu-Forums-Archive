---
title: "old windows xp"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-23
can i open my old windows from linux... something like vitualbox but with my stuff already in it?

---

### Post by Microsoft_Sam on 2007-11-23
I think this is exactly what you want. :)

[http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/]("http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/")

---

### Post by merlinDwizzard on 2007-11-23
If you kept everything fat 32 then go to places>computer>then whatever drive your stuff is in pretty cool eh?

---

### Post by patchido on 2007-11-23
> **Microsoft_Sam said:**
> I think this is exactly what you want. :)

[http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/]("http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/")

ive done everything but i cant do this... # Click Applications &#8594; Add/Remove… . Install the vmware-server package.



that package wont show up

---

### Post by patchido on 2007-11-23
shouls i download it form here[http://register.vmware.com/content/download.html]("http://register.vmware.com/content/download.html")

if yes... which one of the 4?

---

### Post by patchido on 2007-11-24
plz...... i really need this

---

### Post by patchido on 2007-11-24
this is urgent

*bump*

---

### Post by patchido on 2007-11-24
how can i use my old windows xp from ubuntu???

they told me this.. but i cant manage it to work[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/")

this is urgent

---

### Post by Flying caveman on 2007-11-24
Whoa! slow down there buddy! youv'e made 39 posts in 16 hours.

I saw some of your other posts. how did you install Ubuntu? I saw one of your posts talking about the Wubi installer, or did you dual boot? or do you just have Ubuntu and want to run XP in a virtual machine?

That tutorial kind of assumes that XP is already installed and has you configure some stuff first before running it in a virtual machine.  I'm not sure if thats the case.

---

### Post by patchido on 2007-11-24
> **Flying caveman said:**
> Whoa! slow down there buddy! youv'e made 39 posts in 16 hours.

I saw some of your other posts. how did you install Ubuntu? I saw one of your posts talking about the Wubi installer, or did you dual boot? or do you just have Ubuntu and want to run XP in a virtual machine?

That tutorial kind of assumes that XP is already installed and has you configure some stuff first before running it in a virtual machine.  I'm not sure if thats the case.

lets say i really want ubuntu to get stable.. and yea i did dual boot... but i still cant manage to open windows from ubuntu.. and i wish my settings of windows to bre the same

---

### Post by patchido on 2007-11-24
i havent been able to make my old copy of windows run inside ubuntu.. plz i eed this urgent

---

### Post by LaRoza on 2007-11-24
What VM are you using?

Try VirtualBox if you are not using it.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by pdlethbridge on 2007-11-24
Is it installed?
Please give us more information, IE, hard drive size, partitions, versions of windows, ubuntu, etc.

---

### Post by patchido on 2007-11-24
i have gutsy 7.10 and my windows is an XP how the hell do i do it?? i have vitualbox.. but i cant manage to make my old windows work

---

### Post by LaRoza on 2007-11-24
Please give more information.

Are you dualbooting? Running a VM? Installing Windows?

What hardware are you using also.

---

### Post by patchido on 2007-11-24
> **LaRoza said:**
> Please give more information.

Are you dualbooting? Running a VM? Installing Windows?

What hardware are you using also.

obusly i am dualbooting... i said i want my old windos to run meaning.. th windows installed in this same lapptop... it has partition.. but i dont understand what infrmation about that partition u want..

---

### Post by Taboo Mirage on 2007-11-24
> **patchido said:**
> obusly i am dualbooting... i said i want my old windos to run meaning.. th windows installed in this same lapptop... it has partition.. but i dont understand what infrmation about that partition u want..

Frankly it wasn't obvious at all.  I also thought you were referring to virtualization at the start of your thread.  Your English is very difficult to understand right now; writing more legibly may solve this problem.

In regards to your issue, you still haven't really provided anyone with information which could help them assist you.  What exactly are you having problems with?  Are you getting any error messages?  What has led you up to this stage?  Did it ever work?

---

### Post by Paul133 on 2007-11-24
You can't choose it from a list (grub) when you first boot your computer?

---

### Post by patchido on 2007-11-24
ok... ill make this clear srry .... i want to be able to run my windows settings from ubuntu....

i dont know how to do it form Virtualbox.. tried and cant find out how... then i followed a guide for vm.. [http://www.kvaes.be/unix-linux/runni...within-ubuntu/]("http://www.kvaes.be/unix-linux/runni...within-ubuntu/")
 but when this comes up 

Click Applications &#8594; Add/Remove… . Install the vmware-server package.

from that on i cant work it out.. im kid of a noob... and i cant find the vmware server package.. googled it and found different ones and didnt know which one to use.

---

### Post by LaRoza on 2007-11-24
> **patchido said:**
> ok... ill make this clear srry .... i want to be able to run my windows settings from ubuntu....

i dont know how to do it form Virtualbox.. tried and cant find out how... then i followed a guide for vm.. [http://www.kvaes.be/unix-linux/runni...within-ubuntu/]("http://www.kvaes.be/unix-linux/runni...within-ubuntu/")
 but when this comes up 

Click Applications &#8594; Add/Remove&#8230; . Install the vmware-server package.

from that on i cant work it out.. im kid of a noob... and i cant find the vmware server package.. googled it and found different ones and didnt know which one to use.

That made it more confusing, are you dualbooting or virtualizing?

To make things more lucid run these commads and then post the complete results:

```

sudo fdisk -l

```

```

less /boot/grub/menu.lst

```

---

### Post by pdlethbridge on 2007-11-24
Is windows on its own partition or are you trying to run it within linux using Virtualbox?
Could you have erased windows when you set up linux?

---

### Post by LaRoza on 2007-11-24
> **pdlethbridge said:**
> Is windows on its own partition or are you trying to run it within linux using Virtualbox?
Could you have erased windows when you set up linux?

When the OP responds to my post, the partitions and grub will be known to us.

---

### Post by pdlethbridge on 2007-11-24
I was writing that while you were posting, Sorry! Does virtualbox have a gui?

---

### Post by LaRoza on 2007-11-24
> **pdlethbridge said:**
> I was writing that while you were posting, Sorry
It was not for you, it was for the OP, who probably doesn't know how to answer your question or the purpose of the commands I gave, so I didn't want the OP to answer neither.

---

### Post by Paul133 on 2007-11-24
I think he's trying to do virtualization, not dual-booting, since he says he wants to "run his windows settings in Ubuntu".

---

### Post by LaRoza on 2007-11-24
> **Paul133 said:**
> I think he's trying to do virtualization, not dual-booting, since he says he wants to "run his windows settings in Ubuntu".

The OP also said it was obvious it was dualbooting, so we are quite confused.

---

### Post by Paul133 on 2007-11-24
Yes we are.

---

### Post by pdlethbridge on 2007-11-24
As a side note, inquiries should always have pertinent system information. 
A veterinarian has to be on top of his game because the animals can't say where it hurts

---

### Post by patchido on 2007-11-24
> **LaRoza said:**
> That made it more confusing, are you dualbooting or virtualizing?

To make things more lucid run these commads and then post the complete results:

```

sudo fdisk -l

```

```

less /boot/grub/menu.lst

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb72fb72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8025    64460781    7  HPFS/NTFS
/dev/sda2            8026        9651    13060845   83  Linux
/dev/sda3            9652        9729      626535    5  Extended
/dev/sda5            9652        9729      626503+  82  Linux swap / Solaris




the second code is too big... but if u need it tell me... i run dualboot and want to virtualize my already installed windows xp

---

### Post by Taboo Mirage on 2007-11-24
*deleted.*

---

### Post by LaRoza on 2007-11-24
> **patchido said:**
> 
the second code is too big... but if u need it tell me... i run dualboot and want to virtualize my already installed windows xp

For everyone:

The OP wants to use an existing XP installation on a VM in Ubuntu which is dualbooted with Windows.

I don't know if and how that can be done. Others may know more.

---

### Post by patchido on 2007-11-24
> **patchido said:**
> ok... ill make this clear srry .... i want to be able to run my windows settings from ubuntu....

i dont know how to do it form Virtualbox.. tried and cant find out how... then i followed a guide for vm.. [http://www.kvaes.be/unix-linux/runni...within-ubuntu/]("http://www.kvaes.be/unix-linux/runni...within-ubuntu/")
 but when this comes up 

Click Applications &#8594; Add/Remove… . Install the vmware-server package.

from that on i cant work it out.. im kid of a noob... and i cant find the vmware server package.. googled it and found different ones and didnt know which one to use.

in the link in there said how.... but i cant manage to make it owrk

---

### Post by Taboo Mirage on 2007-11-24
I understand now.

Yes, this is possible.  VMWare is the only VM software I know of that supports this, although there may be others I haven't happened upon.

To be honest the procedure for accomplishing this task is somewhat complex and involves a lot of editing.  I recommend checking out [this guide](http://oopsilon.com/Running-a-Windows-Partition-in-VMware) and seeing if you can follow this.  You'll have to edit some of the configuration files with disk sector information as well as create a specific hardware profile for the virtualized Windows installation.

Take care.

---

### Post by akiratheoni on 2007-11-24
I think he has an XP-Ubuntu dual boot, but he wants to virtualize his XP partition in Ubuntu so he can keep his settings and such.

IIRC, it's possible, but XP might deactivate due to hardware changes or whatever and you'll have to input your serial code again. Ah, the joys of using WIndows :-P

---

### Post by patchido on 2007-11-25
gave up on this... lots of cons.. im getting a new virtual not using old settings... can anyone post a guide to follow with virtualbox??? or wich emulator is recommended?

---

### Post by merlinDwizzard on 2007-12-09
virtualbox is pretty easy to deal with. Once installed go to applications>accessories>terminal.Then you must log into root by typing sudo -i. You will be asked for root password, enter it. Then simply type virtualbox (lower case). Virtualbox will start up, yes it has a gui. from there click on new and follow the steps. it will tell you when to install the disc to begin installation. good luck, let us know how it worked out.

---

