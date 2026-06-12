---
title: "Cant make install in Gutsy 7.10"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2007-10-24
Can anyone tell me wat is wrong?  Seems I have build-essential...

sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@ubuntu:~$ cd Desktop
@ubuntu:~/Desktop$ cd rt2570-cvs-2007102319
@ubuntu:~/Desktop/rt2570-cvs-2007102319$ cd Module
@ubuntu:~/Desktop/rt2570-cvs-2007102319/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory. Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

---

### Post by realvz on 2007-10-24
i am not sure...but you might need to run "./configure" before actualling runnign "make" command

---

### Post by webbie180 on 2007-10-24
@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**build-essential is already the newest version**.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@ubuntu:~$ cd Desktop
@ubuntu:~/Desktop$ cd '/home/ching/Desktop/rt2570-cvs-2007102402' 
@ubuntu:~/Desktop/rt2570-cvs-2007102402$ cd Module
[B]@ubuntu:~/Desktop/rt2570-cvs-2007102402/Module$ ./configure
bash: ./configure: No such file or directory[/B]
@ubuntu:~/Desktop/rt2570-cvs-2007102402/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1
@ubuntu:~/Desktop/rt2570-cvs-2007102402/Module$ 

Tried ./configure but still didnt work.

---

### Post by realvz on 2007-10-24
there must be a readme file there or an install file there...can you check it for install instructions...

---

### Post by webbie180 on 2007-10-24
I was following this thread to get my wireless working but stuck at make install,

 HOWTO: Linksys WUSB54G V4 in Gusty 

[http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")

---

### Post by realvz on 2007-10-24
is there a readme or install file in the cvs?

---

### Post by webbie180 on 2007-10-24
This is the readme file I found,
Installation instructions for the rt2570 Module

======================================================================
Build Instructions:
====================
For 2.4 or 2.6 series kernel:

        a. $tar -xvzf rt2570-x.x.x.tar.gz
        go to "./rt2570-x.x.x/Module" directory.

        b. $make # compile driver source code

        c. $make install # installs kernel module driver

======================================================================
INVOCATION
====================
Load the driver:

        $modprobe rt2570 [ifname=<name>] [debug=<mask>]

        <name> is the name of the device and defaults to "rausb%d".
        If more than one adapter is installed, specify <name> in
        sprintf format (e.g. "wlan%d" - without the quotes).
        Successive devices will then be named rausb0, rausb1, etc., or
        (using the example) wlan0, wlan1, etc. If there are already
        wired ethernet devices named eth0 and eth1, then specifying
        <name> as "eth%d" gives the adapter the name "eth2".

        <mask> is a decimal or hex number. See TESTING file. Ignored
        if driver compiled without debug support.

Start it up:

        $ifup rausb0        # If using Debian

======================================================================
UTILITY
====================
Rutilt provides a GUI- based driver configuration facility.

======================================================================
CONFIGURATION:
====================
The RT2570 driver can be configured via following interfaces,
i.e. (i)"iwconfig" command, (ii)"iwpriv" command

        i) iwconfig comes with kernel.
        ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for
            details.

======================================================================
MORE INFORMATION
====================
If you want rt2570 driver to auto-load at boot time:

A) choose rausb0 for first RT2570 WLAN card, rausb1 for second
   RT2570 WLAN card, etc.

B) create(edit) 'ifcfg-rausb0' file in /etc/sysconfig/network-scripts/
   edit (or add the line) in /etc/modules.conf:
        alias rausb0 rt2570

C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-rausb0
        DEVICE='rausb0'
        ONBOOT='yes'

        NOTE:
        if you use dhcp, add this line too .
        BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, add the line
        GATEWAY=x.x.x.x

    in /etc/sysconfig/network

---

### Post by hyper_ch on 2007-10-24
I don't have an answer for you but if you are following a howto, it's better to ask in there as the author of the howto is very likely to be the most competent to give you an answer.

---

