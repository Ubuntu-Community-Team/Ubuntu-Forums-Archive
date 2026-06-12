---
title: "help - newbie needs to complie driver"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-08-11
I'm totally clueless about compiling stuff and I need to compile the driver for a second Ethernet Card - the onboard one has been acting weirdly for a while.
I looked up some stuff on compiling from source, but can't make sense of it with respect to the instructions in the readme (attached) I got with the card.
Could someone please tell me what to do?
Thanks very much.

P.S.: Is it possible that I may not need to do this at all? I mean, I didn't need to install drivers for any other hardware, how do I know the same is not the case with this ethernet card? I know these may sound like stupid questions to some, but I'd really appreciate help.

---

### Post by starcraft.man on 2007-08-11
First thing that I see is the following:

> This driver support linux kernel version 2.4.x/2.5.x now.

I dunno if it's wise to insert a driver that's not tested against the current 2.6.x kernel (I assume your using that), this must be somewhat old. I can't recommend continuing. What's the manufacturer/model of the card? Perhaps someone here can offer better help that's more current.

As for the instructions:
>  1) Create a temporary directory:

        # mkdir /temp



    2) Change to the temporary directory:

        #cd /temp



    3) Copy driver (sl_linux.tgz) from CD-ROM to the temporary directory, and follow the commands: 

       # mount -t iso9660 /dev/cdrom /mnt

       # cp /mnt/sl_linux.tgz /temp



    4) untar the archive file:

       # tar xzvf sl_linux.tgz

       # cd sc92031

    

    5) Compile the driver source files and it will generate sc92031.o, and

       copy it to correct driver installation path (The installation directory

       is different in different kernel versions. In 2.4.x kernel, the path is 

       /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,

       the path is /lib/modules/KERNEL_VERSION/net/)

       # make install



    6) Check configuration file (/etc/modules.conf or /etc/conf.modules,it 

       depend on your Linux distribution) for loading kernel modules. Make sure

       there is the following content in the configuration file, where # is 

       interface number :

        alias eth# sc92031 

  

    7) Reboot now:

        shutdown -r now 



    8) Install your driver module (If the driver module is in the wrong place,

       an error message will appear, and say that can't find the driver 

       module):

        insmod sc92031.o



    8) Use ifconfig command to assign the IP address, where # is network 

       interface number:

        ifconfig eth# <IP>



    9) Check the interface works:

        ping <remote_host_IP>


This is a set of terminal commands. I must say, rather poorly explained at that and only offering the bare minimum. My best advice to understanding terminal commands is to read Linux Command (in my sig, far left orange). Don't attempt this yet, before understanding what your doing and enquiring about it's compatibility. I feel confident there must be a more current solution (if it's not directly supported already in Ubuntu).

Post back more info please on both your cards and the motherboard (as well as anything else relevant) and we'll try to get ya working.

---

### Post by RomeReactor on 2007-08-11
Hi. Just a thought here, but have you tried to connect your internet (LAN) cable to the new ethernet port, or an external hard drive (whatever your intended use for this ethernet card is), to see if it works?

---

### Post by kleo skywalker on 2007-08-11
I thought so about the kernel compatibility thing.
I know next to nothing about hardware, all I know is that I'm using an Intel motherboard, and currently an onboard card. This new card says the following on the box:
> Tricom
10/100 Mbps Ethernet Card
 "Wake on " LAN 
Plug & Play"

**How do I find out if it works without me needing to do anything, like the rest of my hardware?** There is a PnP device in the device list in System-->Preferences-->Hardware information, I'm not sure it was there before.

Thanks.

---

### Post by starcraft.man on 2007-08-11
> **kleo skywalker said:**
> I thought so about the kernel compatibility thing.
I know next to nothing about hardware, all I know is that I'm using an Intel motherboard, and currently an onboard card. This new card says the following on the box:


**How do I find out if it works without me needing to do anything, like the rest of my hardware?** There is a PnP device in the device list in System-->Preferences-->Hardware information, I'm not sure it was there before.

Thanks.

Turn off the machine. Plug in the PCI network card. Connect your ethernet line with the card. Start the computer and log into Ubuntu. If all is working well, Ubuntu should automatically detect the connection and assign you an IP via DHCP assuming that is enabled on your router/modem. If the icon in the top right doesn't connect then ya know ya have a problem and we can go from there.

---

### Post by kleo skywalker on 2007-08-12
Nope, Feisty is not detecting the new ethernet card. What next?

---

