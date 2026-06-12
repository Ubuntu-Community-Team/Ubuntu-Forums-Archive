---
title: "Installing USB external modem in Ubuntu"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by EzEe on 2007-04-20
Hi,
  I have recently started using ubuntu. I have seen my modem in device manager detected as 56k US robotics USB modem. But i can't seem to find any drivers to make it work. Due to this i am unable to download any apps automatically. Please tell me how can i install my usb external modem.

---

### Post by Bachstelze on 2007-04-20
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

run the scanModem tool and put your modemData.txt here.

---

### Post by trishacupra on 2007-04-20
It may not be able to work at all - mine wasn't.

Check out this article, and then check the website of the manufacturer of your modem.

[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by Bachstelze on 2007-04-20
It is a 56k modem, not ADSL...

---

### Post by EzEe on 2007-04-21
here is "modemdata" file. Can ou figure out. Because I am unable to understand anything from it.

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-11-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Mar 13 23:32:38 UTC 2007 (Ubuntu 2.6.17-11.37-generic)
 scanModem update of:  2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	1043:818f	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
169:       4087          0   IO-APIC-level  uhci_hcd:usb5, HDA Intel

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[17179585.016000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179585.016000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

ALSAversion 1.0.11
The audio card is not a modem hosting type.

 	A modem was not detected among the PCI devices:
------------------------------------------------
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 PCIe] (rev a2)
------------------------------------------------
 with USB and bridge devices not displayed.
 Please provide any independent information available on your modem.

	If your modem is mounted on an ISA card, scanModem could not access it.
	If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.

 Checking for audio+modem support in /proc/asound/pcm
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1

 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:2668 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW
      Primary PCI_id  8086:2668
    Subsystem PCI_id  1043:818f 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.1.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
2) The hsfmodem software for Conexant chipset modems: Read Conexant.txt

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.1.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.1.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-intel8x0m and audio drivers it depends on,
 displayed by:	lsmod | grep snd_intel8x0m
Module                  Size  Used by
-------------------------------------
snd_intel8x0m          18956  0 
snd_ac97_codec         97696  1 snd_intel8x0m
snd_pcm                84612  5 snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    58372  14 snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  3 snd_intel8x0m,snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem


----------------end Softmodem section --------------

scanModem could not identify the Support Type needed from diagnosics or archives.
	If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.


Writing Intel.txt

 Formal support for Conexant chipset modems are available ONLY through 
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers).  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 [http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B](http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B) reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 Read Conexant.txt

Writing Conexant.txt

Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.17-11-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-11 00:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
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

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by EzEe on 2007-04-26
hay guys come on . Please I desperately need help with it. 

   Atleast tell me a site from where I can get help.

---

