---
title: "VMWare and etc."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-05-21
Hey I was wondering about a few things. I am currently in an area where the only internet offered is wireless, and there is no Linux driver support for the card that I have. I was hoping to get something like VM Ware that I could use to open a Linux environment within XP. I was wondering what other options I have besides VM Ware, and what you guys have been able to use successfully?

I will also need to be able to move photos from my digital camera to my computer. This is pretty easy to do with Ubuntu normally, but will it recognize that there is an external device when using VM Ware (or equivalent)? Again the main issue with this is I still want to have wireless :) (Although I suppose this also applies to whether or not Linux will recognize an external hard drive, or any other USB storage device, when used via VM Ware and etc.)

Thanks for any help!

---

### Post by Ziox on 2007-05-21
Check out VirtualBox ([www.virtualbox.org]("http://www.virtualbox.org")).  It offers a feature that allows the guest and host to share folders through a network setup (within your pc).

---

### Post by nonpareilpearl on 2007-05-21
Thanks for the advice! I'll try it out and see if it works :)

---

### Post by nonpareilpearl on 2007-05-21
Is it normal to receive a "This may destabilize Windows, please don't install" message when installing VirtualBox?

---

### Post by nonpareilpearl on 2007-06-01
I was able to successfully install VirtualBox, however it appears that it will need a fresh installation of Ubuntu in order to work. I am currently working in the mountains (at an observatory) and I don't have my disks (or any new ones to burn) here. I need a program that will recognize the fact that I already have an Ubuntu partition.

Thoughts?

---

### Post by Ziox on 2007-06-02
You can install Ubuntu using an ISO file.  Just mount the ISO using VirtualBox.

Create a New virtual hard disk
Settings>CD/DVD Rom>Mount ISO

Because VirtualBox is a virtual machine, it won't recognize any partitions on the original Hard Disk. Nor could VMWare.

---

### Post by justifier on 2007-06-02
forgive me for asking a stupid question, but couldn't you just go and pick up a new wireless card? they are quite cheap

---

### Post by drowner on 2007-06-02
> **justifier said:**
> forgive me for asking a stupid question, but couldn't you just go and pick up a new wireless card? they are quite cheap

She's working in an observatory, in the mountains. If they don't sell blank CD;s, they sure as heck ain't gunna sell friggin wireless cards.

---

### Post by justifier on 2007-06-02
ahhhh oki

---

### Post by veloce on 2007-06-03
> **nonpareilpearl said:**
> I was able to successfully install VirtualBox, however it appears that it will need a fresh installation of Ubuntu in order to work. I am currently working in the mountains (at an observatory) and I don't have my disks (or any new ones to burn) here. I need a program that will recognize the fact that I already have an Ubuntu partition.

Thoughts?

I've seen people describe doing the opposite: using a physical windows install from within ubuntu via vmware, but never the reverse. So, theoretically, vmware should be able to do this but it may not have been done before.  

I have no experience with virtualbox.

---

### Post by RedRover1 on 2007-06-03
In VMware products this is called using the Raw disk and is normally recommended for more advanced users as it can easily hose your system if your not careful.


[http://www.vmware.com/support/ws5/doc/glossary_ws.html]("http://www.vmware.com/support/ws5/doc/glossary_ws.html")

> 
Raw disk

— A hard disk in a virtual machine that is mapped to a physical disk drive or a partition of a drive on the host machine. A virtual machine's disk can be stored as a file on the host file system (see Virtual disk) or on a local hard disk. When a virtual machine is configured to use a raw disk, VMware Workstation directly accesses the local disk or partition as a raw device (not as a file on a file system). It is possible to boot a previously installed operating system on an existing partition within a virtual machine environment. The only limitation is that the existing partition must reside on a local IDE or SCSI drive.
See also Virtual disk. 

---

### Post by nonpareilpearl on 2007-06-07
That's actually quite helpful RedRover, thank you! That's probably exactly what I'm looking for, but I'll need to try it out first.

Sorry it takes so long for me to reply, but again I'm in the mountains >.<

---

