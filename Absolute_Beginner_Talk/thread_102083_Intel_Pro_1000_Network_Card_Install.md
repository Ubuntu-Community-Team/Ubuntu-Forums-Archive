---
title: "Intel Pro 1000 Network Card Install"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by jbellny on 2005-12-11
First off - I SO want to leave Windows XP. It's just that I'm having a devil of a time understanding how one installs a driver for a given piece of hardware. From what I can tell it involves magic powder, a volcanoe and the sacraficing of a virgin...but I digress...

During install my Intel Pro/1000 ethernet card wasn't indentified. Thus, I need to install the driver (i'm assuming) for it to work. This is where I'm running into issues. I've read the included install steps (untar, make install) but I get a ton of errors during the process.

Can someone, really simply, just list the steps/prerequisites for getting this driver installed? All of my other hardware seems to have been installed perfectly, but without a network card I'm going nuts!

Thanks very much in advance!:p

---

### Post by Lambert on 2005-12-11
Let's take a quick step to double check because most ethernet nics are supported in linux and I show the e1000 driver in breezy.

run this command

sudo lshw -C network

You should see your nic in the output with a line like this.

configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-

If not then there is a driver problem.

There's a good link in networking on ethernet troubleshooting that might help you.

---

### Post by j2fraser on 2006-01-15
Hi,

I have the same problem. Kubuntu did not recognize my Intel e1000 Gigabit NIC at startup (asked me if I was running Firewire Ethernet!). I have no recognized NIC and, therefore, no access to Internet via Kubuntu.

I had read at [http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/](http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/) (which is the system I am using) that the e1000 driver in Breezy was badly dated. I downloaded the Intel source code from [http://downloadfinder.intel.com/scripts-df/support_intel.asp](http://downloadfinder.intel.com/scripts-df/support_intel.asp) and attempted to create and install the driver -- BONG!

I had run 'apt-get install build essential', changed into the 'src' directory and ran 'make install' and got a bunch of syntax errors ending with the following...
[INDENT]
make[2]: *** [/home/j2fraser/e1000-6.3.9/src/e1000_main.o] Error 1
make[1]: *** [_module_/home/j2fraser/e1000-6.3.9/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
make: *** [default] Error 2[/INDENT]

BTW, I did run 'sudo lshw -C network' command and here is the output I got:

[INDENT]  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:ef7e0000-ef7fffff iomemory:ef800000-efbfffff ioport:cce0-ccff irq:10[/INDENT]

Help! As I'm sure many people will be able to see, I have just enough knowledge to get myself into real trouble -- but I can't begin to fix my ATI display driver until I can get access to my network!

Any help / suggestions would be greatly appreciated.

Thanks,
Jeremy Fraser

---

### Post by p47 on 2006-03-21
Hi j2fraser

I have the same problem with the e1000 dirver, can you help me ?

---

### Post by dvarsam on 2006-03-21
Hello !!!

How come your Untel 1000 Network does NOT work?

What Motherboards do you have guys?

Cause I have an INTEL PERL with 865 chipset & works fine!

---

### Post by dvarsam on 2006-04-01
[QUOTE=dvarsam]Hello !!!
How come your Intel 1000 Network does NOT work?
What Motherboards do you have guys?
Cause I have an INTEL PERL with 865 chipset & works fine![/QUOTE]


OH MY GOD!!!

I just bought an ASUS Motherboard (P5LD2-VM) & just saw your Posts.

I have the SAME Problem:

I performed an lshw -C Network & this is what I get:

> 
root@ubuntu:/home/elena/Desktop# lshw -C Network
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:cffe0000-cfffffff ioport:d800-d81f irq:5


As I said in my previous post, my other Mobo (Intel) has NO problem...
Strange...

Look also at (this Forum's) my Article#: 153441

Did you experience what I experienced, also from the Install?

What Motherboards did you purchase?

I Bet they were ASUS... weren't they?

Thanks.

P.S.> The other PC that I have works fine with my Router & the Router is setup fine! If we all work together, we will solve this...

---

### Post by dvarsam on 2006-04-01
At the same time, if I perform an "ifconfig -a", this is what I get:

> root@ubuntu:/home/elena/Desktop# ifconfig -a

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5917054 (5.6 MiB)  TX bytes:5917054 (5.6 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Any ideas?

Thanks.

---

### Post by dvarsam on 2006-04-01
I installed: > ndiswrapper-utils

Then copied ALL ".inf" & ".sys" Windows files to my Desktop.

I then tried to install the first ".inf" file on "ndiswrapper".

I then tested to see if it installed successfully:

It said: > driver present

What about "hardware present"?

Shouldn't it say something about the "Hardware" being present too?

I then performed a: > sudo modprobe ndiswrapper

AND then tried to access the Internet...

Unfortunately, I could NOT...:( 

NOTHING changed!

I even RESET the Router, but that did NOT get me anywhere either...

_Question_:
What do I do about the "hardware present" NOT showing?

Besides, My Gigabit Wired LAN is "Onboard" my Motherboard...

It is NOT on a separate PCI card...

Thanks.

---

### Post by dvarsam on 2006-04-03
Anybody?

Nobody knows?

---

