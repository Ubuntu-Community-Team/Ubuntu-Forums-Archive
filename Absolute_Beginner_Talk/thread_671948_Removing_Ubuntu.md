---
title: "Removing Ubuntu"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by JavaBeans2007123 on 2008-01-19
After successive attempts to get the internet working on Ubuntu, I have given up. I would now like to remove Ubuntu from my dual-boot configuration and install Vista on the partition which is currently occupied by Ubuntu.

---

### Post by zipperback on 2008-01-19
> **JavaBeans2007123 said:**
> After successive attempts to get the internet working on Ubuntu, I have given up. I would now like to remove Ubuntu from my dual-boot configuration and install Vista on the partition which is currently occupied by Ubuntu.


Perhaps you might give me a chance to assist you, with a little bit of information, I am confident that we can get you up and running.

Please open a terminal window and provide the output from the following commands.

> 

lspci

lsusb

ifconfig

iwconfig





All of those commands will just print out information about the hardware configuration and what is being recognized at this moment. With that information we should be able to help you get online.


Also, please tell us which version of Ubuntu you are using, as well as if it is the 32bit or 64bit version as well.

Thank you

-zipperback
:popcorn:

---

### Post by zipperback on 2008-01-19
I forgot to mention. To open a terminal window......


Applications -> Accessories -> Terminal

- zipperback
:popcorn:

---

### Post by ugm6hr on 2008-01-19
Don't want to detract from Ubuntu: most people *can* get ethernet to work with advice.

But assuming your current dual-boot is with XP - read this before deleting Ubuntu:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by adileader on 2008-01-19
If you have ethernet card then type : sudo pppoeconf and just folow the instructions I am sure that this will work if you have eth

After that just type pon dsl-provider

---

### Post by ugm6hr on 2008-01-19
Perhaps if people are going to offer advice - it would be best to start from correct info: [http://ubuntuforums.org/showthread.php?t=649001](http://ubuntuforums.org/showthread.php?t=649001)

Ethernet & DSL router with cable modem.
DHCP, IP assigned, but apparently unable to ping internet.

First - try pinging the router:
```
ping 192.168.1.1
```

The problem appears to be that DHCP has assigned the IP as 192.168.1.1 (instead of 192.168.1.101 as indicated in the settings page).  Unfortunately, this is the same IP as the router - hence the problem with connection to the gateway.

I have never encountered this, but perhaps someone else has?

---

### Post by mikewhatever on 2008-01-19
> **JavaBeans2007123 said:**
> After successive attempts to get the internet working on Ubuntu, I have given up. I would now like to remove Ubuntu from my dual-boot configuration and install Vista on the partition which is currently occupied by Ubuntu.

Generally speaking, all you need to do is start the installation process (not sure how it's done with Vista) and select the required partition. The partition will be formatted in the process and Grub boot loader overwritten from the MBR.
Good Luck.

---

### Post by louieb on 2008-01-19
Really weird. I'll throw just about any old Ethernet card in - never seen Ubuntu  fail to make a wired connection. Just for grins I'd check the install CD. Boot to it and run the media check and see if you get any errors. 
If so burn another CD and try the install again.

In any case, heres the best guide I know of for getting rid of Ubuntu or any Linux distro that uses GRUB. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

