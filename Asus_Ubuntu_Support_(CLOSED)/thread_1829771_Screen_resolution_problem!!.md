---
title: "Screen resolution problem!!"
date: 2011-08-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by spyter0 on 2011-08-20
Hi 
I had asus eee pc 1101ha
i am new in linux and a few days ago i install ubuntu 11.04.
when i try to change my screen's resolution i had only 2 choses  800x600 and 1024x768. [ATTACH]200484[/ATTACH]
my monitor proper resolution is **1366 x 768**.
How can i add [B]1366 x 768 resolution:confused:

my [/B]lspci  if it helps is 


```
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
```Thanks

---

### Post by spyter0 on 2011-08-25
after weeks of searching i find the solution for my problem :

i just run these commands in the terminal 

```
sudo add-apt-repository ppa:gma500/emgd 
``````
sudo apt-get update
``````
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
``````

sudo emgd-xorg-conf
```then reboot to changes take effect.


Here is where i find these informations.

for asus 1101HA ---- [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Drivers_installation](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Drivers_installation)

if anyone had similar problem check this link may help ---- [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by umerlone on 2011-08-25
Hi, 
Good Job!!
I have a similar problem with a Lenovo x220,
Do you have any idea about where I could look for a solution.
Thanks a lot
Ugo

---

### Post by umerlone on 2011-09-01
Actually my problem was solved in the thread 

Ubuntu 10.04 on Lenovo Thinkpad i5 X220

Ugo

---

### Post by idjut on 2011-10-03
Well done on that! I tried to do the same, but encountered some problems: 

> $ sudo emgd-xorg-conf
Traceback (most recent call last):
  File "/bin/emgd-xorg-conf", line 309, in <module>
    if checkDMI(device) != False:
  File "/bin/emgd-xorg-conf", line 292, in checkDMI
    dmi = os.popen("dmesg | grep DMI").read().split("\n")[1].split(":")[1][1:].split(",")[0] # Getting the dmi from dmesg
IndexError: list index out of range

Any ideas?

---

### Post by spyter0 on 2011-11-12
hmm, i am not sure!
let me know what computer you have.

---

### Post by hwertz on 2011-11-15
To run emgd-xorg-conf on my Mini 12, I had to change line 126 (the first line to mention dell_1210), and add one space to the part that says
```
Dell Inc. Inspiron 1210   /0X605H
```.  There are 3 spaces between "1210" and "/0X605H" and I needed 4.  My *full* DMI line in dmesg is
```
Dell Inc. Inspiron 1210   /0X605H, BIOS A02 12/01/2008
``` so I wonder if the spacing varies by BIOS update?

---

### Post by ChrisBakesCake on 2013-01-09
Try this in terminal.

sudo gedit /bin/emgd-xorg-conf

on line 309 where it says "if checkDMI(device) != False:"
change "False" to True.

Save the file run sudo emgd-xorg-conf in terminal and reboot.

cross yo' damn fingers.

---

