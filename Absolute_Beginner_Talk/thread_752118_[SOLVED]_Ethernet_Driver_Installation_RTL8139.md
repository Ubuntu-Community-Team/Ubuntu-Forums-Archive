---
title: "[SOLVED] Ethernet Driver Installation RTL8139"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Dumpy Dumpster on 2008-04-11
I attach the following instructions that came with my ethernet card and as a newbie, I would be very grateful if they could be interpreted!!  I have put in some details that I know and some questions in italics.  The previous thread on the 8139 card mean nothing to me - sorry.  I am running 7.04.  Here goes--

  Linux driver for kernel 2.2.X *2.6.20-16-generic)*



  The procedure to activate RTL8139 on linux is as follows:



  step 01: Copy the driver source files to a convenient directory.(*Desktop ok?*)



  step 02: Compile

           The instruction for compiling the driver is include at the 

           end of the driver file.If a compile-command is not there use 

           the following compile command:

           (Run this instruction at /usr/src/linux) [I](How do I do this?)
[/I]
           

           *compile-command: 

           " gcc -DMODULE -Wall -Wstrict-prototypes -O6 -c rtl8139.c "



           Or you can use the Makefile included in the driver disk \LINUX.



  step 03: Copy the module "rtl8139.o" to 

           "/lib/modules/{kernel-version}/net"*( I can find this file but not with 'net'on the end)*

   

           *The directory "{kernel-version}" stands for the Linux kernel 

            version you use. 

  

  step 04: Insert the driver as module:

           insmod rtl8139.o [I](How is this done?)
[/I]
           (Run 'lsmod' to see if the module is inserted)



  step 05: Bind your card to an IP address [I] (This  and all the rest is  gobblydegook to me!)
[/I]
  

           /sbin/ifconfig eth0 ${IPADDR} broadcast ${BROADCAST} 

           netmask ${NETMASK}

           (Run 'netstat -i' to see if there is a interface 'eth0')

  

  step 06: Add your card to IP routing table, then add gateway also 

           your card:

           /sbin/route add -net ${NETWORK} netmask ${NETMASK} eth0

           (Should be able to ping local network now)

           

           gateway:

           /sbin/route add default gw ${GATEWAY} netmask 0.0.0.0 metric 1

  

  step 07: Start inet daemon.

           /usr/sbin/inetd

           (You are on the network now)



  *make sure that your kernel is built with network, fast_ethernet and 

   module support. Otherwise, you have to rebuild your kernel.

   ( 01:Go to /usr/src/linux directory

     02:Run "make menuconfig" or "make config"

     03:Mark the options list above.

     04:Exit and rebuild your kernel.

        make dep;make clean;make zImage

        the file "zImage" will be at

        /usr/src/linux/arch/i386/boot/zImage

     05:Modify /etc/lilo.conf.(this file specify where kernel image is)

     06:Run "lilo" )

  

  You can run "netconfig" which will do step 05,06,07 for you. *(Is this a shortcut?)*

  

  Then just add a line at the beginning of "/etc/rc.d/init.d/network".

  

        " insmod /lib/modules/{kernel-version}/net/rtl8139.o "

        

        *The directory "{kernel-version}" stands for the Linux kernel 

         version you use.

  then your driver will work every time you boot.
[FONT="Arial"][/FONT]

---

### Post by Benbow on 2008-04-11
A few months ago my internal ethernet card passed on and I fitted a new one to a pci slot. I then restarted my system and ubuntu found the new card immediately, no probs. I thought that this was normal or was I just lucky?
Also using 7.4 then (8.4 now).

Sorry I can't be of more help with your problem.

---

### Post by quirks on 2008-04-11
Yeah, why are you trying to compile the driver yourself? As far as I know, it is already built-in? Doesn't your ethernet card work?

quirks

---

### Post by Dumpy Dumpster on 2008-04-11
Many thanks qirks and Benbow for your replies.  
I might well be accused of jumping the gun a bit as the France Telecom engineer is coming on Tuesday to set up ADSL for my XP and they cannot cope with Ubuntu!!  So I have not actually connected up yet.  The literature that came with the card said to install the driver, but if it is already in and the card will work 'out of the box' then that is marvellous news.  
I will leave it there and fingers crossed for Tuesday!  Thank again.

---

### Post by stchman on 2008-04-11
I have the 8139 Realtek card in my laptop and in a desktop and the work OOB.  No need to compile a driver that is already in the kernel.

Ubuntu supports a vast array of hardware OOB.

---

### Post by oldham03 on 2008-04-11
Ubuntu is recognising the card but I canoot get on the internet! Frustrating.

---

### Post by stchman on 2008-04-11
> **oldham03 said:**
> Ubuntu is recognising the card but I canoot get on the internet! Frustrating.

You said you have DSL?  If so then you will need to supply a username and password.  Do you have a router?  If yes use PPoE and save the username and password in the router.  If no router (I highly recommend one as they are cheap and allow you to share the connection), then you will need to run te command:

```
sudo ppoeconf
```

I have never had DSL, but I have setup DSL for friends that have routers and it was a snap.

---

### Post by bumanie on 2008-04-11
There is one realtek 8139 card that has a chipset with the number sc92031 I think, going form memory) that was not supported in the ubuntu kernel until 2.6.21 kernel. The particular card was manufactured by (again going from memory) Hungzhou electronics, China. If you have that chipset number, you will probably have to either get a different card or compile a later kernel.

---

