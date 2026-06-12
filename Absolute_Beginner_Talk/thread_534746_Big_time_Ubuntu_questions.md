---
title: "Big time Ubuntu questions"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
1) My computer has 2 drives, 1x 320gig and 1x 750gig. The 320gig is a dedicated drive for the OS and the 750gig is a dedicated drive for all DATA (documents, reports) etc. Currently I have Windows Vista Ultimate x64 installed and both drives have NTFS partition (both drives have single partitions). Can I leave the 750gig as a NTFS partition OR do I need to format it to ext3 partition? If I can leave it as NTFS, do I loose performance?

2) I have the ICH9R chipset and both my drives are SATA2. Do I load in the chipset driver? In windows, you had to press F6 during the installation screen to load the driver. In Ubuntu, is there anything special required?

3) If I format the 750gig as a ext3 partition and specify it as the /home directory, next time I reinstall Linux...will it retain the files in the /home directory? I want it to retain the files. ALSO, I want to login as ROOT (I already figured out how) and does the /home directory belong to the root?

---

### Post by shearn89 on 2007-08-25
1. You can use NTFS, but only after installation of extra drivers. It will automatically ask to format it as ext3 during Ubuntu installation.

2. No idea i'm afraid...

3. It will keep the /home directory, as long as you tell it to use that partition as /home, and tell it not to delete everything. I'm not sure the /home directory belongs to root, although its just as easy to log in normally, and then use "sudo" or "gksudo" for any admin stuff. I wouldn't recommend logging on as root unless there's a really good reason for it.

---

### Post by pencil86 on 2007-08-25
Thanks, more questions.

1) If I format the 750gig as ext3...will I lose my data? 
2) I want a pure barebones installation of Ubuntu...do I install ubuntu and use the synaptic manager to remove uneeded software?
3) My computer is powered by quadcores, Ubuntu will support them properly right? (it also has 8gigs of ram..i'll be using x64 ubuntu)

THanks a bunch!!!

---

### Post by shearn89 on 2007-08-25
1. Yes. You'll have to backup to LOTS of dvds (or an external drive), and then restore it after.

2. Yes, although My 'buntu install is currently sitting on ~3.5GB of the 5 available to it... Its really really small!

3. I guess so - some googling showed that people have installed it before, with no trouble-- > the linux kernel has excellent support for intel multi-core processors. linux has supported multi-core, multi-thread and multi-cpu systems for most of its existence. without this capability, linux would never have become the default operating system for multi-core, multi-thread and multi-cpu systems.

You might want to verify this before plowing on with wiping out windows!

---

### Post by p_quarles on 2007-08-25
1) Yes, absolutely. Any time you format a disk, anything that lives on that disk is gone. What you need to do is create a new partition on one of your disks (min 4 gigs), and then allow the Ubuntu disk to create an ext3 filesystem on *that*. You can read/write the ntfs partitions after installing an app called ntfs3g.

2) The basic installation is pretty barebones. You could also just choose to install the server edition and then add whatever desktop environment you want. 

3) Yep.

---

### Post by pencil86 on 2007-08-25
thanks again...sorry, more questions


1) When installing a program (say java)...should i download the linux version from java.sun.com OR go through the synaptic package manager? (i want the latest and greatest stable released version)


2) what's the difference between server and desktop editions of ubuntu? would the server edition be "barebones"? if it is barebones....does it come with gnome/gui installed...cause i don't know how to install gnome through terminal etc.

---

### Post by p_quarles on 2007-08-25
1) It's a *lot *easier to use the package manager, since that way you're guaranteed (er, mostly) to get a version that works with your distro of Linux. If you want the "latest" that usually means having to grab the source code and compile it yourself. 

2) Server edition comes without a GUI, standard. To install Gnome, you would just log in, and once the command line prompt comes up you'd type:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by pencil86 on 2007-08-25
Thanks again.

One final question, regarding the server version...does it come with preinstalled services like SAMBA and apache/python/php and etc? I don't want those installed. I just want the most basic barebones installed (the bare functionality to get it working etc).

---

### Post by p_quarles on 2007-08-25
You do, actually, want python. It's central to the OS.

But, no, the Ubuntu server installation CD allows you to select what type of server you want. When you get to the section that asks you whether you want a LAMP server or a DNS server, simply leave both blank.

---

