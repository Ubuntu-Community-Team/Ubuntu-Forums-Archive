---
title: "Help installing a Driver"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by housam on 2006-12-02
G'day every one,
After runing the scan modem tool I've got the following data.txt file :

> --------------------------  System information ----------------------------
 Ubuntu 6.06 LTS 
Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:00:1b.0	8086:27d8	103c:30a2	0403: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
169:       2347   IO-APIC-level  HDA Intel, eth0, i915@pci:0000:00:02.0

 --- Bootup diagnositcs for card in PCI slot 0000:00:1b.0 ----
[4294688.367000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294688.367000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:27d8 is a High Definition Audio card, possibly hosting a soft modem.

 For candidate modem in PCI bus:  0000:00:1b.0
   Class 0403: 8086:27d8 0403: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
    Subsystem PCI_id  103c:30a2 
    Softmodem codec or Vendor from diagnostics: 11c1, an AgereSystems type.
                              from    Archives: 11c1, an AgereSystems type.
      

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
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
0 snd_hda_intel
	/proc/asound/card0/codec#1
-------------------------------
Codec: Generic 11c1 Si3054
Address: 1
Vendor Id: 0x11c13026
Subsystem Id: 0x103c30a2
Revision Id: 0x100700
-------------------------------
Current support status of HDA cards is:
  Vendor IDs  Chip maker     Support type 
  ----------  ----------    -------------
  0x14f12bfa  Conexant      hsfmodem , not slmodemd compatible
  0x11c13026  AgereSystems  snd-hda-intel, slmodemd supported
  0x11c11040  AgereSystems      "             "    , patch needed
  0x11c13055  AgereSystems      "             "    ,      "
  0x163c3055  Smartlink         "             "    ,      "
  0x163c3155    "               "             "    ,      "
  0x10573055  Motorola          "             "    ,      "
  0x10573155     "              "             "    ,      ""
as of October 2006.

and from the command:
	aplay -l | grep -i modem
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 The kernel was compiled with gcc version 4.0.3 and a compiler is not installed


If compiling a modem driver proves to be necessary, one of the two procedures must be followed.
If not yet on the Internet, put the Dapper install CD in the drive
Open a terminal and therein:
$ sudo apt-get install  gcc-4.0  make
Additionally the package linux-headers-2.6.15-23-386 must be downloaded.  
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  and search for linux-headers-2.6.15-23-386 
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
	gcc-4.0 make linux-headers-2.6.15-23-386


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-02-23 18:33 /usr/sbin/pppd

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
I've already downloaded the driver **SLMODEMD.gcc4.tar.gz**   and tried to install it but failed.

Can any one help doing the installation.
Thanks

---

### Post by Sef on 2006-12-02
First did you read [linmodems]("http://linmodems.org/")?

---

### Post by housam on 2006-12-03
Yes, I've read it. but found nothing more than what I've done.
I've downloaded the scan modem tool and after running it got the posted results.
I'm not expert in writing code and there are many things I don't understand or how to be done. That's why I need step by step installation guide for this modem driver.

---

### Post by Sef on 2006-12-03
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by housam on 2006-12-03
Thank you for the link.
after careful reading of the file modem data.txt,I'm in the half way installing the Driver of my modem.

---

### Post by Sef on 2006-12-03
You're welcome.  If you have any other questions about it, please post it here.  If you have questions on a different subject, please start a new thread.

---

### Post by housam on 2006-12-04
Thank you Sef , I've tried to solve this problem yesterday but failed. here what I,ve done > housam@housam-laptop:~$ cd ~/Desktop
housam@housam-laptop:~/Desktop$ cd SLMODEMD.gcc4
[email]housam@housam-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ sudo - root
sudo: '-' requires an argument
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
[email]housam@housam-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ sudo chmod a+x slmodemd
Password:
[email]housam@housam-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ sudo cp slmodemd /usr/bin/
[email]housam@housam-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ sudo modprobe snd-intel8x0m
[email]housam@housam-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ sudo slmodemd -c EGYPT --alsa hw:0,6
SmartLink Soft Modem: version 2.9.11 Mar 13 2006 18:27:33
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.


and in another terminal I configured wvdial and got the following:> housam@housam-laptop:~$ sudo wvdialconf /etc/wvdial.conf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31
Modem Port Scan<*1>: S32  S33  S34  S35  S36  S37  S38  S39
Modem Port Scan<*1>: S40  S41  S42  S43  S44  S45  S46  S47
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
housam@housam-laptop:~$


and till now I can't connect to the web.

Do I missed something or should I do something else.

---

### Post by housam on 2006-12-05
Would any body had the same problem help?

---

### Post by _duncan_ on 2006-12-05
try this:

1. open a terminal and type:
```
sudo cp /etc/wvdial.conf /etc/wvdial.conf_orig
sudo gedit /etc/wvdial.conf
```

2. make sure it contains the following lines:
```
Carrier Check = off
Stupid Mode = on
```

3. save and exit.

4. try dialing out again by typing this in the terminal:
```
sudo wvdial
```

---

### Post by housam on 2006-12-05
After code > sudo cp /etc/wvdial.conf /etc/wvdial.conf_orig
sudo gedit /etc/wvdial.conf
and adding > [QUOTE]Carrier Check = off
Stupid Mode = on[/QUOTE]
I got the following:> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = 07770777
New PPPD = yes
Modem = /dev/ttySL0
Username = housam
Password = ****
Baud = 460800
Carrier Check = off
Stupid Mode = on

and when"> sudo wvdial

I got the following:> housam@housam-laptop:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.55
--> Cannot open /dev/ttySL0: No such file or directory
--> Cannot open /dev/ttySL0: No such file or directory
--> Cannot open /dev/ttySL0: No such file or directory
housam@housam-laptop:~$

and still no connection to the web.

---

### Post by housam on 2006-12-05
I,m a little confused, 
Do I've to use system >> admin. >> networking >> modem connection >> activate while using terminal >> sudo wvdial ? or these are two different programs ?

---

### Post by _duncan_ on 2006-12-05
Just saw your 2nd to the last post. The /etc/wvdial.conf file looks OK to me.

From the error message, seems like the modem driver itself wasn't properly installed. Can't help you with that coz I have a different modem and have a different way of installing the driver.

---

### Post by housam on 2006-12-06
Thank you anyway _duncan_ , I'll start the whole process from the begining to ensure the proper installation of the driver.

---

### Post by _duncan_ on 2006-12-06
Good luck! Just in case you find yourself still stuck there are a few things you may want to try out:

1. Email linmodems.org with an attached ModemData.txt file.
2. Consider changing your current software modem with:

- another software modem. I personally have great success with smartlink for the past 3 Ubuntu versions (breezy 5.10, dapper 6.06 and now edgy 6.10). Search around this forum using the keyword 'dial-up' so you'll have an idea which models work well in Ubuntu. It's pretty cheap too, I got mine for less than 5 US dollars. Conexant used to work well but I understand it doesn't work for edgy 6.10.

- hardware modem. Most of them don't even need drivers to operate. I have an old 3Com/US Robotics fax modem as a back-up. I like trying out various linux distros. Whenever I find myself unable to compile the smartlink modem driver for a particular distro, I whip out this old hardware modem, configure the system to use it, and usually get on-line in a few minutes. They are more expensive than software modems though.

Just don't give up and you will eventually get on-line. It took me 3 months to get on-line when I first started out with linux.

---

### Post by housam on 2006-12-06
I had a similar case with my Desktop pc software modem two months ago and I solved it with the help of the forum community and get on-line . Now I'm facing it again for my new laptop but with a different software modem which is compleceted than the other one. 
I won't give up but if it is unsolved matter, I'll go for a DSL because I'm not sure about finding a proper hardware modem here in Egypt, and also I've read that some of them won't work with laptops.

---

