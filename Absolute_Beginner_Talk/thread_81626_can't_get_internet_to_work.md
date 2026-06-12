---
title: "can't get internet to work?"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by JollyRoger on 2005-10-24
I can't seem to get my internet to work
(I'm using eithernet, cable)
I tried both the static IP address, and the DHCP (I think thats it?), and neither worked. I wasen't sure what to put in the Submask field for Static IP, but it put in a defult value, is this causing it not to work?

I know I'm pretty new at this stuff, but thanks anyway :)

---

### Post by ecobuntu on 2005-10-24
sudo network-admin

Make sure your eth0 is activated.  Deactivate it, then reactivate it, and hopefully this works for you.  If it's no eth0, then do this with your eth1 link.

Also try this 
ifconfig

And paste the results here.

---

### Post by JollyRoger on 2005-10-24
The activating and Deactivating didn't work, so the results of ifconfig:

John@John:~$ ifconfig
eth0          Link ehcap: Ethernet  HWA ddr  00:A0:01:23:80:A9
                inet addr: 141.209.194.15  Bcast: 141.209.255.255  mask: 255.255.0.0
                inet6 addr: fe80::2a0:d1ff:fe23:80a9/64  Scope: Link
                UP BROADCAST MULTICAST MTU: 1500  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuebeu: 1000
                RX bytes: 0 (o.o b)  TX bytes: 0 (0.0 b)
                Interupt: 11   Memory: bc000000-0

it also had a listing for "lo"  but did you need that?  I didn't feel like copying it down, because I couldn't copy this to a cd-rw because it wouldn't let me write on it for some reason, and I don't have a floppy drive, heh.


(Is it harmful to show my ip address like that?)

thanks for the help/info

---

### Post by cwaldbieser on 2005-10-24
[QUOTE=JollyRoger]The activating and Deactivating didn't work, so the results of ifconfig:

John@John:~$ ifconfig
eth0          Link ehcap: Ethernet  HWA ddr  00:A0:01:23:80:A9
                inet addr: 141.209.194.15  Bcast: 141.209.255.255  mask: 255.255.0.0
                inet6 addr: fe80::2a0:d1ff:fe23:80a9/64  Scope: Link
                UP BROADCAST MULTICAST MTU: 1500  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuebeu: 1000
                RX bytes: 0 (o.o b)  TX bytes: 0 (0.0 b)
                Interupt: 11   Memory: bc000000-0

it also had a listing for "lo"  but did you need that?  I didn't feel like copying it down, because I couldn't copy this to a cd-rw because it wouldn't let me write on it for some reason, and I don't have a floppy drive, heh.


(Is it harmful to show my ip address like that?)

thanks for the help/info[/QUOTE]

The card looks configured with an IP address.  What exactly is the problem?  Can you ping or traceroute to an IP address?
```

$ ping 68.142.226.37

```
Can you ping a DNS address like "www.yahoo.com"?  What's not working?

---

### Post by JollyRoger on 2005-10-24
well I just type any address into firefox and it dosen't load, and gaim also won't connect, but I'll try to ping something.

---

### Post by JollyRoger on 2005-10-25
In windows it says my connection is DHCP, and when Ubuntu was being installed the intaller said it could not detect the DHCP connection.  Do I need to install a driver for my ethernet controller or something like that?  I'm am also at a college, do you think their internet would not support linux for some reason?

thanks for the info again

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=JollyRoger]In windows it says my connection is DHCP, and when Ubuntu was being installed the intaller said it could not detect the DHCP connection.  Do I need to install a driver for my ethernet controller or something like that?  I'm am also at a college, do you think their internet would not support linux for some reason?

thanks for the info again[/QUOTE]
Well, it could be one of several problems.  The two most likely are:
1) DSN is not configured correctly.  You will be able to ping addresses, but you won't be able to resolve names.
2) You have a more general connectivity issue.

Try opening a terminal in Ubuntu and type:
```

$ sudo dhclient

```
This should try to automatically detect your network settings via DHCP.  If there are any errors in the output, post them back here.

---

### Post by JollyRoger on 2005-10-25
[QUOTE=cwaldbieser]Well, it could be one of several problems.  The two most likely are:
1) DSN is not configured correctly.  You will be able to ping addresses, but you won't be able to resolve names.
2) You have a more general connectivity issue.

Try opening a terminal in Ubuntu and type:
```

$ sudo dhclient

```
This should try to automatically detect your network settings via DHCP.  If there are any errors in the output, post them back here.[/QUOTE]

This is what it came up with:

john@John:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 8026
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/ath0/00:11:f5:78:da:b8
Sending on   LPF/ath0/00:11:f5:78:da:b8
Listening on LPF/eth0/00:a0:d1:23:80:a9
Sending on   LPF/eth0/00:a0:d1:23:80:a9
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


sorry its so long.

Do you think I have to install the drivers for the ethernet controller? (Is that what its called)  I found them on the internet for my computer, I'm just having trouble installing them

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=JollyRoger]This is what it came up with:

john@John:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 8026
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/ath0/00:11:f5:78:da:b8
Sending on   LPF/ath0/00:11:f5:78:da:b8
Listening on LPF/eth0/00:a0:d1:23:80:a9
Sending on   LPF/eth0/00:a0:d1:23:80:a9
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


sorry its so long.

Do you think I have to install the drivers for the ethernet controller? (Is that what its called)  I found them on the internet for my computer, I'm just having trouble installing them[/QUOTE]
Could be-- is your ethernet on a PCI card?  Try
```

$ lspci

```
and see if your ethernet card listed in the output.  If not, what kind of card is it?  What problems are you having installing the drivers?

---

### Post by JollyRoger on 2005-10-26
Yes, it is a PCI card.  I just get an error when installing it, this is from the install.log :

+++ Install mode: User
+++ Driver version: 8.28.1.2 (beta) (Sep-29-2005)
+++ Kernel version 2.6.12-9-386
+++ smp_count=0
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ Make not found
+++ Mismatch!!! Kernel:3.4.5 != gcc:4.0.2

thanks for your help

---

### Post by JollyRoger on 2005-10-26
this is what I got from lspci:

john@John:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04 )
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:06:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:06:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:06.4 0805: Texas Instruments: Unknown device 8034


My Ethernet controller is the Marvell Technology, and the Atheros is my wireless, but it says Uknown device afterwords...so does this mean I have to install a driver, or something else?

I really appreciate the help

---

### Post by JollyRoger on 2005-10-26
(bump)

thanks

---

### Post by jrw6 on 2005-10-26
Can you give us the output of:  ifconfig -a

I suspect your motherboard's onboard network card is getting detected as eth0.  Of course, since there's nothing plugged into it, it fails to get a DHCP address.  I don't think you're going to get the Marvell working, since it has an unknown PCI device ID - which means no-one writing Linux device drivers knows that this particular type of card exists.

I'm guessing your motherboard has an onboard ethernet port.  Plug your network cable into that and reboot.

---

### Post by cwaldbieser on 2005-10-26
[QUOTE=JollyRoger]this is what I got from lspci:

john@John:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04 )
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:06:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:06:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:06.4 0805: Texas Instruments: Unknown device 8034


My Ethernet controller is the Marvell Technology, and the Atheros is my wireless, but it says Uknown device afterwords...so does this mean I have to install a driver, or something else?

I really appreciate the help[/QUOTE]

Strange-- it recognizes the device, but not what it is.  Do you have a URL to the drivers you are trying to install?  I'll take a look at them so I can get so I can familiarize myself with the steps you are taking to install it.

---

### Post by JollyRoger on 2005-10-26
This is the download link:

[http://www.marvell.com/drivers/driverDisplay.do?dId=107&pId=10](http://www.marvell.com/drivers/driverDisplay.do?dId=107&pId=10)

and this is the readme for the driver:

[http://www.marvell.com/drivers/driverDisplay.do?dId=120&pId=9](http://www.marvell.com/drivers/driverDisplay.do?dId=120&pId=9)

It kind of looks like a general Linux driver for the Yukon line of ethernet boards

I really apreciate the help...its frustrating not being able to use the internet heh.

---

### Post by JollyRoger on 2005-10-26
[QUOTE=jrw6]Can you give us the output of:  ifconfig -a

I suspect your motherboard's onboard network card is getting detected as eth0.  Of course, since there's nothing plugged into it, it fails to get a DHCP address.  I don't think you're going to get the Marvell working, since it has an unknown PCI device ID - which means no-one writing Linux device drivers knows that this particular type of card exists.

I'm guessing your motherboard has an onboard ethernet port.  Plug your network cable into that and reboot.[/QUOTE]

I'll try the ifconfig -a in a little bit, but I only see one ethernet port for my comp. (Its a laptop), unless I'm just being blind heh.

---

### Post by cwaldbieser on 2005-10-27
[QUOTE=JollyRoger]Yes, it is a PCI card.  I just get an error when installing it, this is from the install.log :

+++ Install mode: User
+++ Driver version: 8.28.1.2 (beta) (Sep-29-2005)
+++ Kernel version 2.6.12-9-386
+++ smp_count=0
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ Make not found
+++ Mismatch!!! Kernel:3.4.5 != gcc:4.0.2

thanks for your help[/QUOTE]

OK, this error is saying that the version of gcc you have installed is 4.02.  However, the version of gcc used to build your kernel (which you can find with "cat /proc/version") is 3.4.5.  I am not exactly sure what to do about that--  I will ask over on the programming forum if anyone knows if there is some sort of compatibility mode...

---

### Post by JollyRoger on 2005-10-27
[QUOTE=cwaldbieser]OK, this error is saying that the version of gcc you have installed is 4.02.  However, the version of gcc used to build your kernel (which you can find with "cat /proc/version") is 3.4.5.  I am not exactly sure what to do about that--  I will ask over on the programming forum if anyone knows if there is some sort of compatibility mode...[/QUOTE]

cool, thanks

---

### Post by cwaldbieser on 2005-10-27
[QUOTE=JollyRoger]cool, thanks[/QUOTE]
OK, it turns out that you can just get gcc-3.4 from the repositories and you can try to compile with that.  I am not sure if that will replace your current gcc in your PATH.  Once you get it installed, try 
```

$ gcc -v

```
and look at the last line to see if you have the correct version in the PATH.
You may have to just change the gcc symlink to point to the correct version of gcc, or maybe you could just create a bash function called gcc that calls the version you want.

---

### Post by JollyRoger on 2005-10-27
[QUOTE=cwaldbieser]OK, it turns out that you can just get gcc-3.4 from the repositories and you can try to compile with that.  I am not sure if that will replace your current gcc in your PATH.  Once you get it installed, try 
```

$ gcc -v

```
and look at the last line to see if you have the correct version in the PATH.
You may have to just change the gcc symlink to point to the correct version of gcc, or maybe you could just create a bash function called gcc that calls the version you want.[/QUOTE]

How do I go about changing the symlink of gcc?

I noticed that one of the requirements was the source of the Linux kernel:



To install the sk98lin driver the following files
and tools on your Linux system are required:

- Linux kernel source available in directory /usr/src/linux

- Compiler tools (e.g. gcc)


And I don't have anything in /usr/src/linux

maybe that would be a problem too, do you know how I should get the source of linux into there?

thanks a lot, I really appreciate the help :)

---

### Post by Mustard on 2005-10-27
For the linux-source you would need to find the version of your kernel by entering...
```
uname -r
```

Then you could go to synaptic, enter 'linux-source' in the search field and install the one that matches with the version that uname -r says you have.

You may also need to install the 'build-essential' package via synaptic, as this contains essential components for compiling stuff.

---

### Post by JollyRoger on 2005-10-28
[QUOTE=cwaldbieser]OK, it turns out that you can just get gcc-3.4 from the repositories and you can try to compile with that.  I am not sure if that will replace your current gcc in your PATH.  Once you get it installed, try 
```

$ gcc -v

```
and look at the last line to see if you have the correct version in the PATH.
You may have to just change the gcc symlink to point to the correct version of gcc, or maybe you could just create a bash function called gcc that calls the version you want.[/QUOTE]

(bump)

I was just wondering how I could do either one of these?  (Change the cymlink for gcc or create a bash function to point to it), because when I type in gcc -v it still shows the newer version.

thanks :)

---

### Post by cwaldbieser on 2005-10-28
[QUOTE=JollyRoger](bump)

I was just wondering how I could do either one of these?  (Change the cymlink for gcc or create a bash function to point to it), because when I type in gcc -v it still shows the newer version.

thanks :)[/QUOTE]
For the symlink, you need a root shell (so be careful!):
```

$ sudo bash
# rm /usr/bin/gcc
# ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

```

The function doesn't require root mode, but you have to source it for each shell.  Make a file and put the following in it:
```

gcc () 
{ 
    /usr/bin/gcc-3.4 $@
}

```
Call the file something like "old_gcc".  Then at the terminal, you can just 
```

$ source old_gcc
$ gcc -v
Reading specs from /usr/lib/gcc/i486-linux-gnu/3.4.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,f77,pascal,objc,ada --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug i486-linux-gnu
Thread model: posix
gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)

```
You should probably source it from inside your ~/.bashrc file-- that way it will be done automatically, even if you start a new shell.

---

### Post by JollyRoger on 2005-10-28
[QUOTE=cwaldbieser]For the symlink, you need a root shell (so be careful!):
```

$ sudo bash
# rm /usr/bin/gcc
# ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

```

The function doesn't require root mode, but you have to source it for each shell.  Make a file and put the following in it:
```

gcc () 
{ 
    /usr/bin/gcc-3.4 $@
}

```
Call the file something like "old_gcc".  Then at the terminal, you can just 
```

$ source old_gcc
$ gcc -v
Reading specs from /usr/lib/gcc/i486-linux-gnu/3.4.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,f77,pascal,objc,ada --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug i486-linux-gnu
Thread model: posix
gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)

```[/QUOTE]


What do you mean by source it for each shell?  Do you mean I have to do it each time I want to do it?

---

### Post by JollyRoger on 2005-10-28
I don't think I can actually get gcc 3.4 from synaptic, or at least I don't really see it.  I see something like gcc 3.3, but nothing new showed up in /usr/bin/gcc

I don't think I have multiverse or universe installed because I think that needs the internet right?

Is there a way to download gcc 3.4 in wondows and put it into Ubuntu manually?

thanks, I appreciate it.

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=JollyRoger]I don't think I can actually get gcc 3.4 from synaptic, or at least I don't really see it.  I see something like gcc 3.3, but nothing new showed up in /usr/bin/gcc

I don't think I have multiverse or universe installed because I think that needs the internet right?

Is there a way to download gcc 3.4 in wondows and put it into Ubuntu manually?

thanks, I appreciate it.[/QUOTE]
Technically, you could go to some site like: [http://packages.ubuntu.com/breezy/devel/]("http://packages.ubuntu.com/breezy/devel/")
find the .deb files for gcc-3.4 and gcc-3.4 base, and install them with dpkg.  You need to make sure you meet the dependencies, though, so you might have to go back and forth installing even more .debs you don't have.

The easiest thing for you to do might be to find someone else who has a working Internet connection who can build and package the driver for you (because they have the card), or get someone to let you borrow a card you can get working until you can download the files you need.

---

### Post by JollyRoger on 2005-10-29
ok, so I got the .deb files for gcc 3.4 and I tried to install them, but it says I need super user privliges, I tried typing in gksudo naulilus before I installed it, but it still gave me that error, does anyone have any ideas as what to do?

thanks a lot

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=JollyRoger]ok, so I got the .deb files for gcc 3.4 and I tried to install them, but it says I need super user privliges, I tried typing in gksudo naulilus before I installed it, but it still gave me that error, does anyone have any ideas as what to do?

thanks a lot[/QUOTE]
I am a little rusty on the syntax, but I believe you want to open the terminal and "cd" to the folder where the .deb files are.  Then, you type:
```

$ sudo dpkg -i package.deb

```
for each package, substituting the actual .deb file name in for "package.deb".

---

### Post by JollyRoger on 2005-10-31
ok, so I installed gcc 3.4, and I got it to change the version alright, but now the installer gives me this:

+++ Install mode: User
+++ Driver version: 8.28.1.3 (Sep-29-2005)
+++ Kernel version 2.6.12-9-386
+++ smp_count=0
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ Kernel header not found. ln -s /usr/src/KERNEL_VERSION?



The installer says I should have the same version of the kernel as the kernel header:

- The kernel source and kernel version have to be consistent. 
  For instance, it might be, that you run kernel version 2.4.20, but 
  the header files the kernel module will be compiled with refer to 
  kernel version 2.4.21. If you don't have the same kernel version, 
  install the sources and compile a new kernel. It's not possible to 
  mix different kernel versions!

Does anyone know what I should do?

Sorry to keep coming back to this, but I really appreciate the help, I'm close to installing it, I swear heh.

thanks a lot again

(a little p.s., I made a symlink using the first method you described, and I was just wondering, is that just temporary? Should I do anything to "undo" it after the install?, or does it just change back to normal when I restart?)

thanks a lot :cool:

---

### Post by Mustard on 2005-10-31
```
apt-cache search linux-headers

```
...and pick and install the relevant headers for you kernel?

---

### Post by JollyRoger on 2005-11-04
I got past that part, but now when it tries to compile I'm getting an error:

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
Makefile:485: .config: No such file or directory
  Building modules, stage 2.
/usr/src/linux-headers-2.6.12-9-386/scripts/Makefile.modpost:38: .config: No such file or directory
make[1]: *** No rule to make target `.config'.  Stop.
make: *** [modules] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
+++ Compiler error


does anyone have any ideas?

Sorry to keep asking these questions, I'm still just really new to Linux.

thanks a lot :p

---

### Post by JollyRoger on 2005-11-05
(bump) heh

thanks

---

### Post by JollyRoger on 2005-11-09
Bump?

Thanks again

---

### Post by deamon on 2005-11-09
[QUOTE=JollyRoger]

Sorry to keep asking these questions, I'm still just really new to Linux.

[/QUOTE]

No need to appologise, you are posting in the Beginner Community > Absolute Beginner Talk after all.

:-({|=

---

