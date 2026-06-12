---
title: "ndiswrapper and wireless help on a laptop"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by todd_freeride on 2007-10-04
Hello. First off I will say ... I'm not as good with computers as most people. I'm great with windows, great with mac ...when I have to get something to work I can just simply download the drivers or pop in the instillation CD. But I'm having a huge amount of trouble with linux. Please help? :D 

My Computer Specs (I have a Dell Inspiron 1000 laptop) 256MB RAM, 2.2 Ghz non mobile ](*,) Celeron processor, 40GB toshiba hard drive, and ubuntu 6.06 installed. I Can upgrade to 7.04 or 7.1 if that is going to make things a ton easier. The only place where I can get eithernet is in the living room downstairs. Also, this is a laptop...so I really need wireless to work. My computer isnt the most fast out there, it really slow on Windows XP, but ubuntu seems to make the entire computer run quieter, cooler and faster.

My wireless card is a Netgear MA521wireless PC card. 802.11b at 2.4 ghz. RTL8180L Chipset.


alright, enough about specs. 

I was told to go to an icon (while plugged into the eithernet) called "restricted drivers manager" but I cant find that on 6.06 so I'm guessing thats a 7.04 thing? So I decided to install ndis wrapper and use a windows driver?

here is where my trouble kicks in. I'm using this information [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

"You need a recent kernel, at least 2.6.18 or 2.4.26, with kernel headers, and gcc-3.4 or newer. Make sure that /lib/modules/VERSION/build is a link to the kernel source."

How do I find out what Kernel I'm on? a link to the kernel source?

"extract it with
tar -zxvf ndiswrapper-version.tar.gz

This will create the ndiswrapper-version directory. Change to that directory with
cd ndiswrapper-version " 

Huh?

"Go to the source-directory and run make distclean and make. As root, run make install. This should compile and install both the kernel module and the userspace utilities. If you don’t need USB support in ndiswrapper, with recent versions, you can compile with make DISABLE_USB=1 and install with make DISABLE_USB=1 install." again .... huh ?

Sorry for the dumb questions... I think I just need all of this put into english instead of ubuntu. Again...is there just a much easier way to get linux working wirelessly? I know theres one card out there that supposedly works flawlessly with 6.06  am I just better off going and getting that rather than trying to get my MA521 to work? Would a different version of linux fix my problem?

Thank you so much if you read this far :p Thanks for your help.

---

### Post by kevdog on 2007-10-04
You need for your card ndiswrapper with the win98 drivers.  The native driver may work -- thats the r818x driver but Im not sure how stable it is during long transfers of information.  If you could, I would also upgrade to Feisty or Gusty -- Dapper is getting quite a bit dated and some of the new tricks dont work on that release -- thats just my opinion but Ive been down this path many times before.

---

### Post by todd_freeride on 2007-10-04
Alright, so now I'm a little more confused. I "upgraded" to 7.04, went to restricted drivers manager and it said "your hardware does not need any restricted drivers"

So does that mean that I have to use ndiswrapper? I still cant get wireless to work.

---

### Post by kevdog on 2007-10-04
Do the following for me (we are kind of experimenting at the moment)

Please post
lshw -C network

In the /etc/modprobe.d/blacklist file, are r818x and r8187 listed??  Is there something similar??


Thanks.

---

### Post by todd_freeride on 2007-10-04
> **kevdog said:**
> Do the following for me (we are kind of experimenting at the moment)

Please post
lshw -C network

In the /etc/modprobe.d/blacklist file, are r818x and r8187 listed??  Is there something similar??


Thanks.

uhh, where do I enter that information? in terminal? see....I have no clue what I'm doing :p

---

### Post by kevdog on 2007-10-05
Yes in a terminal

To check the file or see its contents, either open up an editor
gksu gedit /etc/modprobe.d/blacklist

or just list the contents at the command line
sudo more /etc/modprobe.d/blacklist

Either way you should be able to cut and paste the output.

---

### Post by todd_freeride on 2007-10-05
okay, so it is mentioning the r818x and r8187 

Here is what the terminal command " sudo more /etc/modprobe.d/blacklist " Gave me

" 
todd@Dell-Inspiron-1000:~$ sudo more /etc/modprobe.d/blacklist

# This file lists those modules which we don't want to be loaded by

# alias expansion, usually so some other driver will be loaded for the

# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much

# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
todd@Dell-Inspiron-1000:~$

---

### Post by kevdog on 2007-10-06
Try commenting out or simply putting a # sign in front of line that reads

blacklist r818x

You will need root privileges to edit the file:
gksu gedit /etc/modprobe.d/blacklist

Ok all the changes we did was for a reboot -- if you want to see if something works now without rebooting the following:

sudo modprobe r818x

Now Ive read that there is a problem with this driver in that a fake or extra character needs to be added onto the essid name to make it work.  I can not personally verify this but Ive read it alot. Assuming for example your essid of your network was ducky, to connect to ducky you would do the following

sudo iwconfig wlan0 essid duckyx
sudo dhclient wlan0

Again the x is the extra character.  This also assumes your wireless card is assigned wlan0.  It maybe something different such as eth1 or something else.  If you type lshw -C network at the command line, look under the section that pertains to your wireless card, and look for the line that states logical name, you will find your interface name.

---

### Post by todd_freeride on 2007-10-06
> **kevdog said:**
> Try commenting out or simply putting a # sign in front of line that reads

blacklist r818x

You will need root privileges to edit the file:
gksu gedit /etc/modprobe.d/blacklist

Ok all the changes we did was for a reboot -- if you want to see if something works now without rebooting the following:

sudo modprobe r818x

Now Ive read that there is a problem with this driver in that a fake or extra character needs to be added onto the essid name to make it work.  I can not personally verify this but Ive read it alot. Assuming for example your essid of your network was ducky, to connect to ducky you would do the following

sudo iwconfig wlan0 essid duckyx
sudo dhclient wlan0

Again the x is the extra character.  This also assumes your wireless card is assigned wlan0.  It maybe something different such as eth1 or something else.  If you type lshw -C network at the command line, look under the section that pertains to your wireless card, and look for the line that states logical name, you will find your interface name.


yea, so really none of that even did anything. it doesnt even know there is a wireless device installed. I tried editing "blacklist r818x" to "#blacklist r818x" and couldent even access that. when I click on connections, it just says "no network connection" I cant get ndis wrapper installed, I think thats what I have to get working just to run this windows driver to possibly..maybe..one day...get linux working on wireless. currently I'm really starting to think its not possible.

I've tried to get linux working 4 different times. this is my fourth time coming back to linux only to have it totally fail me as an OS. I'm sorry...I just have NO CLUE what I'm doing here. I dont even know where to start with this thing.

---

### Post by darrenlh on 2007-10-06
Todd - Wireless support in linux is still the dealbreaker for a lot of people trying to migrate to linux. Seeing as you yourself admit to being a complete noob at this, might I suggest that you try loading ndiswrapper using synaptic package manager? If you search for nidswrapper in synaptic, you will also see a program called ndisgtk. This is basically a gui for ndiswrapper.

You will need to load your windows driver somewhere easy to find, and hopefully it can work for you. Perhaps starting somewhere easy, we can get that card working, and ease you into it.

If it does not work, you have more options still...
You can use google and your own sweat to take a crash course in the command line, but for a small fee ($20), Linuxant has a GUI ndiswrapper driver loader, and some native support drivers for linux. It works great under ubuntu. I used this option when I was new to Ubuntu. The great thing is that you can download this program for I believe 30 days for free, and If it works then you pay afterward. I see on their site they support REALTEK.

Check it out [www.linuxant.com](www.linuxant.com)

Good Luck, once you get wireless going, I promise you will never go back!

---

### Post by kevdog on 2007-10-06
Hold on for a minute.  Dont give up on the native driver just yet. We are using all command line commands.

Make sure you commented out the 
r8187
r818x 

lines inside your /etc/modprobe.d/blacklist file. Use gksu gedit to make the changes.

Reboot.

Ok lets just check a few things.  Is the r818x driver associated with your card??
lshw -C network <---- Please post the above

Also is the module loaded??
lsmod | grep 818   <----Please post

Ndswrapper is a fallback and this is easy too, however you will need to find a copy of the win98 drivers for your card.  I dont know if you have these, so Im trying to get the native drivers up and running first!!   And dont pay anyone to setup ndiswrapper for you.  As with everything in life it will eventually break, or you will upgrade, and then you will have to have the knowledge of how to reinstall the driver.  Its not hard.

---

### Post by todd_freeride on 2007-10-07
> **kevdog said:**
> Hold on for a minute.  Dont give up on the native driver just yet. We are using all command line commands.

Make sure you commented out the 
r8187
r818x 
lines inside your /etc/modprobe.d/blacklist file. Use gksu gedit to make the changes.


Commented out?
> **kevdog said:**
> 
Ok lets just check a few things.  Is the r818x driver associated with your card??
lshw -C network <---- Please post the above

todd@Dell-Inspiron-1000:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:11:43:3c:2c:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.0.107 latency=173 maxlatency=11 mingnt=52 multicast=yes
       resources: ioport:1800-18ff iomemory:e4003000-e4003fff irq:21
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: wlan0
       version: 20
       serial: 00:09:5b:8c:b3:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b
       resources: ioport:1c00-1cff iomemory:24000000-240001ff irq:16
todd@Dell-Inspiron-1000:~$ 


> **kevdog said:**
> Also is the module loaded??
lsmod | grep 818   <----Please post

Ndswrapper is a fallback and this is easy too, however you will need to find a copy of the win98 drivers for your card.  I dont know if you have these, so Im trying to get the native drivers up and running first!!   And dont pay anyone to setup ndiswrapper for you.  As with everything in life it will eventually break, or you will upgrade, and then you will have to have the knowledge of how to reinstall the driver.  Its not hard.

todd@Dell-Inspiron-1000:~$ lsmod | grep 818
r818x                  89996  0 
ieee80211_rtl          80392  1 r818x
todd@Dell-Inspiron-1000:~$ 


Thank you so much for helping me with all of this mess. to make things worse now I installed ubuntu studio on my spare computer. so thats going to be hell because my PCI card completly locks ubuntu and prevents it from running. I figure I'll just get my laptop running linux first and then work on my other computer later. but theres the information that you requested. I did use the synaptic package manager and it said it was either downloading or installing something but I'm not totally sure what. so I might have ndis wrapper installed but I have no clue where to look to find out. I found the driver for my wireless card V 1.0 it was for like win 98, 2000, me etc. will this work? or do I need to hunt for a 98 exclusive diver?

---

### Post by todd_freeride on 2007-10-07
> **darrenlh said:**
> Todd - Wireless support in linux is still the dealbreaker for a lot of people trying to migrate to linux. Seeing as you yourself admit to being a complete noob at this, might I suggest that you try loading ndiswrapper using synaptic package manager? If you search for nidswrapper in synaptic, you will also see a program called ndisgtk. This is basically a gui for ndiswrapper.

You will need to load your windows driver somewhere easy to find, and hopefully it can work for you. Perhaps starting somewhere easy, we can get that card working, and ease you into it.

If it does not work, you have more options still...
You can use google and your own sweat to take a crash course in the command line, but for a small fee ($20), Linuxant has a GUI ndiswrapper driver loader, and some native support drivers for linux. It works great under ubuntu. I used this option when I was new to Ubuntu. The great thing is that you can download this program for I believe 30 days for free, and If it works then you pay afterward. I see on their site they support REALTEK.

Check it out [www.linuxant.com](www.linuxant.com)

Good Luck, once you get wireless going, I promise you will never go back!



I've went in and downloaded the ndisgtk and ndswrapper ( as a package thing or something like that) and it had a few loading bars and looked like it was doing something. so I think that I have ndiswrapper installed but I really have no clue. I've got my driver for the wireless card just saved onto the desktop. But every time I try to load it the window pops up asking what to   open some of the files with and no applications are ever selected. I will pay for the driver thing (if I can even figure out how to install that.)

---

### Post by darrenlh on 2007-10-08
Well, as mentioned above by kevdog, using the kernel module is the *best* way of running your card. If you are going to use ndisgtk, then you need to go to synaptic package manager select the package for installation, and click the apply button. You should then see the manager download and then install the software. If that is done correctly as it sounds like you did, you then go to System --> Administration --> Windows Wireless Drivers.

As for the windows driver, I am uncertain what would be the best, probably win98 would be a good start. Don't forget that for some cards you need both the *.inf file and *.sys file loaded. Once they are loaded, it should say "Hardware: present". A good thing to check too is to look at the *.inf file to make sure that it mentions your chipset, that tripped me up once trying to use a dell driver I downloaded.

If you try out the linuxant driver, just remember to use the *.deb package if they don't have  one that mentions Ubuntu specifically. *.deb is short for debian, which ubuntu is based on.
After I used the linuxant driver, I saw that I was in fact missing a specific file from my attempt to load ndiswrapper. Nowadays I just go ahead and attempt the kernel modules first, then go to ndiswrapper. Remember the trial is for 30 days, that gives you a month to figure it out :)

---

### Post by kevdog on 2007-10-08
Ok

Todd -- ok the r818x driver is loaded with wlan0 interface.

If you type the following in the command prompt, does this work:

sudo ifdown wlan0
sudo ifup wlan0
sudo iwconfig wlan0 essid duckyx
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Let me know what happens.  I can point you to a thread about ndiswrapper if this doesnt work.

---

### Post by todd_freeride on 2007-10-08
> **darrenlh said:**
> Well, as mentioned above by kevdog, using the kernel module is the *best* way of running your card. If you are going to use ndisgtk, then you need to go to synaptic package manager select the package for installation, and click the apply button. You should then see the manager download and then install the software. If that is done correctly as it sounds like you did, you then go to System --> Administration --> Windows Wireless Drivers.

As for the windows driver, I am uncertain what would be the best, probably win98 would be a good start. Don't forget that for some cards you need both the *.inf file and *.sys file loaded. Once they are loaded, it should say "Hardware: present". A good thing to check too is to look at the *.inf file to make sure that it mentions your chipset, that tripped me up once trying to use a dell driver I downloaded.

If you try out the linuxant driver, just remember to use the *.deb package if they don't have  one that mentions Ubuntu specifically. *.deb is short for debian, which ubuntu is based on.
After I used the linuxant driver, I saw that I was in fact missing a specific file from my attempt to load ndiswrapper. Nowadays I just go ahead and attempt the kernel modules first, then go to ndiswrapper. Remember the trial is for 30 days, that gives you a month to figure it out :)

I've tried using the terminal, but it just doesnt seem to be doing anything. so I've got the "wireless windows drivers" button, I click on it and begin to install. I told it to install two .inf files, but they didnt show up. there is still one .sys file but I have no clue how to get that. also the two files I loaded arent showing up saying they loaded, my computer just lags for a second then I'm assuming it was installed although it doesn't say anything. Also something new, I uncompressed this folder only to have these little lock icons over the files, could this be what might be causing a problem installing the drivers? I havent gotten a hardware present anything yet. 

Some screen shots of its failure. on the network icon on the top, it only says manual configuration. I can get more screen shots if needed, but am I doing anything wrong here?

(I can re size these if they're too big)

[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/Screenshot-1-1.png[/IMG]
[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/Screenshot-2.png[/IMG]

---

### Post by todd_freeride on 2007-10-08
> **kevdog said:**
> Ok

Todd -- ok the r818x driver is loaded with wlan0 interface.

If you type the following in the command prompt, does this work:

sudo ifdown wlan0
sudo ifup wlan0
sudo iwconfig wlan0 essid duckyx
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Let me know what happens.  I can point you to a thread about ndiswrapper if this doesnt work.

so this is what I ended up getting 

todd@Dell-Inspiron-1000:~$ sudo ifdown wlan0 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   Socket/fallback 
todd@Dell-Inspiron-1000:~$ sudo ifup wlan0 
Error for wireless request "Set Encode" (8B2A) : 
    invalid argument "kylealan". 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
todd@Dell-Inspiron-1000:~$ sudo iwconfig wlan0 essid duckyx 
todd@Dell-Inspiron-1000:~$ sudo iwconfig wlan0 mode Managed 
todd@Dell-Inspiron-1000:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
todd@Dell-Inspiron-1000:~$  

the wireless card still doesn't seem to work. do I have to be plugged into the eithernet to get this to work?

---

### Post by darrenlh on 2007-10-08
todd, in your example you set essid as duckyx, should that not be the name of your router? apart from that wlan0, your card absolutely works

---

### Post by todd_freeride on 2007-10-08
> **darrenlh said:**
> todd, in your example you set essid as duckyx, should that not be the name of your router? apart from that wlan0, your card absolutely works

yea, in expirementing. but my router name is "default" even when I set it to default it still doesnt work. how can I get to a wireless configuration screen? when I click on the network icon thing on the top, it just says "manual configuration" where here is my non working desktop with the menu I think I'm trying to get too (but this is when my computer locked up) 

[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/IMG_3807-1.jpg[/IMG] also do I need that one .sys file or something?

---

### Post by darrenlh on 2007-10-08
make sure to disconnect wired ethernet, as it may wish to default to eth0. I see that you have no encryption on, so after a minute or two, it should connect. Sometimes on ubuntu, it may be neccessary to turn off, and turn on the wlan card with the external switch if your laptop came with one. I have to do this sometimes, and it may take about 20 seconds for it to find the router. you do not need the .sys file. That would be if you are running ndiswrapper, which you are not. to change network settings go to system - administration - network. Thanks to kevdogs advice you are getting close.

---

### Post by kevdog on 2007-10-08
Lets change things up just a minute, but lets get one thing straight

You need to know the name or essid of the router you are connecting to.  Because of a bug in the r818x drivers you need to add a bogus symbol like x or a or b or any letter after the essid name.  So if your router essid is default, in the commands we are going to type below the essid will be defaultx.  Got it??

Can you post 
iwlist scan  
This will help me and show you all the wireless networks around you.

Now type the commands below, we can fine tune them later.  You are really close

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "RouterNamex"  <----notice extra character x here
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Thanks for the screen caps -- but those sure are shi**y

---

### Post by todd_freeride on 2007-10-08
> **kevdog said:**
> Lets change things up just a minute, but lets get one thing straight

You need to know the name or essid of the router you are connecting to.  Because of a bug in the r818x drivers you need to add a bogus symbol like x or a or b or any letter after the essid name.  So if your router essid is default, in the commands we are going to type below the essid will be defaultx.  Got it??

Can you post 
iwlist scan  
This will help me and show you all the wireless networks around you. 

This is what it gave me 

todd@Dell-Inspiron-1000:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 
todd@Dell-Inspiron-1000:~$ 

> **kevdog said:**
> Now type the commands below, we can fine tune them later.  You are really close

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "RouterNamex"  <----notice extra character x here
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0



I typed those in, and finally a little action in the wireless card. the "link" light is now on, however I have no internet connection and its not finding any local networks.

todd@Dell-Inspiron-1000:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 
todd@Dell-Inspiron-1000:~$ sudo ifconfig wlan0 down 
Password: 
todd@Dell-Inspiron-1000:~$ sudo ifconfig wlan0 up 
todd@Dell-Inspiron-1000:~$ sudo iwconfig wlan0 essid defaultx 
todd@Dell-Inspiron-1000:~$ sudo iwconfig wlan0 mode Managed 
todd@Dell-Inspiron-1000:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   LPF/wlan0/00:09:5b:8c:b3:02 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
todd@Dell-Inspiron-1000:~$

---

### Post by kevdog on 2007-10-08
If iwlist scan doesnt produce any networks, then you are not going to be able to connect, since iwconfig and iwlist are part of the same wireless tools package.  In fact if iwlist scan doesnt pick up any networks, no driver is going to work.

I find it curious that you posted a screenshot that listed 3 networks with network manager, but now you dont pick up any networks.  Does network manager "see" any networks??

To the best of my knowledge network manager relies on the wireless tools package (iwlist, iwconfig, iwpriv, etc), to negotiate network connections.

Did you move your laptop beyond network range??

---

### Post by todd_freeride on 2007-10-08
> **kevdog said:**
> If iwlist scan doesnt produce any networks, then you are not going to be able to connect, since iwconfig and iwlist are part of the same wireless tools package.  In fact if iwlist scan doesnt pick up any networks, no driver is going to work.

I find it curious that you posted a screenshot that listed 3 networks with network manager, but now you dont pick up any networks.  Does network manager "see" any networks??

To the best of my knowledge network manager relies on the wireless tools package (iwlist, iwconfig, iwpriv, etc), to negotiate network connections.

Did you move your laptop beyond network range??

no, I stated that the picture of the networks was on my ubuntu studio dekstop machine. We've been working on my laptop this whole time. the issue with my dekstop it tries to connect, but then freezes. 

Right now its on my laptop, I get a link light on the card, but I cant figure out how to get that drop down menu shown on my screenshot (actually a picture from my cell phone because the system locked and I couldent do anything) so how can I get that drop down menu? all it says when I click the computers is "wired connection" and "manual configuration".

well, I did get a bit further. I enabled roaming mode and got this (see pics below) but when I open up firefox and try to go to the web "page cannot be displayed" is there anything that I might have done wrong? do I have to tell my network to connect to "defaultx" ?

(sorry, cell phone pics)
[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/IMG_3809.jpg[/IMG]
[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/IMG_3808-1.jpg[/IMG]

---

### Post by kevdog on 2007-10-08
Yes make a manual connection and and tell it to connect to defaultx

Hmm I should have guessed it was a cell phone -- actually not too bad

---

### Post by todd_freeride on 2007-10-09
> **kevdog said:**
> Yes make a manual connection and and tell it to connect to defaultx

Hmm I should have guessed it was a cell phone -- actually not too bad

okay, where do I go to do this? I've typed in telling it to connect to defaultx and it doesnt connect. I typed in sudo dhclient wlan0 to get the link light back on. but that also didnt work. to get a network list on the dropdown menu I have to enable roaming mode. but for some reason it doesnt want to work.

Update, I got ubuntu to work wirelessly! BUT... now it doesnt work anymore. I had just pressed a ton of buttons, going in and clicking around, enabling roaming mode, then disableing it. trying to get it to connect, at times it will say "connected to default 98% and stuff, but it wont work. I got it running finally and the signal was pretty poor, but allowed me to install beryl (even though beryl does nothing but restart my machine) but I finally shut the computer down to see if the signal would pick back up, sure enough...it wouldent. is this because of my driver?

---

### Post by kevdog on 2007-10-09
OK, maybe its time to go to ndiswrapper, but Im going to give this native driver one last shot.

If you are seeing default listed in the dropdown menu, when you type
iwlist scan

Do you see the network default listed here also???

The command line and the GUI have nothing to do with one another.  They share some of the same programs to make the connection, but dont share data.

If you see default listed in the results of iwlist scan can you please type the following at the command line and at least show me what happens (a screen shot is OK):

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "RouterNamex" <----notice extra character x here
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

And just in case -- I dont know if you are doing this or not -- but you cant run a wired connection and wireless at the same time.  You need to bring down the wired connection and then bring up the wireless connection if you are doing so.  I you are not running a wired connection, my apologies.

---

### Post by todd_freeride on 2007-10-09
> **kevdog said:**
> OK, maybe its time to go to ndiswrapper, but Im going to give this native driver one last shot.

If you are seeing default listed in the dropdown menu, when you type
iwlist scan

Do you see the network default listed here also???

The command line and the GUI have nothing to do with one another.  They share some of the same programs to make the connection, but dont share data.

If you see default listed in the results of iwlist scan can you please type the following at the command line and at least show me what happens (a screen shot is OK):

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "RouterNamex" <----notice extra character x here
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

And just in case -- I dont know if you are doing this or not -- but you cant run a wired connection and wireless at the same time.  You need to bring down the wired connection and then bring up the wireless connection if you are doing so.  I you are not running a wired connection, my apologies.

okay, so here is what I got. (I'm just going to screen shot all this, maybe if someone else sees a visual they can also learn from it if they're watching this thread)

But no, I'm not plugged into the either net. UPDATE I told it to connect to "default" in the drop down menu, and I just let it sit for a while, eventually it connected. my guess is it might not like how far away from the router I am (b card, + 4 walls and 150 feet second story of the house). I'll try to run the native drivers first before turning to ndiswrapper. so it seems like I have to just let it sit for 5 mins.

[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/Screenshot-3.png[/IMG]
[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/Screenshot-4.png[/IMG]

---

### Post by kevdog on 2007-10-09
Ok weird but great you have a working connection.  If you are not happy with this connection or you are finding this connection to be frequently dropped, bad range, etc. then we can uninstall these drivers and then go for ndiswrapper.

If you elect for ndiswrapper I can help you, however you need the win98 drivers (as I think Ive mentioned).  Great to know the native drivers still work (with a twist)

---

### Post by darrenlh on 2007-10-09
Why don't you try changing the default channel from 6 to lets say 10 or something to rule out interference on the router?

---

### Post by todd_freeride on 2007-10-09
> **kevdog said:**
> Ok weird but great you have a working connection.  If you are not happy with this connection or you are finding this connection to be frequently dropped, bad range, etc. then we can uninstall these drivers and then go for ndiswrapper.

If you elect for ndiswrapper I can help you, however you need the win98 drivers (as I think Ive mentioned).  Great to know the native drivers still work (with a twist)


I think I'm going to have to go to ndis wrapper. when my laptop finally connects. its about 1/250 tries. this is my laptop, my only laptop. I need to have a working connection. 

Will a driver that is suitable for win98, ME, 2000, XP work? or does it have to be a specific win 98 driver?

Thanks again

-Todd

---

