---
title: "PCMCIA Ethernet card install – compiling drivers"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by tatibot on 2006-10-23
Hi all,
I am relative noob to linux - I just installed Xubuntu on the 7 year old laptop. Since it doesn’t have Ethernet connector built in, I bought pcmcia “Cardbus 10/100 Ethernet PC Card” Model 7901A made by U.S. Robotics, but it doesn’t work out of the box. I looked at installation CD and there are drivers for Linux, however they need to be compiled. Files included are :
Makefile
Usr.c
Readme.txt

I followed directions in readme.txt however it’s not working for me – I can’t get thing to compile. Since I am new I might not be using correct syntax, so that might be a problem (probably is).
Every time I type ‘make’ command I get ‘command not found’. When I type ‘man help’ it says that there is no entry for make. Some kind of compiler s include with Xubintu isn’t it? (how do I check). 
What is correct command syntax to compile the driver? Do I need anything else installed in order to get this card working?

All help is greatly appreciated!

P.S. 
this is the link to the mfg. product page
[http://www.usr.com/support/product-template.asp?prod=7901a](http://www.usr.com/support/product-template.asp?prod=7901a)

this is procedure from in readme.txt file
> 
Installation Procedures
------------------------
 
 1. Uncompress the attached file to an empty floppy disk.

 2. To login as the root.
 
 3. Copy the driver source files to a convenient directory, simply do 
 
 4. Modify the Makefile
    
    Please modify the following line to specify the correct Kernel version.
    NEW_INCLUDE_PATH = /usr/src/linux-x/include/ 
    Comment: X->indicates the current kernel version 

 5. To compile and generate the object code from the driver source code
 
    #make 
    The final file is usr.o 

 6. Copy the module "usr.o" to 
    "/lib/modules/{kernel-version}/kernel/drivers/pcmcia"
 
    *The directory "{kernel-version}" stands for the Linux kernel 
     version you use. 
 

 7. Insert the driver as module:
    #insmod mii
    #insmod usr.o
 
 8. Edit config:
    ->Add 5 lines to the file "/etc/pcmcia/config"
    
    #
    # Device driver definitions
    #
   
    device "usr"                                    (==>Add 1/5)
    class "network" module "usr"                    (==>Add 2/5) 
   
    :
    :
 
    #
    # 10/100BaseT Network Adapter
    #
 
    card "U.S. Robotics CardBus 10/100 Ethernet PC Card"  (==>Add 3/5)
    manfid 0x0000, 0x024c                                 (==>Add 4/5)
    bind "usr"                                            (==>Add 5/5)
    
    The values 0x0000, 0x024c are JEDEC ID and can be read by typing 
    "cardctl ident" on console with one card on socket.


 9. To reboot the Linux system
    
    #shutdown -r now

 8. To login as the root.

 9. To Set up the IP configuration
 
    #netconfig 

 10. To reboot the Linux system
    
    #shutdown -r now


Copyright
----------
   This document can be freely used and redistributed without any
   prior permission.

---

### Post by tatibot on 2006-10-25
Update &#8211; well I couldn&#8217;t  do &#8216;make&#8217; since make package wasn&#8217;t loaded. I installed &#8216;build-essential&#8217; package and that took care of it. Since I am trying to build driver for network interface I loaded build-essential from distribution CD. For noobs like me, in order to do so you have to enable CD as a location for packages
Applications>System>Synaptic Package Manager>Edit>Add CD-Rom

Once I did that, using terminal I typed 
sudo apt-get install build-essential

and that took care of it. I still can&#8217;t compile files, but that&#8217;s  due to some other issues (and I&#8217;ll ask about that in another post)

---

