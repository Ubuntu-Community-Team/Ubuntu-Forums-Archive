---
title: "Hod can I see a full specification of my system?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-04
I need the version of my motherboard, but I don't know where to look at it!

---

### Post by liamwithers on 2007-10-04
Not sure if this will help or not because I'm not using Gnome and wouldn't know where to find it.

Is it in, System - Administration - Device Manager? (something like that maybe?)

---

### Post by llamakc on 2007-10-04
Pay attention and write down what is posted when you are booting up. It'll be when BIOS is posting.

---

### Post by rfruth on 2007-10-04
lshw [http://www.rfruth.net/resume/computers/linux/ubuntu/lshw-rf.html]("http://www.rfruth.net/resume/computers/linux/ubuntu/lshw-rf.html")

---

### Post by rsambuca on 2007-10-04
You won't be able to tell the version of your motherboard from within ubuntu.  You can guess at it if you know the brand, and then find out what the chipsets are, but to be positive you need to look inside.  

If it is a big brand machine, then we may be able to tell by the model number on the outside.

---

### Post by llamakc on 2007-10-04
It should be noted that you don't get the mobo info unless lshw is ran as root or with "sudo -i".

 sudo -i
root@llamakc:~# lswh
-bash: lswh: command not found
root@llamakc:~# lshw
llamakc                   
    description: Desktop Computer
    product: MS-7135
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop


So yes, you can determine the mobo possibly from within Ubuntu.

---

### Post by rsambuca on 2007-10-04
> **llamakc said:**
> It should be noted that you don't get the mobo info unless lshw is ran as root or with "sudo -i".

 sudo -i
root@llamakc:~# lswh
-bash: lswh: command not found
root@llamakc:~# lshw
llamakc                   
    description: Desktop Computer
    product: MS-7135
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop


So yes, you can determine the mobo possibly from within Ubuntu.

Sweet.  I stand corrected!

---

### Post by llamakc on 2007-10-04
I didn't think it was possible either (see my earlier advice). Linux is awesome.

---

### Post by rsambuca on 2007-10-04
Do you happen to know why it shows the Motherboard info for root and not a regular user?

---

### Post by llamakc on 2007-10-04
No I don't. I guess one would have to look at the code for lshw to see why/where that happens.

---

### Post by rfruth on 2007-10-04
```
man lshw
```  reports lshw must be run as super user or it will only report partial  information.

---

