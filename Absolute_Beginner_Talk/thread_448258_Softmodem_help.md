---
title: "Softmodem help"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by thornumbers on 2007-05-18
I'm new to *nix and for now I'm stuck with dial up.  I am attempting to get my modem working with fiesty, and I'm having some problems.  I've used scanModem and I still need some help.

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_May_11


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1e.3	8086:266d	1179:0001	Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 18:        682   IO-APIC-fasteoi   ohci1394, eth0

 --- Bootup diagnositcs for card in PCI slot 00:1e.3 ----
[   13.141590] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   13.141599] ACPI: PCI interrupt for device 0000:00:1e.3 disabled

 The PCI slot 00:1e.3 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  00:1e.3
   Class 0703: 8086:266d Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW
      Primary PCI_id  8086:266d
    Subsystem PCI_id  1179:0001 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: SIL27, an AgereSystems type.
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-04: Intel ICH - IEC958 : Intel ICH6 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel ICH6 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH6 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH6 - MIC ADC : capture 1
00-00: Intel ICH : Intel ICH6 : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
 0 snd_intel8x0
and from the command:
	aplay -l | grep -i modem


----------------end Softmodem section --------------

Writing Intel.txt
The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-04 21:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1 eth0:avah
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------





Now I'm still not entirely sure what chipset it is so anyone who knows what they are doing, your input would be greatly appreciated.

---

### Post by AAM on 2007-05-19
I can't see your chipset either. Cruise over to Linuxant.com and see if they can help. You can down load their driver for free to see if they work, and if they do and you want more than 5kb/s you can get the unencumbered driver for about $20.

I have used them before, once you pay the single fee, you can download the driver as often as needed for kernel uploads. The driver uses the MAC to password protect so while you have the same MAC you're covered for ages.

---

