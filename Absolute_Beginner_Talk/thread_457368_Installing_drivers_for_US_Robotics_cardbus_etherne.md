---
title: "Installing drivers for US Robotics cardbus ethernet card"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by quind on 2007-05-28
Extreme Linux newbie here. I want to install the drivers for my ethernet card but I don't know how. The CD's folder entitled "Linux" has a readme, a makefile, and a file called usr.c 

I tried using the package manager but it said it couldn't find any packets on the CD.

The readme file gives instructions (posted below) , I just don't know how to follow them. Could someone tell me what to do? Is terminal the program I should be using to do this? I have feisty fawn, by the way.

> File List
---------
    The complete files list is as follow:

    readme.txt
    Makefile
    usr.c
     

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


---

