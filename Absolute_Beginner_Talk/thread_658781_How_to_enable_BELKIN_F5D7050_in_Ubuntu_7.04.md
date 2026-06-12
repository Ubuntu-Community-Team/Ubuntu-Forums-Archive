---
title: "How to enable BELKIN F5D7050 in Ubuntu 7.04"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by manmohanpv on 2008-01-05
Hi Frnds,

I'm using dell inspiron with ubuntu 7.04. My system has a built in intel 3945ABG wireless card. I have wicd installed and able to connect my wireless home router.

Recently i purchased BELKIN F5D7050 (FCC ID RAXWN4501H, IC 4711A-WN4501H) USB wireless adapter

I'm trying to install and no idea about the driver or chipset used in the adapter.

Anybody, please guide me in installing this wireless adapter and i would like to have a switching option between my intel and belkin wireless adapter.

Please help

-thanks
manmohanpv

---

### Post by Deadmode on 2008-01-05
[http://ubuntuforums.org/showthread.php?t=252465](http://ubuntuforums.org/showthread.php?t=252465)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

take a look at that thread and this guide to use ndiswrapper and compile a driver for it.  Also, I would look into updating to 7.10 I read that the wireless adapter works with Gutsy.

---

### Post by doorknob60 on 2008-01-05
Just curious, is there any reason you want to switch between them?

---

### Post by manmohanpv on 2008-01-05
I'm trying to do some penetration testing. some softwares do not support intel wireless card, so i thought belkin would be good choice. 

Why i need to switch is, i'll be using belkin only when i need to do the test (its an usb, i need to carry). Most of the other time i'll be connected through the built in intel wireless card.

Do you have a different idea?

-thanks
manmohan

---

### Post by Deadmode on 2008-01-05
In that case perhaps you should disable your intel wireless card if you aren't going to be using it anymore.  Otherwise I think they may conflict.

[http://ubuntuforums.org/showthread.php?t=512020](http://ubuntuforums.org/showthread.php?t=512020)

Here is a thread discussing disabling internal wireless cards.

---

### Post by manmohanpv on 2008-01-05
Thanks, looks like there is no conflict

I tried using both, but system in connecting to the router through Belkin(eth2) and there is no IP address assigned for intel(eth1). Any idea why? can i connect both cards to different access points, then which IP will be used while browing? just curious....

when i remove belkin and boot, it works fine with ipw3945abg

**For information**, i never blacklisted any drivers (i'm using Ubuntu 7.04)

i just downloaded latest build files and headers (look at the link above). The driver for belkin f5d7050 v4 is included with kernel 2.6.15, so there is no need to install driver separately( if you are using ubuntu 7.04 or higher)

thanks guys

manmohan

---

### Post by jonnywombat on 2008-01-05
I use the same belkin usb wireless stick. It has complete native support in 7.10... If it were me I would upgrade to 7.10.. but thats me..

I tried getting it working under 7.04 with ndiswrapper but could never get WPA encryption working properly, and eventually gave it up as a bad job.

---

### Post by manmohanpv on 2008-01-05
why do u need to use ndiswrapper if you have the drivers with the kernel

what you need to do with 7.04 is :-

1. Prepare the Linux Build Environment

user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build


2. Edit etc/network/interfaces file

add eth2 interface for the belkin

3. connect ur belkin to your usb adapter and boot

Now you have both ipw and belkin, but system assigns IP address to eth2 interface, not sure why it doesn't  pick intel wireless card(built-in)

-thanks
manmohan

---

