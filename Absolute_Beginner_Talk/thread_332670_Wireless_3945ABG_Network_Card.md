---
title: "Wireless 3945ABG Network Card"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by duncG38 on 2007-01-06
Hi a complete newbie here.  I have a HP Pavilion Laptop with the Intel Pro Wireless 3945ABG Netwrok card inside.

My problem is that it does not show up in the network manager so I can not use it.  I have followed several of the previous posts to no avail.

lshw shows this

*-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@05:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945
                resources: iomemory:d6000000-d6000fff irq:193

The drive is the ipw3945

lsmod shows

hci_usb                18068  2 
ipw3945               124576  0 
bluetooth              53476  7 rfcomm,l2cap,hci_usb


but iwconfig shows this

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Where am I going wrong???

Oh I have the LAN working and read another link that suggested that be set to a static IP so I have done that too.

Regards Duncan

---

### Post by duncG38 on 2007-01-06
Forgot to say I am running Ubuntu V 6.10

Duncan

---

### Post by grndslm on 2007-01-14
Dunno if you figured this out yet or not....

but I recently fixed this issue in Edgy with:

sudo apt-get install linux-restricted-modules-686

or
sudo apt-get install linux-restricted-modules-generic
or 
sudo apt-get install linux-restricted-modules-k7
or
whatever the heck kinda processor ya got!

Then it worked...YAY!!

---

### Post by ekka on 2007-01-14
I have the same wireless card in my Acer laptop and it is working fine. It is listed under eth1 through. What exactly is problem, you cannot access internet?

---

### Post by c188co on 2007-02-08
found the fix the hard way, most of this brothers in the linux love this way, following too much advice requires sometimes reinstall the whole system.

i just went to applications/add remove prgrams, got the program network manager
folowed the promts and reboot.
after rebooting a new icon shows on the top of the screen, shows network detected and the option to connect. 
my network is unsecure so i connect and is working fine

please try and see

c188co

---

