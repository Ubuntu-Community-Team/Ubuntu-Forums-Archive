---
title: "How to install Intex Lancard???...Plz Help Me Out"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by udayan18 on 2007-04-24
i installed ubuntu 7.04...the installation went fine..but like windows even ubuntu didnt install drivers for my lancard..i found the driver in cd...but i cant understand the procedure...so if sm1 can help me out it wud b of gr8 help...heres the procedure  tht it says


Introduction:
=============

    The instructions are for linux driver installation. You must
    compile the source code to generate sc92031.o and use insmod command to
    insert sc92031.o as module.

Contents of the Subdirectory:
=============================

    readme.txt                This file.
    sc92031.c                 The linux core driver source code file
    Makefile                  Makefile for generating driver object file
    
Kernel Supported
================
    This driver support linux kernel version 2.4.x/2.5.x now.

Installation
============
    1) Create a temporary directory:
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

---

### Post by udayan18 on 2007-04-24
i understood the procedure till step 4...i didnt understand the rest of it...
plz help i am completely new to linux

---

### Post by udayan18 on 2007-04-25
Can ne1 tell me how to install lancard drivers for realtek lancard..??..plz help me out bcoz my net is not working in fiesty..n i want to install umbrello which i desperately require to study for my exams....

---

### Post by tictacman on 2007-04-25
Hello I'm not quite sure what you are referring to:

> install lancard drivers for realtek lancard

Do you mean a wired lan network card with a realtek chip?  In my experience these cards run out-of-the-box without any further configuration.

If you are referring to a wi-fi card then the answer would depend upon which realtek chip you have on your card.  There are some extensive guides on this forum covering wi-fi cards so you might like to type in the name of the realtek chip into the search feature.  If you can't find what your looking for continue to post here.

---

### Post by tictacman on 2007-04-25
Forgot to add if your not sure which chip you have in the wi-fi card then you can find out by typing this command into the terminal/shell

 lspci | grep -i network

---

### Post by udayan18 on 2007-04-25
i hv realtek ttl lancard...not a wifi card...this is the actual name of it..
Realtek Rtl-8139d PCI Fast Ethernet 
this card is not detected by ubuntu..nor its drivers r installed by it

---

### Post by aysiu on 2007-04-25
You actually seem to be getting a lot of help. I'm not sure what happened to your other post in question, but I'm sure the moderator meant well. Perhaps it was a simple mistake?

In any case, I've merged your threads about Intex Lancard together so it'll be easier for people to help you out.

---

### Post by udayan18 on 2007-04-25
tx alot...n sry for me getting frustrated...the thng is i hv got my exams ...n i need to pracitce on umbrello...so if theres a way by which i can install umbrello in ubuntu without using internet in it(my net works in windows....so can i just dld the package of umbrello from windows n install it in ubuntu??)

---

### Post by Buffalo Soldier on 2007-04-25
> **udayan18 said:**
> i hv realtek ttl lancard...not a wifi card...this is the actual name of it..
Realtek Rtl-8139d PCI Fast Ethernet 
this card is not detected by ubuntu..nor its drivers r installed by it
Firstly, welcome to GNU/Linux and Ubuntu.

OK... From what I can see these are the threads/posts you have made. None were jailed or deleted. Or have I missed any?

[LIST]
[*] [http://ubuntuforums.org/showthread.php?t=422338](http://ubuntuforums.org/showthread.php?t=422338)
[*] [http://ubuntuforums.org/showthread.php?t=421536](http://ubuntuforums.org/showthread.php?t=421536)
[*] [http://ubuntuforums.org/showthread.php?t=422323](http://ubuntuforums.org/showthread.php?t=422323)
[*] [http://ubuntuforums.org/showthread.php?t=422322](http://ubuntuforums.org/showthread.php?t=422322)
[/LIST]

The first post you made was around 12 hours ago. In here some post get answered quickly, some need to wait longer for a respond, and some post do get ignored (intentionally / unintentionally).

Sometimes you just need to be patience or re-post in that thread to it bubbles up to the top of the "New Posts" list or re-phrase your sentence in a more "pleasing" way.

I guess threads created in these few weeks do tend to get lost in the blizzard of questions due to Feisty being released a few days ago.

I think what you need to do is:

[LIST]
[*] Not create a "this/that suxx" thread, cause it rarely do you any good in the long run. You'll be surprised by how many people in here who have excellent long-term memory.
[*] Try to be more specific in your question such as typing **lspci** in your command line and showing the output here
[/LIST]

---

### Post by udayan18 on 2007-04-25
i hv already edited my post...n tld u abt the reason for creating such a post(EXAMSSS)...if u felt offended by it...i really regret posting such a thread..m sry again

---

