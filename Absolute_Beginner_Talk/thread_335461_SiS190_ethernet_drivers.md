---
title: "SiS190 ethernet drivers"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by chatterbabies on 2007-01-10
I got a new computer to put Ubuntu on. I just love it! Want to use it as a server. Well I would like it to be a server/desktop but don't know if that is possible...anyway. It has Sis190 ethernet on board and stays connected for about 3 seconds. It is being identified as a Sis190 but I found the most recent version for linux on the Sis website. I have managed to gather I will need to "compile" them (whatever that is) but my main concern is if this is going to be possible at a command prompt on a server with no internet. If so could someone give me a "For Dummies" walk through on how to do this. I have a file called sis190191_linux.tar.gz
Any advice on a better way would be welcome.

Thanks bunches.

Maybe this isn't the right driver :( . This is what the readme.txt says in the file

//** Install sis190 module into linux kernel. **//

1. Install Fedora Core 3. (Currently only FC3 can be installed on 965 demo board.)

2. Download Linux kernel 2.6.9 or latter version from [http://www.kernel.org](http://www.kernel.org). The follwing examples are based on linux-2.6.9.

3. copy the kernel source to the location /usr/src/linux-2.6.9.

4. cp sis190.c /usr/src/linux-2.6.9/drivers/net

5. Edit the file "/usr/src/linux-2.6.9/drivers/net/Kconfig".
    a. Serach for the string "config SIS900"
    b. Add the following item below the item of SIS190.

config SIS190
        tristate "SiS 191/190 PCI Gigabit/Fast Ethernet Adapter support"
        depends on NET_PCI && PCI
        select CRC32
        ---help---
          Say Y here if you have a SiS 191/190 PCI Gigabit/Fast Ethernet adapter.

          To compile this driver as a module, choose M here: the module
          will be called sis190.  This is recommended.

6. Edit the file "/usr/src/linux-2.6.9/drivers/net/Makefile".
    a. Search for the string "obj-$(CONFIG_SIS900) += sis900.o".
    b. Insert "obj-$(CONFIG_SIS190) += sis190.o" to next line.

7. cd /usr/src/linux-2.6.9

8. Input the command 'make menuconfig'. Then the Linux Kernel configuration menu will be popped.
    a. Select "Device Drivers -->", "Networking support -->", "Ethernet (10 or 100Mbit) -->".
    b. Goto the item "SiS191/190 PCI Gigabit/Fast Ethernet Adapter support".
    c. Press space key to make this item marked with <M>.
    d. Save and exit the kernel configuration menu.

9. Make kernel and modules. Input the command 'make bzImage modules modules_install install'.

10. Reboot and Select the boot item "2.6.9".


//** Probe sis190 module **//

1. Input the command 'rmmod sis190'.

2. Input the command 'modprobe sis190'.

3. Input the command 'ifconfig eth0 <ip_addr>'.
    a. <ip_addr> is the IP address of sis190.
    b. example: 'ifconfig eth0 192.168.209.1'.

---

### Post by Modernity on 2007-01-10
yes, the desktop version can be run as a server, you just have to download and install the packages you want.

---

### Post by Iyatos on 2007-01-10
If it asks for Fedora Core then you probably have downloaded the wrong driver - Fedora is another Linux OS

---

### Post by chatterbabies on 2007-01-10
I have the driver CD that came with it but it only comes with drivers for Redhat and windows. Can I compile the windows into one that will work. I have the inf file and when I look in it it looks as though the driver is based on two or three different realtek drivers. . Anyone gotta clue how I can do this?

---

### Post by chatterbabies on 2007-01-10
can I follow a tutorial for using ndiswrapper or is that only for wireless cards.?

---

