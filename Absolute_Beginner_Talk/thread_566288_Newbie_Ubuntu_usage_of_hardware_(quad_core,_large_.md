---
title: "Newbie: Ubuntu usage of hardware (quad core, large RAM) and advice for Win user"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Keith_2 on 2007-10-03
I will be receiving a new quad core PC (4GB RAM, will expand to 8 if needed for performance) which will be used to run virtual machines for software testing. The VMs will need to be able to use/share USB devices, SATA devices, the host OS's network connection to the internet. 

Originally the project plan was based on using MS as a host system, and the MS VM software. However, I'm exploring other options.

I've never used Unix or Ubuntu; my first question is whether the basic desktop install of Ubuntu will take full advantage of the quad cores and large memory space, and also freely pass those resources on to virtual machines (possibly using VMWare).

My extremely newbie question is for your opinion on how difficult it would be for a complete novice to install and configure Ubuntu (including networking, etc) to support the VMs. If the learning curve is steep, I may not have time to explore and learn Ubuntu. Once i have a working host, most of my work will just be in the VMs.

Thank you for any feedback or advice,
Keith

---

### Post by go2dell on 2007-10-03
Here are some bits of reading to help you make your decisions:

[LIST][*][Supported Architectures]("https://help.ubuntu.com/community/SupportedArchitectures")
[*][Supported Hardware]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/ia64/hardware-supported.html")
[*][Virtual Machines]("https://help.ubuntu.com/community/VirtualMachines")
[/LIST]

I think you *may* need to compile your own kernel if you go with a full 8GB RAM, but I'm not certain on this.  It's not particularly difficult, and complete instructions are here:  [Compiling a New Kernel]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/ia64/kernel-baking.html").

You have a selection of VMs to choose from and installation under Ubuntu is easy enough that you can play with the different ones to find which one you like best.

Enjoy!

---

### Post by deserthowler on 2007-10-04
I ran Win2K for a while in Virtual Box under Ubuntu.  I quit using after a while because all I did was update and run virus scanner and spyware scanner. LOL I also did some Linux distros in it.  It worked OK with the hard drives and the floppy drive and the network.  I never tried anything else with it though.

Earl

---

### Post by Paulmd on 2007-10-04
> **Keith_2 said:**
> I will be receiving a new quad core PC (4GB RAM, will expand to 8 if needed for performance) which will be used to run virtual machines for software testing. The VMs will need to be able to use/share USB devices, SATA devices, the host OS's network connection to the internet. 

Originally the project plan was based on using MS as a host system, and the MS VM software. However, I'm exploring other options.

I've never used Unix or Ubuntu; my first question is whether the basic desktop install of Ubuntu will take full advantage of the quad cores and large memory space, and also freely pass those resources on to virtual machines (possibly using VMWare).

My extremely newbie question is for your opinion on how difficult it would be for a complete novice to install and configure Ubuntu (including networking, etc) to support the VMs. If the learning curve is steep, I may not have time to explore and learn Ubuntu. Once i have a working host, most of my work will just be in the VMs.

Thank you for any feedback or advice,
Keith

Setting up one or more VMs isn't that tough. VirtualBox is pretty decent. But is by no means the only option. I know it can share the internet, and USB devices. Not sure about sharing SATA. 

What won't be happening in a VM is any software requiring hardware accelleration for video.

---

### Post by hyper_ch on 2007-10-04
I think one problem you may have is that you can assing a USB device only to one VM at a time...

---

### Post by roaldz on 2007-10-04
Don't you need to run a 64BIT kernel if you have 8 GB of ram? I would really recommend a 64BIT kernel if you are going to install Ubuntu. Just get the AMD64-livecd from a mirror. You can use Qemu, Virtualbox or VMware for you virtual machines. 

Greets,

Roald

---

