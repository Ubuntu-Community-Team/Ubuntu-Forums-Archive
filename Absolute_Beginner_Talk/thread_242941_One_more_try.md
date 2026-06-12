---
title: "One more try"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by CovekNaFrezi on 2006-08-24
I have decided that after one more try with this linux stuff, if it doesn't find my modem, I'm going back to XP. Say what you want, but OS with internet is better than OS without internet. 

Now, if I may...

ModemHowTO instructs me to:
```
Preliminaries

    *

      These are steps you will only have to run through the first time you build this driver, we're just making sure you have all the installed packages you need. Your will need the following packages installed: **build-essential fakeroot gcc3.4** as well as a linux headers package, **linux-headers-ARCH**, where ARCH is your architecture, which you can find out by running $ uname -r, which should give you something like VERSION-XX-ARCH (where ARCH is your kernel flavor, e.g. 386, 686, 686-smp, k7 or k7-smp if you use Intel, powerpc for PPC ...).

      You also need to install the source of the Smartlink driver itself with the following packages: sl-modem-source sl-modem-daemon.

      You can install all packages listed above at the same time.

```

what the fcuk!? where do I find this "build-essential fakeroot 3.4"? There IS some fakeroot in Synaptic, but it's not as described above...

I need step-by-step instructions because I'm linux-stupid. Thanks. :rolleyes: 

PS:
Sorry, I have been at it a week now and my time is wasted and wasted some more on this modem crap. Pitty Lunux devs know everything but how to make a modem work out of the box. Maybe they know it, but aren't telling...either way it sucks. No linux beginner should go through the stuff I'm going through (and other noobs).

---

### Post by wpshooter on 2006-08-24
Covek:

Is this a dial-up modem ?

---

### Post by CovekNaFrezi on 2006-08-24
Indeed. 
It is visible in Device Manager as "ALi Corporation M5457 AC'97 Modem Controller" and I have already ran the "scanModem" tool, but don't know how to translate the text file that it gives - therefore I have no clue if its a modem supported by SmartLink driver, ALSA or whatever else. 

I have tried the "ALSA" installation approach, but gives me fatal errors. So I moved on to SmartLink - One of them has to work.

---

### Post by CovekNaFrezi on 2006-08-24
Here is the text file from ScanModem tool

```
 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.06.1 LTS  kernel 2.6.15-26-386 
 This will alert cogent experts, and  distinguish cases in the Archives 
 YourCounry is not essential, but will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org
--------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2006_August_22

	Checking for ALSA (Advanced Linux Sound Architecture) 
compatible modem cards with:  aplay -l | grep -i modem
---------------------------



Checking /proc/asound/  folders for modem support.
	/proc/asound/pcm
-------------------------
00-00: ALI 5451 : ALI 5451 : playback 32 : capture 1

               The node for modem setup is:    modem:


=======================================================
 For candidate modem in PCI bus 0000:00:03.0, System summary: 
                    -----PCI_IDs-------                    --CompilerVer- 
    Feature List:   Primary  Subsystem Distr  KernelVer   kernel default CPU
   ./scanModem test 10b9:5457 104d:8158 Ubuntu 2.6.15-26-386 4.0.3 none i686 
 ------------------------------
 Chipset or support type: Smart

 With modem hardware:
   Modem: ALi Corporation M5457 AC'97 Modem Controller
   with Primary PCI_id  10b9:5457
    and a SubSystem_id  104d:8158
   using interrupt (IRQ) 11 , with sharing reported from /proc/interrupts:
         1:       1111          XT-PIC  i8042
 11:       1969          XT-PIC  uhci_hcd:usb1, yenta, ALI 5451, sonypi

There is DISagreement of diagnostics and hardware prediction.
Pausing for 10 seconds.
----------------------
There was a failure to acquire mc97 codec information, suggesting either
a Conexant modem chip, not supported by the ALSA modem driver snd-intel8x0m,
of that snd-intel8x0m may require reloading. Please with Root permission do:
	sudo modprobe -r snd-intel8x0m 
	sudo modprobe snd-intel8x0m  
Then rerun
	./scanModem
If displayed, Ignore his message on the next run.

 Lacking a dsp (digital signal processing) chip, the modem is a software intensive
 or "softmodem" type. Its primary controller manages the traffic with the CPU. But
 the software needed is specified in the Subsystem, not in the primary host controller.

 Information acquired by the scanModem analysis is:

 implying that the modem hardware:
 	Modem: ALi Corporation M5457 AC'97 Modem Controller
 with Subsystem 104d:8158 needs support type: SMART 
  Rather than an ALSA driver, the ALI5457 card requires the Smartlink driver:  slamr

 For more common kernels, some compiled SmartLink drivers are available. 
 The modem should setup with:
    sudo modprobe ungrab-winmodem
    sudo modprobe slamr
    sudo  slmodemd -c YOUR_COUNTRY /dev/slamr0
 Read Smartlink.txt for and Testing.txt  for details.


=======================================================
 For candidate modem in PCI bus 0000:00:04.0, System summary: 
                    -----PCI_IDs-------                    --CompilerVer- 
    Feature List:   Primary  Subsystem Distr  KernelVer   kernel default CPU
   ./scanModem test 10b9:5451 104d:8158 Ubuntu 2.6.15-26-386 4.0.3 none i686 
 ------------------------------
 Chipset or support type: Smart

 With modem hardware:
   Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device 
   with Primary PCI_id  10b9:5451
    and a SubSystem_id  104d:8158
   using interrupt (IRQ) 11 , with sharing reported from /proc/interrupts:
         1:       1111          XT-PIC  i8042
 11:       1969          XT-PIC  uhci_hcd:usb1, yenta, ALI 5451, sonypi

There is DISagreement of diagnostics and hardware prediction.
Pausing for 10 seconds.
----------------------
There was a failure to acquire mc97 codec information, suggesting either
a Conexant modem chip, not supported by the ALSA modem driver snd-ali5451,
of that snd-ali5451 may require reloading. Please with Root permission do:
	sudo modprobe -r snd-ali5451 
	sudo modprobe snd-ali5451  
Then rerun
	./scanModem
If displayed, Ignore his message on the next run.

 The candidate ALSA modem driver on your System is:  snd-ali5451
 Lacking a dsp (digital signal processing) chip, the modem is a software intensive
 or "softmodem" type. Its primary controller manages the traffic with the CPU. But
 the software needed is specified in the Subsystem, not in the primary host controller.

 Information acquired by the scanModem analysis is:

 implying that the modem hardware:
 	Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device 
 with Subsystem 104d:8158 needs support type: Smart 
 

 Driver snd-ali5451 has modem in addition to audio support, for non-Conexant modems.
 An ALSA (Advanced Linux Sound Architecture} modem driver snd-ali5451 
  provides ONLY a low level access to the hardware. The complementing HIGH 
 level support for ALSA  modem drivers is through a Smartlink utility:  slmodemd
 Download from http://linmodems.technion.ac.il/packages/smartlink/ the SLMODEMD.gcc4.tar.gz 
 Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.tar.gz
 and read instructions therein. But briefly, the modem should setup with command:
 >>>	sudo slmodemd -c YOUR_COUNTRY --alsa -s hw:0,1     <<<

 A dialer utility such as wvdial (perferable) is still needed for dialout.
 slmodemd MUST be kept running throughout a dialout session.
 Read Modem/YourModem.txt and Modem/SmartLink.txt for furthere details.

 Already added to the kernel is snd-ali5451 and audio drivers it depends on, displayed by:
	lsmod | grep snd_ali5451
Module                  Size  Used by
-------------------------------------
snd_ali5451            24460  1 
snd_ac97_codec         93088  2 snd_intel8x0m,snd_ali5451
snd_pcm                89864  4 snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    55268  9 snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
-------------------------------------
 Note that mere loading does NOT establish that snd-ali5451 is the correct driver, rather
 than hsfmodem drivers.  But snd-ali5451 may still support readout of Subsystem information.

====== Writing residual advice ========
 The Major.Minor versions differ for the 
	the compiler used in kernel assembly:  4.0
	and the designated compiler:           none
 But there must be a match on the target for driver installation, 
 of gcc Major.Minor versions or kernel and drivers!!
 Otherwise the drivers will fail to load with warning:
	Invalid module format!!"
	See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 

If compiling a modem driver proves to be necessary, one of the two procedures must be followed.
If not yet on the Internet, put the Dapper install CD in the drive
Open a terminal and therein:
$ sudo apt-get install  gcc-4.0  make
Additionally the package linux-headers-2.6.15-26-386 must be downloaded.  
Go to http://packages.ubuntu.com/  and search for linux-headers-2.6.15-26-386 
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
	make linux-headers-


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 08:00 /usr/sbin/pppd
To enable dialout without Root permission do:
	$ su - root
        # chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	$ SUDO chmod a+x /usr/sbin/pppd
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


```

---

### Post by wpshooter on 2006-08-24
Covek:

Here is my take on this, others may disagree.  But if you choose to proceed I hope you can find the assistance you need.  

When I first attempted to install and use Ubuntu a number of months ago, I was still using dial-up modems on all of my computers and dial-up ISP for my internet connection.  When I tried I could never find out how to get the O/S to recognize the dial-up modem.  I have since, about 6 months ago, switched from dial-up to Verizon DSL service.  Once I did that I had zero problems in getting connected.  It is my opinion, that even if you get your modem configured, the dependence of the speed of your internet connection in downloading and applying updates to your Ubuntu O/S not to speak of other things you will want to do with your internet connection, will make trying to use and maintain Ubuntu a very frustrating effort.  I would recommend that if there is any way possible that you switch to broadband internet service before you attempt to use Ubuntu.

Good luck in your efforts.

---

### Post by CovekNaFrezi on 2006-08-24
DSL is not available in my area. Cable is expensive. They are the only ones in the area who provide cable and so they pump the prices up to an unbelievable price. I'll stick to modem if possible on Ubuntu. If not, comes the good ol XP.

---

### Post by xpod on 2006-08-24
I get broadband(1meg)through my set top box which has a simple ethernet converter adapter on the end that i plug into a usb port.
Plus i can unplug it and plug it into ANY pc in the house and my internet works fine on all.(not at home network stage just yet)
I am now waiting on a tech coming to give us a cable modem i apparently require for my soon to be upgrade to 4meg ....

But after a recent post plus all the threads i see regarding cable modem problems im begining to think i`ve made a bad decision.Plus i here i`ll need to do something called "mac address cloning" with a router if i want to use the internet connection on any other pc(so i was told)...I use the USB method instead of the straigtht ethernet one because i did`nt have the right port on the pc at the time.I like my USB way now though
I only use it to stick games on the Kubunto and m.e pc`s for the kids so the whole "home network" setup thing is hassle i dont need just now.OR any potential hassle ive got coming next week with this new "cable modem".

IS it time to call NTL back and cancel mabey???
Im only doing the upgrade cause it works out cheaper believe it or not.
Im not asking for advice here...just merely commenting.I posted about it the other day but i was`st any the wiser from it...

---

