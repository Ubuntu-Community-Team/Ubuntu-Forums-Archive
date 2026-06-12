---
title: "support for internal modems on Toshiba laptop?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by imfaisal on 2006-10-04
Hi! Have installed Kubuntu on my TOSHIBA Satellite A105. It has got an internal modem (Windows shows this as INTEL_AZL.Modem) on COM3. But I am having difficulty dialing up - how do I know that the modem is detected and supported?

Thanks!

---

### Post by Sef on 2006-10-04
Have you checked out [linmodems.org]("http://linmodems.org/")?

---

### Post by imfaisal on 2006-10-04
Downloaded and ran scanModem. The content of ModemData.txt is below. 

Based on what I could understand, I then downloaded and unzipped SLMODEMD.gcc4.tar.gz. Now I have a bunch of files and not sure where to go from here...

-------------------ModemData.txt-----------------------
 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.06.1 LTS  kernel 2.6.15-26-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2006_September_29


USB modem not detected by lsusb

 Modem or host audio card candidates have firmware information:
 PCI ID     Subsystem  Name
 ---------- ---------  -----------------
 1002:437b  1179:ff10  0403: ATI Technologies Inc: Unknown device 437b 
 Checking interrupt assignment and sharing:
201:       6607   IO-APIC-level  HDA Intel

 For candidate modem in PCI bus:  0000:00:14.2
   Class 0403: 1002:437b 0403: ATI Technologies Inc: Unknown device 437b
      Primary PCI_id  1002:437b
    Subsystem PCI_id  1179:ff10 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 
      

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-hda-intel and audio drivers it depends on,
 displayed by:	lsmod | grep snd_hda_intel
Module                  Size  Used by
-------------------------------------
snd_hda_intel          18964  1 
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-00: ALC861 Analog : ALC861 Analog : playback 1 : capture 2
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]

----------------end Softmodem section --------------
Writing Smartlink.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 The kernel was compiled with gcc version 4.0.3 and a compiler is not installed


If compiling a modem driver proves to be necessary, one of the two procedures must be followed.
If not yet on the Internet, put the Dapper install CD in the drive
Open a terminal and therein:
$ sudo apt-get install  gcc-4.0  make
Additionally the package linux-headers-2.6.15-26-386 must be downloaded.  
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  and search for linux-headers-2.6.15-26-386 
After downloading, it can be installed with:
$ sudo dpkg -i linux-header*.deb

Or alternatively if online through Ethernet do:
$ sudo apt-get update
$ sudo apt-get install build-essential
will do all the necessary installations mentioned above.

In either installation case, set a symbolic link which will be expected later:
$ sudo ln -s /usr/bin/gcc-4.0  /usr/bin/gcc
After check with:
$ ls -l /usr/bin/gcc*
which should display:
lrwxrwxrwx 1 root root    16 2006-07-09 21:53 /usr/bin/gcc -> /usr/bin/gcc-4.0
-rwxr-xr-x 1 root root 93584 2006-04-20 18:22 /usr/bin/gcc-4.0
-rwxr-xr-x 1 root root 16245 2006-04-20 18:13 /usr/bin/gccbug-4.0

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	gcc-4.0 make linux-headers-2.6.15-26-386


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 19:00 /usr/sbin/pppd

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

Read Modem/YourSystem.txt concerning other COMM channels: ath0 eth0
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

### Post by imfaisal on 2006-10-05
it has been a while since I posted this message for help. Should I assume that no help is forth coming? I think I am half way through and just a hint would help me set up kubuntu on my laptop with full satisfaction...](*,)

---

### Post by stephenc on 2006-10-12
*bump*

I just bought an A105-S4334 and completed my first install last night. Will try to use modem tonight.

---

### Post by dmizer on 2006-10-12
> **imfaisal said:**
> it has been a while since I posted this message for help. Should I assume that no help is forth coming?

you said you unpacked SLMODEMD.gcc4.tar.gz and have a bunch of files.  in the "bunch of files" is a readme file.  read it, and it will tell you how to make it work.  if you run into problems, post back.

if you have trouble understanding the readme file, post it and let us know where you have trouble and we can offer guidance.

---

