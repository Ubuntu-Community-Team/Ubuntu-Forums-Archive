---
title: "Problems installing 3Com NIC"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by TraderEyal on 2005-10-08
Hey, This is my first Linux installation. I'm having trouble installing the LAN driver. The instructions are shown below, I'm not sure where the source is .. and step no. 6 gives a "command not found" for the make and no such file or director for the insmod command.. any advise would be great!

Thanks
Eyal

This file describes the 3Com Gigabit NIC (3C2000) driver for Linux.  

Loading the driver
------------------

1) Make sure that the kernel source is installed in /usr/src/linux
   or /usr/src/linux-2.4.

2) Copy the file /Linux/3c2000.tar.gz from the 3Com driver CD to 
   your hard drive.

3) Change to the directory containing 3c2000.tar.gz

4) Type 'tar zxvf 3c2000.tar.gz'

5) Type 'cd 3c2000'

Note: on SuSE systems since 7.1, you will have to execute the
following commands before running make:

cp /boot/vmlinuz.version.h /usr/src/linux/include/linux/version.h
cp /boot/vmlinuz.autoconf.h /usr/src/linux/include/linux/autoconf.h

For more details se [http://sdb.suse.de/en/sdb/html/mwalter_kernel_24.html](http://sdb.suse.de/en/sdb/html/mwalter_kernel_24.html)

6) Type 'make load' to load the driver.

Alternatively, you may type the following to load the driver: 

	insmod 3c2000.o

Something like the following will be added to /var/log/messages:

Jan 22 19:31:19 localhost kernel: 3C2000: 3Com Gigabit NIC Driver Version A08
Jan 22 19:31:19 localhost kernel: Copyright (C) 2003 3Com Corporation.
Jan 22 19:31:19 localhost kernel: Copyright (C) 2003 Marvell.
Jan 22 19:31:19 localhost kernel: eth0: 3Com Gigabit NIC (3C2000)

Depending on your configuration, the OS may then automatically bring the
interface up and request an address from a DHCP server.  If it does not,
bring the interface up with the command:

	ifconfig eth0 up

You may have to substitue 'eth0' for your actual interface if you have
more than one ethernet NIC installed.

If your system is not configured for DHCP, you can assign an IP address
with the command:

	ifconfig eth0 a.b.c.d

Where a.b.c.d is the IP address that you wish to use.  Again, eth0 may
be different depending on your system configuration.  

Configuring the Driver 
------------------------

    The 3C2000 driver supports various options, which can be supplied 
    as command line arguments to the 'insmod' command or in the 
    /etc/modules.conf file. You may specify more than one option.
    Unless otherwise stated, all settings take the form of:
    	
    	<Option-Name>=value [,value...]

    If you use the modules.conf file to load the driver at boot time, 
    include the word "options" when configuring the driver.

    For example:  
	options 3c2000 DupCap_A=Full
	
    If you use command line 'insmod', do not include the word "option"
    when configuring the driver. 

    For example: 
 	insmod 3c2000.o DupCap_A=Full
		
                                                                              		
  The following options are supported:

  OPTION: Speed_A
    Selects the speed of Port A of the NIC.  

	"Auto" - Automatic Resolution
	"10"   - 10MBPS
	"100"  - 100MBPS
	"1000" - 1GIG

  OPTION: DupCap_A
    Selects the duplex capabilities of Port A of the NIC.

	"Full"  - Full Duplex
	"Half"  - Half Duplex
	"Both"	- Both Half Duplex & Full Duplex


To unload the driver
--------------------

1) Type 'ifconfig eth0 down' (Substitute you actual interface for 'eth0')

2) Type 'rmmod 3c2000'

---

### Post by mlomker on 2005-10-08
> Hey, This is my first Linux installation. I'm having trouble installing the LAN driver. The instructions are shown below, I'm not sure where the source is .. and step no. 6 gives a "command not found" for the make and no such file or director for the insmod command.. any advise would be great!

[How-to]("http://ubuntuforums.org/showpost.php?p=361253&postcount=10") for installing the kernel source.

When you get to step 6 the command is:

```

sudo modprobe 3c2000

```

---

### Post by TraderEyal on 2005-10-08
Hi mlomker. thanks for the reply.

I tried the code and got an error message Couldn't find package linux-tree

I'm on Kubuntu if that changes anything?

I tried installing this through the Adept Manager and a linux directory was added to the /usr/include (but not to src) 

The modprobe command gave an error Module 3c2000 not found..

Where do I go from here? :)

Thanks
Eyal

---

### Post by TraderEyal on 2005-10-08
One more thing, I did apt-cache search for kernel-source and linux-source and it did not return any result.

---

### Post by TraderEyal on 2005-10-09
I managed to get the source installed. But still can't load the driver.

neither the make load, insmod or modprobe commands go through. I get either
make: command not found
insmod: can't read 3c2000.o no such file
modprobe: Module 3c2000 not found

Any other advice?

Thanks!
Eyal



[QUOTE=mlomker][How-to]("http://ubuntuforums.org/showpost.php?p=361253&postcount=10") for installing the kernel source.

When you get to step 6 the command is:

```

sudo modprobe 3c2000

```[/QUOTE]

---

### Post by mlomker on 2005-10-09
> make: command not found


If **make** isn't found then it isn't compiling anything:

```

sudo apt-get install build-essentials

```

---

