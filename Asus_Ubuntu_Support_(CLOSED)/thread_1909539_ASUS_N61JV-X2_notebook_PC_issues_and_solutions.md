---
title: "ASUS N61JV-X2 notebook PC issues and solutions"
date: 2012-01-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Welly Wu on 2012-01-15
I have an ASUS N61JV-X2 notebook PC which I purchased from Amazon in late August 2010. I upgraded the RAM to Crucial 8 gigabytes of DDR3 PC-8500 1,066 MHz SODIMM SDRAM. I also replaced the Seagate Momentus 7200.4 hard drive with an Intel 2nd Generation X25-M MLC NAND FLASH 160 gigabyte Solid State Drive. I installed Ubuntu 10.04.3 64 bit LTS as my primary operating system.

I have an ASUS USB-BT211 Bluetooth 2.1 + EDR USB dongle. It does not work in Ubuntu 10.04.3 64 bit LTS. I did some searches and it seems that my Linux kernel needs to be upgraded to the latest version which is 3.x in order to get out of the box hardware compatibility. In other words, I will have to wait until Canonical releases Ubuntu 12.04 64 bit LTS to get this problem fixed. I have an ASUS Laser Bluetooth Mouse and an Etymotic Research EtyBlu2 Bluetooth headset that I can not use right now.

I also have Super Speed USB 3 and a Nvidia GeForce GT 325M GPU with Nvidia Optimus technology. I know that Nvidia does not plan to support GNU/Linux officially. There are the Bumblebee and Ironhide projects that offer limited support. I did install Ubuntu 11.10 64 bit and I tried out Bumblebee and Ironhide separately, but they both failed to work properly because the X servers did not start for some unknown reason. Bumblebee and Ironhide have been tested to work with Ubuntu 11.04 which is one year ahead of 10.04.3 64 bit LTS. Is it safe for me to try out either Bumblebee or Ironhide now or should I wait to upgrade to Ubuntu 12.04 64 bit LTS and try them out later? It is also my understanding the Super Speed USB 3 hardware compatibility will be right out of the box with the latest Linux 3.x kernel so my Patriot Memory Supersonic Magnum 128 gigabyte USB 3 thumb drive will be supported at full sequential read and write speeds of 220 MB/s and 120 MB/s respectively with Ubuntu 12.04 64 bit LTS. Am I correct in my thinking? Does anyone own a hardware device such as an external hard disk drive, solid state drive, or USB 3 thumb drive and tested its hardware compatibility and performance with a computer that supports Super Speed USB 3 with any version of Ubuntu 64 bit beyond 10.04.3 LTS? What were your results if applicable?

Finally, I want to know just how many other Ubuntu users own an ASUS N61JV-X2 notebook PC within this community. Please reply with your lessons learned and valuable experiences as they relate to debugging and troubleshooting problems.

Thank you.

---

### Post by Welly Wu on 2012-01-26
Ubuntu 11.10 64 bit works with my ASUS N61JV-X2 notebook PC right out of the box. Just add the Bumblebee project and everything will work right out of the box with all hardware devices and software packages. Looking forward to future Ubuntu 64 bit releases including Nvidia device driver support if they reverse their decision and they decide to support GNU/Linux environments with Optimus technology.

---

