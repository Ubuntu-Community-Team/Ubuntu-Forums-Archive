---
title: "Help in installing the modem"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by I_have_seen_the_light on 2007-11-05
I recently installed Ubuntu on a Laptop.  everything works well except for the modem.  It has been two weeks now that I have been trying to get the built in modem to work.  I have done the modem scan already and this is what I got from the modemdata. txt

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.20-15-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
 Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  20071019


 There are no blacklisted modem drivers in /etc/modprobe*  files 

Advanced Linux Sound Architecture  (ALSA) spackage providing audio support 
on your System, also includes drivers for some modems. For modems using the 
snd-hda-intel  audio+modem driver, upgrades to a new ALSA version are sometimes 
necessary to achieve function. See for example:
      [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02144.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02144.html)
Copying ALSA diagnostics to Modem/ALSAroot.tgz
ALSAversion = 1.0.13

USB modem not detected by lsusb

Modem or candidate host audio card have firmware information and diagnostics:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	1558:5405	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 21:       2831          0   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   23.224000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   23.224000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

  The High Defintion Audio card with PCI ID 8086:27d8 may host a soft modem chip.
Bootup diagnostics lack ALSA data.

 Modem not detected though HDA card diagnostics, though not excluding
 a possible Conexant modem chip impervious to ALSA diagnostics. 
 Proceeding through alternative possibilties.


There is candidate modem software.

 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
    Subsystem PCI_id  1558:5405 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 10573055_Motorola_Si3054
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.1.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.1.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-hda-intel and audio drivers it depends on,
 displayed by:	lsmod | grep snd_hda_intel
Module                  Size  Used by
-------------------------------------
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-02: ALC883 Analog : ALC883 Analog : capture 2
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 2

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.20-15-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 



If a driver compilation files with message including some lack of some FileName.h (stdio.h for example. 
Some additional kernel-header files need installation to /usr/include.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:
$ sudo apt-get -s install linux-kernel-devel
While some of the files may be on the install CD, others may have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)

For Ubuntu Feisty, additional packages required were:
 libc6-dev linux-libc-dev
available through [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , if not on the install CD.
Such packages may have different names for other Linux distributions.
Try installing just the libc6-dev, then test the compile again.


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 11:41 /usr/sbin/pppd

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1
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


I cant make heads or tails out of it and I am now at a loss on what to do next.  help!

Btw, I apologize if I was not able to post the modemdata.txt in a frame so that you could just scroll  over it.  I dont know how to.  sorry.

thanks,

Homer

---

### Post by qamelian on 2007-11-05
It looks like you are still using Dapper. This is much simpler if you are using the current (Gutsy) release. You can install your modem in much the same way as you would install restricted drivers for your wireless card.

---

### Post by I_have_seen_the_light on 2007-11-05
I think I am using 7.04 I dont actually plan to upgrade now because I am stuck in a place wherein I dont have access to broadband.  I am using dial up.  can you guys help me?  Im fairly comfortable using the terminal and I am very much willing to learn how to do this.   I just need some body to explain to me what the ModemData.txt means, and how should I proceed with the installation.  I know   installing Gutsy would be a big help. but I'd like to learn.

thanks

Homer

---

### Post by gator on 2007-11-07
seems like u have a slmodem....
go to System->Administration->synaptic package manager

select and install -> sl-modem-daemon
select and install -> GnomePPP
reboot

setup gnomeppp... click autodetect modem
hope this works...let us know

---

### Post by plucky on 2007-11-07
Homer,

I have recently seen a similar modemdata.txt on a **desktop **machine.It was not actually picking up the PCI modem but was finding the built in modem and sound card on the motherboard.

To fix it I went into the BIOS and turned off the onboard modem and rebooted.

Then I ran scanmodem again and it picked up the PCI modem and I was then able to install the correct driver from linmodems.org.

What are your laptop specs and is the modem onboard or on the PCI bus?

Hope this helps

Peter

---

### Post by I_have_seen_the_light on 2007-11-12
Gator,

thanks for the tip will try that out once I get to a place where I could connect via cable and download the sl modem daemon.

Plucky,

I tried to look for the setting to turn off the on board modem but, unfortunately there is no option for me to turn it off in the PC's setup (bios).  The specs of the laptop,  hmm... its a centrino Duo 1gig ram.  I think you could check it out here.   [www.Neo.com.ph](www.Neo.com.ph).  the sticker says it model M54N



will give it a go and try out Gator's suggestion.  wish me luck.
Btw,  I tried to install Gutsy and it worked fine.  everything works except for  the modem.


Thanks,

Homer

---

