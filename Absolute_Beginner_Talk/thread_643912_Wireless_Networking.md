---
title: "Wireless Networking"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by browning_man9 on 2007-12-18
Hey! I finally installed ubuntu, but I am having some problems getting my wireless network up and running. Here are some of the things i've checked:

My wireless network card is listed in the device manager.

I brought in the driver file anyway from windows and did a: ndiswrapper -i desktop mrv8335.inf and it says that the driver is already installed.

I did a sudo lshw -c network and its listed.

However, when I do an iwconfig i get:
L0 no wirelesss extensions
eth0 no wireless extensions

Could someone please help me through this?

---

### Post by lvleph on 2007-12-18
did you try

```
sudo modprobe ndiswrapper
```

and then add the following to /etc/modules
```
ndiswrapper
```

---

### Post by browning_man9 on 2007-12-18
Thanks for responding. I don't know that it did anything.

However, when I do an ndiswrapper -l it says that MRV8335.sys does not exist. I've been doing a lot of reading at I think that you are supposed to be using .inf files. However, my current windows driver is a .sys file (I dont know what kind of difference this makes). So, my current sitution is:

I have the file MRV8335.sys on my desktop. How do I correctly install this driver?

Thanks.

---

### Post by Rplus9 on 2007-12-18
I wish I had an URL for you but it shouldn't be to hard to google.

However, with my wireless I required two .sys and one .inf

the .inf file was what I did the 
$ sudo ndiswrapper -i wusb54gsc.inf

however immediatly after I need to 
$ sudo cp *.sys /etc/ndiswrapper/wusb54gsc/

once you get the right .sys files in that ndiswrapper/"your driver here" folder things should check out when you 
$ ndiswrapper -l

Right now I'm having issues chaning kernels, once I upgraded the step

$ sudo modprobe ndiswrapper
FATAL: Module not found

I havn't figured out where I'm missing something.

---

### Post by browning_man9 on 2007-12-18
Is it possible that I only need a .sys file? When I type in sudo ndiswrapper -i mrv8335.sys, it says that it's already installed. So, now what?

---

### Post by lvleph on 2007-12-18
There should be 3 files; an inf, a sys, and some other file. The inf is the one you want to install, but ndiswrapper still needs the other two files.

If that doesn't help, I am sorry, I won't be much more help.

---

### Post by coolbrook on 2007-12-18
Try

sudo depmod -a

then...

> **lvleph said:**
> 

```
sudo modprobe ndiswrapper
```

---

### Post by mukul_d on 2007-12-18
Forgive me for asking, but what version of Ubuntu are you using & what is the hardware that you are using? In the latest versions, it should not be this difficult to use Wireless. Most of the cards are configured automatically. 

I suspect your wirelss card is already configured but is in Disabled state. You might have to enable it in BIOS (I had to do that a couple of times myself on multiple hardware platforms to enable wireless radio).

---

### Post by browning_man9 on 2007-12-18
I am using Ubuntu 7.10...And the hardware is a Marvell 802.11g Wireless PC Card...and the driver is MRV8335XP.sys..

Now I downloaded the zip file which contains the .inf file....the .sys file....and the .cat file....I am going to put them on my thumb drive and place them on the desktop in linux....Now can someone tell me the correct commands to run from the terminal?

Or perhaps tell me something else to do? Thanks

---

### Post by browning_man9 on 2007-12-18
Alright.....If I type: sudo ndiswrapper -i mrv8335.inf it says driver already installed....
Then i Type cd desktop......then sudo cp mrv8335.sys /etc/ndiswrapper/mrv8335....

How can I tell if my driver is properly installed? What is my next step? Thanks.

---

### Post by coolbrook on 2007-12-18
```

ndiswrapper -l

```

If it doesn't show that a device is present with the driver then you'll have to find a better driver.

```
sudo depmod -a
sudo modprobe ndiswrapper
```

Check with *ifconfig* and *iwconfig*

---

### Post by browning_man9 on 2007-12-18
Alright I did some more playing and think I'm heading in the right direction. I think I finally got the driver to install because when I type:

ndiswrapper -l, I get:
mrv8335: Driver Installed
     device(11AB:1FAA) present

Now, when I type ifconfig or iwconfig, I get the follwing entries:

eth0
lo

Judging from the Hardware Address of "eth0", it is my onboard LAN. And lo is some loopback thingy. Shoudln't my wireless card be showing up here also? Thanks, I appreciate this. I am learning alot with your help.

---

### Post by browning_man9 on 2007-12-18
When I type: sudo lshw -C network, the device is listed. The first line says *Network Unclaimed. Don't know if that is something important. I believe I have the driver installed, why isn't it showing up when I do an iwconfig?

---

### Post by Rplus9 on 2007-12-18
> **browning_man9 said:**
> Alright I did some more playing and think I'm heading in the right direction. I think I finally got the driver to install because when I type:

ndiswrapper -l, I get:
mrv8335: Driver Installed
     device(11AB:1FAA) present

Now, when I type ifconfig or iwconfig, I get the follwing entries:

eth0
lo

Judging from the Hardware Address of "eth0", it is my onboard LAN. And lo is some loopback thingy. Shoudln't my wireless card be showing up here also? Thanks, I appreciate this. I am learning alot with your help.

If the device is present I usually do the next few
$ ndiswrapper -m
this places the file: /etc/modprobe.d/ndiswrapper
in the /etc/modprobe.d/ndiswrapper file it says something like alias wlan0 ... I forget the rest
now from the "man modprobe" I learned that that folder "/etc/modprobe.d/ is where modprobe gets the extra modules.

continuing:
$ modprobe -n ndiswrapper
this does a "dry run" so you can make sure things are good before modprobe goes and does things you might not understand (I don't...)
if that's good then you're doing well.
$ modprobe ndiswrapper
this does the modprobe for real.

then for fun you do

$ dmesg | grep ndiswrapper
should reveal the portion of dmesg relating to ndiswrapper

again if that's there you're card should be good to go.  Check your network manager... maybe reboot.  If you keep losing your wireless on reboot, there are a couple of ways to fix that but I don't have my notes handy.
I'll post again with that info.

My question to folks smarter than I is this:  what about upgrading a kernel would cause a conflict in Modprobe?  In my old kernel 2.6.22-14-generic my wusb54gsc USB wireless worked fine (but caused kernel panic) now in 2.6.23 the ndiswrapper -l shows the device present and happy but

$ sudo modprobe ndiswrapper
FATAL: Module not found

the only traces of ndiswrapper that I can find are in 
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper/wusb54gsc

And I want to figure out what the ndiswrapper.ko file is about.

---

### Post by browning_man9 on 2007-12-18
Thanks for the reply.... everything went good, until the last thing. Maybe one of you can decipher what it is telling me. My wireless network was still not listed in my network manager....

dave@dave-ubuntu:~$ sudo modprobe ndiswrapper 
dave@dave-ubuntu:~$ dmesg | grep ndiswrapper 
[  241.102488] ndiswrapper version 1.45 loaded (smp=yes) 
[  241.146026] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B 
[  241.146035] ndiswrapper (load_sys_files:216): couldn't prepare driver 'mrv8335' 
[  241.146891] ndiswrapper (load_wrap_driver:118): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver' 
[  241.153261] usbcore: registered new interface driver ndiswrapper 
dave@dave-ubuntu:~$

---

### Post by x-to-tha-t on 2007-12-18
Sorry I haven't read much of this thread, but if you are having problems with WPA or DHCP (static/auto IP) then try switching from the Ubuntu standard network manager to WiCD - It fixed all of my problems straight up. Also if you are using WPA try switching it off first. Having it switched on while trying to set up wireless is just gonna make things difficult.

---

### Post by Rplus9 on 2007-12-19
For the benifit of others,

It does look like there is some 64/32 bit issue with your drivers.  I don't know why but I imagine that switching to a 32bit Ubuntu would make it work.

Also the best advice I have for learning this stuff is take notes! lots of them.  Write down every bit of syntax and your best understanding of what it is doing and why you did it.  When you come back to some of these problems it will make a world of diffrence.

---

