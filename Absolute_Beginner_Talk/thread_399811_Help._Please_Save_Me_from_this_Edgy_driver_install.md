---
title: "Help. Please Save Me from this Edgy driver install"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-04-02
I hope someone can show me the path -- surely there is an easier way given the situation below.

I have a Lenovo 3000 N100 laptop, and it has the intel 3945 wireless adapter.

Previously when I used **Ubuntu 6.06 Dapper**, the wireless hardware was detected and properly interfaced with at installation.

But when I do a clean, reformated install ***with 6.10 Edgy Eft, this piece of wireless hardware is not installed at the time I put on the OS***.  Hmmm?   Backwards progress?

I've done my Googling and found that I can install drivers (intel 3945 Linux) and the install process is only ... ten pages long.  Here it is **[COLOR="Lime"][here]("http://www.commonmancomputing.com/3945.txt")[/COLOR]**.

Since an older version of Ubuntu used to automatically detect and configure this particular hardware, I am figuring there must be some mistake on my part in understanding.

Since the wireless doesn't show up in Networking Options now with Edgy Eft, is there any easy thing I can do to get it there minus the 10 pages of instructions?

Thank you!

---

### Post by mikewhatever on 2007-04-02
Actually, it wasn't a driver problem on my HP. After installing kernel restricted modules wireless just worked, so I suggest trying it before the 10 pages option. You can verify that the driver is loaded by typing in the terminal > sudo lshw -C network
here is the output of mine > $ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:c8:d2:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Blue"]driver=ipw3945[/COLOR] driverversion=1.1.0mp firmware=13.0 1:0 () ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:52000000-52000fff irq:185

If you have wired connection, make sure Universe and Multiverse are enabled in System>Administration>Software Sources, then open the terminal and type
> sudo aptitude install linux-restricted-modules
If there is no wired connection, look [here ](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all)for your kernel version, download and install it.

---

### Post by Average_Joe on 2007-04-03
Here is the output of my command sudo lshw -C network:

$ sudo lshw -C network
Password:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:b0200000-b0200fff irq:169

I also loaded the restricted modules per the second command you mentioned, and I already had all repositories available to me, but this didn't seem to change anything in Networking Options.  Wireless adapter still doesn't show up.  Any other ideas?

---

### Post by seshomaru samma on 2007-04-03
I know this is not much help - but why do you want to upgrade anyway?
If dapper works ,why do you need edgy?

---

### Post by mikewhatever on 2007-04-03
What's the kernel you use? Can you post the output of the following two:
> uname -r
dpkg -la | grep linux-restricted-modules

---

