---
title: "Wireless card and ATI Graphics card Driver help"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Sir Warner on 2008-02-25
Issue #1
Alright- I have tried for 3 days, searching the net and these forums for help with my "Netgear 54Mbps Wireless PCI Adapter 32-bit PCI WG11v3" Wireless card on my e-machine desktop. I got a crash course on the terminal and NOW in the terminal I get this stuff:

timothy@Skylar2:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present
timothy@Skylar2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

when I go to System>Administration>Wireless Drivers, It says it's installed. but when I disconnect the Ethernet cable... No wireless.

Issue #2
I recently found the System>Administration>Restricted drivers manager, and found out my Radeon Xpress 200G is "Not in use" and attempts to install it have been pointless.

Welp- Not too bad for 4 days old into the world of Linux. Any help would make me exceptionally happy.

---

### Post by deepclutch on 2008-02-25
^well,u should try to see the o/p of "ifconfig" "ifconfig -a" apart from lwconfig.
also,try ur luck by looking at the o/p of "lspci" command.may be u'd like to do  a "sudo update-pciids" before launching lspci.check for any netgear listing.


reg,ati driver,u have to enable repositories in ur /etc/apt/sources.list via synaptic or manual edit and have to update and upgrade when INTERNET is CONNECTED.then only will those modules available.

---

### Post by uberlube on 2008-02-25
Try the methods of installing your drivers here:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Repost here if your still having trouble :)

---

### Post by uberlube on 2008-02-25
Also, grab ENVY from the synaptic package manager and use that to install the ATI driver. Dont tamper with the restricted driver manager.

---

### Post by sloggerkhan on 2008-02-25
Well, here's a question. How well is the open source ati default driver working for you?
200G integrated is one of those things it's hard to be happy with no matter the driver.
If you find that the default open source driver doesn't work, and that clicking the check box in the restricted driver manager doesn't work, then maybe you need to think about the latest fglrx restricted driver.

---

### Post by Sir Warner on 2008-02-27
Ok, sorry about the wait- I have been freakishly busy!!

ATI Graphics card working. after a huge system update I went to System>admin>screens+graphics>>graphics card tab and changed driver to ATI>Radeon (fglrx) ((open source)) +thanks sloggerkhan+ and after a reboot, it's all looking good with me! (Except the opening ubuntu loading screen, my monitor just says "out of range" 

Wireless card still NOT working. heres some fresh stats for ya.

timothy@Skylar2:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D3:0F:95:EA  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe0f:95ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2724698 (2.5 MB)  TX bytes:352702 (344.4 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

timothy@Skylar2:~$ lspci
02:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
timothy@Skylar2:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present

**CLIP FROM "dmesg"**

[ 1515.491346] ndiswrapper version 1.45 loaded (smp=yes)
[ 1515.749748] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1515.749756] ndiswrapper (load_sys_files:216): couldn't prepare driver 'mrv8000c'
[ 1515.750695] ndiswrapper (load_wrap_driver:118): couldn't load driver mrv8000c; check system log for messages from 'loadndisdriver'

What the heck am I missing?!

---

### Post by deepclutch on 2008-02-27
well,edit /etc/usplash.conf and give the value a  800x600 may be to stop the display out of range problem ;)

and ndiswrapper logs suggests,u may better install a 64-bit driver for ur card :confused:

---

### Post by Sir Warner on 2008-02-28
The Graphics card was working fine, now it's rather odd... when I save any settings or anything- I restart, and before the splash screen comes on, a message pops up "Running in low graphics mode" so I select the right driver, again, the card is enabled and "working" but it's like whenever I change somthing it wont keep. even the slash screen resolution.

Wireless card- Unable o find 64 bit driver for it.

---

