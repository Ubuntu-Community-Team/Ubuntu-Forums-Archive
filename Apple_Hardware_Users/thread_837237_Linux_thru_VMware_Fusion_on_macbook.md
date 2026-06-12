---
title: "Linux thru VMware Fusion on macbook"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by phidia on 2008-06-22
I was just wondering how many people here have tried vmware fusion specifically on a macbook, but any experienced input is welcome.
BTW I have seen comments in the Apple Users forum that macbooks are not the best choice for running Ubuntu, but a lot of PC laptops fall into that category too!
With a HP pavilion (which I researched b4 I purchased) I have had a tough ride with wireless and problems with ndiswrapper which can work fine but then suspend and other things don't work. Madwifi on my HP has big performance issues..so whatever. Believe me I'm not mentioning a whole bunch of other things.
I like macbooks for their good battery life too so can anyone say whether or not vmware fusion runs linux with good performance and usability? Thanks

---

### Post by DGortze380 on 2008-06-22
Ubuntu 7.04 had some issues on VMWare Fusion when I tried, I wish I could give you details but I honestly don't remember. I haven't tried anything more recent. Running command line 8.04 on VirtualBox (free), but to the best of my knowledge NAT doesn't work on Mac in VirtualBox.

---

### Post by hajk on 2008-06-23
My experience is that Linux runs very well in VMware Fusion, both in version 1.1 on an original 1,1 MacBook and -- more recently -- in the 2.0 beta on a 4,1 MacBook Pro. It is the ideal way if you want to spend considerable time in Mac OS X as well; and if you don't want to deal with hardware incompatibilities (of which there have been several new ones recently). Now, if you have no use for Mac OS X at all, then you would be better off not getting an Apple computer in the first place.

It should be noted that discussions on the running of Ubuntu in a VM should more properly be relegated to the general sections of the Ubuntu forums, as these VMs mimic a regular PC, not an Apple computer. The only exception may the keyboard that the VM inherits from the Apple computer it is running on: how to remap quote/tilde keys, how to specify third-level chooser and dead-letter keys, how to remap a right mouse click. But all that is pretty straightforward using xev and xmodmap.

---

### Post by phidia on 2008-06-23
Thanks for the responses. I posted here because I am and have been a mac user-in fact I started with linux on old beige powermacs.
I wanted to know if anyone had actual experiance using fusion on a macbook so the Apple Users forum seemed like the right place. The wrong place would have been the general section since I would have been polling the majority who are peecee users.
Thanks again.

---

### Post by Demetrix on 2008-06-23
I am using Ubuntu 8.04 with my MacBook Pro through VMware Fusion, and it works perfectly fine. Except for one  thing, I can't use the VMware "unity" feature.

---

### Post by oxnardmontalvo on 2008-06-23
running 8.04 on a macbook using fusion. Tried parallels and virtual box, fusion I believe is the smoothest and best. but that's just my opinion. 

there are a few gotchas. vmtools is a real problem. I guess there are some directory structure differences, so it will take you a while to build and get them running. but it can be done. networking is also an issue. it's almost impossible to get afp running. smb is also very difficult. i've yet to get a working ssh/sftp functioning, unless I use an sftp client instead of gnome client. Ununtu is nice. I fiddle with it from time to time. but, and I hate to say this, the average user used to osx package management and the way things 'just work' will find no end to the frustration. not a flame, just an observation. take the vmtools as an example. I had to google myself to death finding the 'right' info to install the tools. never really did find it. but was able to get them to finally build and install by gathering little bits of partial information here and there to finally figure out how to get it to install. I've given up on afp and smb. I'm sharing directories using sftp. the 'shared directories' that fusion uses, once you get the tools installed, is almost useless and buggy. due to permissions issues, almost any directory, with the exception of the shared public directory can not be viewed. 

still, its fun to fiddle with. interesting to see how things are looking on the linux side. installed suse 11 the other day. it's nice, vmtools automatically install, nice. but, it is rather resource heavy and much much slower than ubuntu.

---

### Post by hajk on 2008-06-23
You're right as far as Ubuntu 8.04 and vmware-tools is concerned. Debian has a perfectly usable open-vm-source package with which to compile the tools; no reason why Ubuntu shouldn't have the same (they could just take the Debian package, it compiles OK in Ubuntu 8.04). VMware themselves haven't optimized VMware Fusion for use with Ubuntu 8.04 either... here, too, Debian has fewer issues in my experience, such as with screen resolution and the xserver-vmware video driver. These are missed opportunities, both by Ubuntu and VMware.

---

### Post by mfox on 2008-06-23
I am successfully running Ubuntu 8.04 on VMware Fusion, on a Mac mini.  VMware Tools won't install in the normal way with 8.04, but I found instructions on the internet for compiling the tools from an open vmware version the company posted.  I'm pretty new to Linux, but the instructions were like following a cookbook, and they worked well.  I have all the tools working on 8.04; even the drag-and-drop across the Mac desktop and back.  I have tried Ubuntu 8.04 on Parallels Desktop, VirtualBox and even on a G4 PPC.  Parallels Tools will not install on this version, though a fix is supposedly in the works.  VirtualBox works well except for the drag-and-drop across the desktop.  And Ubuntu is actually pretty good on a G4 PowerBook - even AirPort works - except I couldn't get the program Mac-on-Linux to work on it.

---

### Post by cyberdork33 on 2008-06-23
First, a clarification. Running Ubuntu in a VM is _not_ the same as running Ubuntu on your Macbook.

Ubuntu runs great in VMware Fusion! However, it runs great in Virtualbox too, and virtualbox is free!

---

### Post by phidia on 2008-06-23
> **cyberdork33 said:**
> First, a clarification. Running Ubuntu in a VM is _not_ the same as running Ubuntu on your Macbook.

Ubuntu runs great in VMware Fusion! However, it runs great in Virtualbox too, and virtualbox is free!

I wonder why that was necessary to clarify, but if by *not the same* you mean avoiding hardware conflicts, dual booting and not getting to wear a technogeek wizard beanie cap I agree it's not the same.

VMware Fusion is a VM there are those available to linux users who want to try other distros without dual booting too.

Thanks for the info on virtualbox download page [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") for anyone else interested. I had seen and read a little about virtualbox but don't know much about it.

---

### Post by cyberdork33 on 2008-06-24
> **phidia said:**
> I wonder why that was necessary to clarify, but if by *not the same* you mean avoiding hardware conflicts, dual booting and not getting to wear a technogeek wizard beanie cap I agree it's not the same.
I mean that it is not the same. You are not "running Ubuntu on your Macbook" you are running Ubuntu in a VM. It is widely expected for Ubuntu to run very well in a VM because VMs are designed to be compatible... I can install on a PC running VMware send you the config and drive image, and you can boot it just the same in Vmware fusion. 

I am not trying to put you down, but post like yours make it seem very easy to new users to install on their Mac like there is no issues to resolve. If you are happy with a VM and that suits you, great! but this is a support forum for running Ubuntu on _Mac_ hardware, not virtualized hardware. There is a virtualization forum for those discussions.

> **phidia said:**
> VMware Fusion is a VM there are those available to linux users who want to try other distros without dual booting too.

Thanks for the info on virtualbox download page [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") for anyone else interested. I had seen and read a little about virtualbox but don't know much about it.

I absolutely agree! I have a copy of VMware fusion on my Mac as well. I normally use virtualbox as it runs almost as good for running linux as a guest unless you have specific requirements for some of the unimplemented features.

---

