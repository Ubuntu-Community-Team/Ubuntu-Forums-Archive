---
title: "Setting up a Dialup Internet Connection"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2006-08-30
I am new to Linux/Obuntu and I have a few question re Setting up a Internet connection using a dialup service with a Win Lucent modem. 
Q1. Do I need to have the Ethernet Enabled in the BIOS (not required in my Windows setup), if so how do I configure the DHCP/Stactic IP and the DNS IP address.
My first attempt the modem appeared to connect (normal dialup modem noises) but I received the following Pop-Up Message in Evolution Mail Evolution Error (& similar message in Mozilla Firefox).
"Error While Fetching Mail"
Host LooKup failed: mail.bigpond.com
Temporary failure in name resolution.

If I need to download any updates/drivers can I download via Windows XP then copy them to the correct area somewhere in Sdb1???
Any help would be appreciated.

Old Kevin

---

### Post by CameronCalver on 2006-08-30
try this [http://www.ubuntuforums.org/showthread.php?t=245610](http://www.ubuntuforums.org/showthread.php?t=245610) and let me no if you succeed

---

### Post by catanzag on 2006-08-30
Did you check [this]("https://help.ubuntu.com/community/DialupModemHowto") help page for modem dialup configuration?

As in Windows, no Ethernet is needed, and the IP is (generally) dynamic

EDIT: of course, you can download whatever you want in Windows and then use it in Ubuntu via usbpen

---

### Post by CameronCalver on 2006-08-30
yes that thread i gave you is basicly lames vesion of that wiki

---

### Post by hanzj on 2006-08-30
I did take a look at the [help page on setting up the dialup modem]("https://help.ubuntu.com/community/DialupModemHowto"),  but I am stuck.I've reached [the stage where I've done scanModem ]("https://help.ubuntu.com/community/DialupModemHowto#head-66d0d948c2a02d4046c1c4eb4db7ac500a8289b5").

This is what hte ModemData.txt says about my modem:

> --------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
 scanModem update of:  2006_August_28



=======================================================
 For candidate modem in PCI bus 0000:00:0b.0, System summary: 
                    -----PCI_IDs-------                    --CompilerVer- 
    Feature List:   Primary  Subsystem Distr  KernelVer   kernel default CPU
   ./scanModem test 127a:1005 127a:1005 Ubuntu 2.6.15-26-386 4.0.3 none i686 
 ------------------------------
 The modem hardware is:
   Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp 
      Primary PCI_id  127a:1005
 Support type needed or chipset:	HCF
 


 Formal support for Conexant chipset modems are available ONLY through 
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers).  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types, hsfmodem  and hcflinmodem.

 The modem requires a hcflinmodem package.
Writing Conexant.txt
 The Major.Minor versions differ for the 
	the compiler used in kernel assembly:  4.0
	and the designated compiler:           none
 But there must be a match on the target for driver installation, 
 of gcc Major.Minor versions or kernel and drivers!!
 Otherwise the drivers will fail to load with warning:
	Invalid module format!!"
	See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 


So this says that my modem is "HCF" type. But the help page doesn't talk about hcf types.

Please advise, anybody.

---

