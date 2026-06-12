---
title: "Network card not working (or Network for Newbies++)"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by wwwwolf on 2007-06-06
Hello, All;

I am quite new with Linux but fell in love with it and consider problems I face as an opportunity to learn new things. I am usually able to sort out my problems with with some reading and internet browsing, feeling very proud of myself when I finally come to the solutions.

In this particular case, though, I have been stuck for almost 3 weeks, reading back and forth on documents and HowTo's that most of the time sound greek to me. So, I am finally resorting to the community, hoping someone will have the time and inclination to shed some light on some (probably) very basic procedures.

This is the situation. I have installed Molinux (a Spanish distro based on Ubuntu) on an old laptop. It's a old Gateway that I had for some time. Previously, I had Ubuntu DD on it and it worked quite ok. After I changed to Molinux, the network card, a 3Com Megahertz (Model 3CCFE574BT), stopped working.

For the past few days I have been trying to understand how networking works in Linux and trying to make the card work. However, as I said, most of the time I am just issuing commands I am not familiar to or doing things without quite understanding the reasons - simply following instructions found on the internet.

According to what (I think) I know, the appropriate module is loaded in the kernel and the interface is mentioned in the "interfaces" file. But there is no network connection when I boot and if I try to issue a "ifup eth0" I get an error saying "No such device".

If I boot from a ZenWalk Live, the card works. So, it's not the cabling or the card. Is there a way to copy the configuration used by the Live CD to fix my current installed environment?

I am sure it is something simple but because I lack the basics, I just don't get it.

Would anyone be willing to detail, "from the cable onwards" what are the tools (commands) and procedures to manually have the network recognized and operational? And, would anyone be willing to help getting my network card connected?

I am attaching some info collected for reference.

Thanks in advance.

Cheers

---

### Post by mainalisuyog on 2007-06-06
Do you have dhcp running? Or do u use a static/manual IP? for static IP, you could run
 ifup eth0 xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy
where xxx.xxx.xxx.xxx is your ip address and yyy.yyy.yyy.yyy is the subnet mask. For eg:
ifup eth0 192.168.0.22 255.255.255.0

---

### Post by wwwwolf on 2007-06-06
Hi; Thanks for reading.

Yes, DHCP is enabled at the router and IPs are assigned without problem when I boot using a different Live CD. It all works if I boot with Zenwalk Live, for example. Just for the sake of it, I tried your suggestion. The result was the same:

root@psique:/# ifup eth0 192.168.1.133 255.255.255.0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
Ignoring unknown interface 192.168.1.133=192.168.1.133.
Ignoring unknown interface 255.255.255.0=255.255.255.0.

I believe the problem lies before the actual IP assigning. Could it be that I am missing the config for eth0? Where would I do that? How do I check?

Cheers

---

### Post by Austin_KW on 2007-06-06
I dont see you LAN card in the output for lspci. I am guessing that it is on a cardbus slot hidden behind a bridge. What is the output from lspci on the working live boot.

---

### Post by Austin_KW on 2007-06-06
Actually it might be more useful to post the output from "lspci -tv" on the working OS.

---

### Post by wwwwolf on 2007-06-06
Hello, Austin. Thank you for reading.

I am attaching the results for 'lspci -tv' on both installed system (Molinux) and the boot on Zenwalk Live. They are exactly the same, apparently. I am also posting the 'lsmod', 'ifconfig' and 'dmesg' results for Zenwalk.

The lsmod is a lot shorter but mentions "3c574_cs". Just so I learn in the process, that means the module is loaded, right? As it is on the installed system, I believe.

What is the 'dmesg'? Is it the boot log? What happened during the boot? The live cd 'dmesg' has a line that says:

pcmcia: the driver needs updating to supported shared IRQ lines.
  ASIC rev 1,<6>eth0: Megahertz 574B at io 0x300, irq 10, hw_addr 00:01:03:81:BE:77.
 64K FIFO split 1:1 Rx:Tx, autoselect MII interface.

I guess this is what is supposed to happen... Should be because internet access works when I boot from the live cd. The eth0 starts by itself, at boot time. I do not have to 'ifup' it.

What do you think? What am I missing?

Cheers,

---

### Post by Dedoimedo on 2007-06-06
Hello,

Maybe you do not have a network card configured.

1. Install relevant driver.
2. Configure the network card.

1. Download the relevant source and compile it. You should end with a driver.ko. Install this driver by running:
sudo insmod driver.ko

2. Configure your card:
sudo ifconfig ethX xxx.xxx.xxx.xxx

Now, you can setup the DNS if needed (can be done via Preferences, also).

See if you can connect.

Upon reboot, this device will no longer be enabled. You will have to make it start on bootup.

Two choices:

1. Script
2. Place it in the default folder

1. Script (make a text file and save, e.g. network_script)

#!bin/bash

cd driver_directory
insmod driver.ko
ifconfig ethX xxx.xxx.xxx.xxx

Now, make this script executable and place it in init.d

sudo chmod +x network_script

cp network_script /etc/init.d/

Update the system, so it will take the script into consideration.

update-rc.d network_script defaults 


2. Default location

Copy the driver to:
/lib/modules/<KERNEL VERSION>/kernel/drivers/net/driver.ko

Be aware that method 2 will be reset every time there's a kernel update, so you'll have to recopy the driver.


See if this helps you.

Dedoimedo

---

### Post by Austin_KW on 2007-06-06
I don't see the problem.

Perhaps Dedoimedo is correct and you need a newer to download and install a newer 3c574_cs.

This is a 2.4 kernel? Does that distribution give you the option of booting a 2.6 kernel, it might work better as the pcmia stuff was redone for 2.6

---

### Post by wwwwolf on 2007-06-06
Hi, Dedoimedo and Austin;

Thanks for the assistance. Much appreciated.

I can see 3c574_cs in my lsmod listing. Doesn't that mean the driver is already loaded in the kernel? I do have a file named 3c574_cs.ko under /lib/modules/2.6.15-26-386/kernel/drivers/net/pcmcia/. When I tried inserting it with 'insmod' I got an error message that said:

"insmod: error inserting '3c574_cs.ko': -l File exists"

I tried to configure the card using 'ifconfig' but got the same message as before, saying

"eth0: ERROR while getting interface flags: No such device."

Austin, the kernel is 2.6.15-26-386 as reported by 'uname -r'.

It must be something in between the steps to have the network configured. I tend to think by elimination. I know the cable is good. I know the card works. I know the DHCP on the router is fine. I know the driver is loaded. But the system cannot see the interface eth0. What am I missing?

I read that in Linux, everything is a file. The printer, the video, all devices are files. Not sure if that is accurate or not but since the system cannot "see" eth0. Could it be a file missing? The eth0 file itself, if there is such thing at all? How do I link the kernel module to a device? Where do I check to see if such config is in place? Do I have to mount anything?

I am really lost here. Any other ideas?

Cheers

---

### Post by Dedoimedo on 2007-06-06
Try to re-download / re-compile the driver...
Dedoimedo

---

