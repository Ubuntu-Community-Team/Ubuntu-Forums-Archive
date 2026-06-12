---
title: "No wifi adapter when installed on Macbook Pro"
date: 2018-04-28
forum: Apple Hardware Users
---

### Post by redlinesprint on 2018-04-28
Hey all. Not sure if this is the correct place to put this but I just installed Ubuntu 17 on a spare partition of my SSD. Install went fine. Went with only 1 partition, no swap, just ext4. Everything seemed to go smoothly but as the title says I have no wifi adapter available. How do I go about getting ubuntu to see the onboard wifi adapter. Thanks in advanced!

system specs:
2011 macbook pro
macOS High Sierra
Ubuntu 17
16gb RAM
400gb mac
100gb ubuntu

---

### Post by jeremy31 on 2018-04-28
*Thread moved to **Apple Hardware Users**.*
Post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

### Post by redlinesprint on 2018-04-28
mike@Ubuntu-Mac:~$ lspci -nnk | grep -ia3 net


00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller 
[8086:1c22] (rev 05)
	
	Subsystem: Intel Corporation Server Board S1200BTS / Apple MacBook Pro 8,1/8,2 
[8086:7270]
	
	Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM57765 Gigabit Ethernet PCIe 
[14e4:16b4] (rev 10)
	
	Subsystem: Broadcom Limited NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
	
	Kernel driver in use: tg3
	
	Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Limited BCM57765/57785 SDXC/MMC Card Reader 
[14e4:16bc] (rev 10)
	
	Subsystem: Broadcom Limited BCM57765/57785 SDXC/MMC Card Reader [14e4:0000]
	
	Kernel driver in use: sdhci-pci
	
	Kernel modules: sdhci_pci
03:00.0 Network controller 
[0280]: Broadcom Limited BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
	
	Subsystem: Apple Inc. AirPort Extreme [106b:00d6]
	
	Kernel driver in use: bcma-pci-bridge
	
	Kernel modules: bcma

---

### Post by redlinesprint on 2018-04-28
That took far longer than it should have. i also have the problem of not being able to install gparted on the mbp because of no internet and it took over an hour to salvage the flash drive as it was used to install ubuntu in the first place.
Also thank you for moving the thread to the correct location for me.

---

### Post by soniamaria221 on 2018-05-28
you need to get restart again

---

### Post by redlinesprint on 2018-06-01
I have tried restarting. I can try again but it doesn't seem to do anything.

---

### Post by redlinesprint on 2018-06-01
Are there any files or terminal commands that I can use to help get things going? It would be nice to be able to use the internet when in the ubuntu environment and keep the system up to date.

---

### Post by robertarnold659 on 2018-06-10
your 2011 MacBook Pro should have an ethernet connection on it. If it does, connect to the internet that way, then go to your applications menu and click the Software & Updates app. Go to the additional drivers tab and install them.

---

