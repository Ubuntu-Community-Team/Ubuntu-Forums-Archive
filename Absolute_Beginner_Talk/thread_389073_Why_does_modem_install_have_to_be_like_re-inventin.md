---
title: "Why does modem install have to be like re-inventing the wheel?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-20
I am clueless about getting my dial up modem working. I ran scanmodem and I have a pctel type modem. 
I downloaded the driver from the site they recommended. The instructions are pretty cryptic.

According to the instructions I need something called GCC???
Is this something included with ubuntu? Is this something I have to download or install? They don't say.

Also I need MAKE and PERL. What are these? Do they come with ubuntu? IS this something I need to install, download?????   No clue???

I have visited the ubuntu forum how to pages and they don't seem to be very informative.

It sure would be nice to have a beginner tutorial to get these very basic things working.
If there is one I can't find it.

Any help would be appreciated. Thanks

---

### Post by KenSentMe on 2007-03-20
Can you tell us where the instructions are that you mentioned, that might help us help you. 

Maybe this page on the Ubuntu Wiki can also help you:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by linuxjerk on 2007-03-20
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Yes that's the exact link that has me confused. They mention one version of gcc 3.4 and they say don't  use ver 4.0.
I have ubuntu 6.10. All I see is gcc 4.0 I take it that this is a C compiler?????
Doesn't tell you anywhere in ubuntu that I can find to install it????
 
What is MAKE and PERL I need to be a programmer to figure this stuff out.

Recompiling the kernel???? What the heck!

This is the link where I got the driver: [http://linmodems.technion.ac.il/pctel-linux/](http://linmodems.technion.ac.il/pctel-linux/)
This is the file: pctel-0.9.7-9-rht-7.tar.gz

The instructions I mentioned are in this zipped file.

I feel like I'm rewriting the os.

---

### Post by linuxjerk on 2007-03-20
Spilled the beans is right!!
Man this is a fast moving forum.
Does anyone else have a pctel like modem that can help me?

---

### Post by X-626 on 2007-03-20
What you may need is a package called "sl-modem-daemon".  Since you can't get your modem to work, I am going to give you another way to get the package.  Simply go here: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.10%2B2.9.9d%2Be-pre2-5build1_i386.deb&md5sum=1567d1e9f242b8cdfce6afe2f0779289&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.10%2B2.9.9d%2Be-pre2-5build1_i386.deb&md5sum=1567d1e9f242b8cdfce6afe2f0779289&arch=i386&type=main)

Pick the mirror that is closest to you.  After that, go to where you saved the file, right click on it, and select "Open with GDebi Package Installer".  Then just click the button that says Install.

---

### Post by zvacet on 2007-03-20
```
sudo aptitude install build-essential
```
and compile commands are
1. tar xvzf  program.tar.gz
2.cd /program     
3. ./configure
4. make
5. sudo make install

---

### Post by linuxjerk on 2007-03-21
Thanks X-626 I downloaded the package and installed it. Now how do I know it actually worked? When I start the browser I don't get a dialer popup? What am I doing wrong?

Thanks zvacet for the help. I know those commands look very simple to you but they are still a little cryptic to me.
Is that the exact way I would type them in? Or are some of the words substitutes for the
names of programs I have?
These commands are to be typed in the recovery terminal? Or where?
I there a dialer or something I have to start or should that appear when I start the
browser.
Please have patients, I am a total noob to this stuff.
Thanks

---

### Post by linuxjerk on 2007-03-21
Incredible, I've never had this much trouble with any operating system I've ever used.
How do I get a dialer running? I think wvdialer is installed. I don't have a clue how to run it.
I still don't know if my modem is installed correct????????

---

### Post by dstew on 2007-03-21
Find instructions by entering man wvdial in the terminal window. To start wvdial, use the command sudo wvdial.

Also, did you see if you could set it up now in the network administration window?

---

### Post by linuxjerk on 2007-03-21
Hi dstew
Do you mean where you setup the number you dial and password and port and stuff?
I have always been able to do that. I'm not to sure about which port to use. The modem is a winmodem of pctel type. According to scanmodem it's on PCI. I have /dev/modem set now??
I will try to get wvdial going. Do I have to set up that to?

---

### Post by kinematic on 2007-03-21
> **linuxjerk said:**
> Incredible, I've never had this much trouble with any operating system I've ever used.
How do I get a dialer running? I think wvdialer is installed. I don't have a clue how to run it.
I still don't know if my modem is installed correct????????

blame the modem manufacturer....they're the ones not supplying decent linux drivers to the kernel maintainers or supplying the info they need to write them.

---

### Post by linuxjerk on 2007-03-21
Hey dstew
I ran wvdial and got this error message: Cannot open /dev/modem: No such file or directory
Do you know what this means? I suppose it's because my modem still isn't installed correctly.
thanks

---

### Post by linuxjerk on 2007-03-21
Hey dstew
I ran wvdial and got this error message: Cannot open /dev/modem: No such file or directory
What did I forget to do??
Probably because my modem still is not set up correctly. Probably no driver.
Thanks

---

### Post by dstew on 2007-03-21
If the modem is installed, wvdial will call your ISP and start a PPP (internet) session. It is strictly a terminal application, and the information it uses to dial is in the file /etc/wvdial.conf. If you want to use wvdial, which is the most reliable way to connect, you will need to edit the wvdial.conf file. To edit the file, enter in a terminal window:

sudo gedit /etc/wvdial.conf

If the wvdial.conf file is not present, type the command wvdialconf in the terminal. This will create a fresh wvdial.conf file, with your modem information patched into it. You will still need to put in the phone number, your username and password for your ISP.

To read more about wvdial and wvdialconf, you can issue the commands

man wvdial

 or

man wvdialconf

in the terminal window. The man pages are also on the internet:

[http://www.die.net/doc/linux/man/man1/wvdial.1.html](http://www.die.net/doc/linux/man/man1/wvdial.1.html)
[http://www.die.net/doc/linux/man/man1/wvdialconf.1.html](http://www.die.net/doc/linux/man/man1/wvdialconf.1.html)

Edit: I just saw your post, you are still at the stage where the modem is not installed. You said you installed the driver according to what X-262 said. I want to confirm that you installed the stable driver as listed here:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.10%2B2.9.9d-6ubuntu1_i386.deb&md5sum=8f67b8b3ce6fdef952b9ebcfada7c7c6&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.10%2B2.9.9d-6ubuntu1_i386.deb&md5sum=8f67b8b3ce6fdef952b9ebcfada7c7c6&arch=i386&type=main)

---

### Post by Steven_B on 2007-03-21
linuxjerk, please try to avoid sounding like you're whining about Linux.  Linux isn't Windows, and it takes some getting used to. Take a look at [http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm") for a further explanation of what I mean.
A lot of questions, such as how to install packages (gcc, etc.) can be found with minimal work using the wiki, forums or Google.
If you're willing to put some work into it, you'll find that Linux really can be way better than Windows.
Thanks.

---

### Post by linuxjerk on 2007-03-21
I checked that path and the /dev/modem is a shortcut that says it's broken
Says /dev/ttySL0 does not exist.
Yes I did run the install of the file at the link that X-626 gave me.

---

### Post by linuxjerk on 2007-03-21
I just want this to work. I don't think I'm complaining any more than necessary.
Oh I forgot that my mouse is on tty0.
Anyway yes it looks like there will be a lot of work getting this going.

---

### Post by dstew on 2007-03-21
Enter on a command line:

**modprobe slamr**

and after that

**slmodemd --help**

That should tell us that the modem driver software is in place.

---

### Post by Bartender on 2007-03-21
I read dozens of threads from folks who were having nothing but grief with dial-up modems.  Decided there was no way I was gonna be able to figure out how to complie this, and tar.gz that, so went shopping on ebay.  Bought a couple of old Sportster external modems.  Hooked them up to my Windows PC< visited the USR website, flashed them to the latest firmware, then hooked them up to my test PC with Dapper installed.  Haven't even used wvdial.  Used the graphic Modem setup and put Modem Monitor applet on the upper panel.
Edgy, for some reason, doesn't allow me to set up the modem using the same graphic install procedure.  I set dial to "Tone" and it keeps going back to "Pulse".  So you're better off with Dapper and I hope they fix that in Feisty.

---

### Post by linuxjerk on 2007-03-21
Boy that's what I need right now. A bartender.

modprobe slamr  yielded 
FATAL: Module ungrab_winmodem not found.
FATAL: Module slamr not found

slmodemd -help yielded a bunch o switches on slmodemd usage.

I think I'm going to pour some rum.

---

### Post by linuxjerk on 2007-03-21
Did that telll you if the sl-modem software was installed?

---

### Post by dstew on 2007-03-21
If you want to keep flogging -- I'm not saying you should -- you would uninstall the package:

**sudo dpkg -r sl-modem-daemon**

then install it again

**sudo dpkg -i sl-modem-daemon**

and look at the system messages for clues to why it did not install the slamr module correctly using:

**dmesg**

Then again, as Bartender said, you could just buy a real modem, and give up on the softmodem. But, somebody went to a lot of work to write the software, so maybe to honor their effort we keep trying...or maybe not...up to you.

---

### Post by linuxjerk on 2007-03-21
dstew
I am having a heck of a time getting it to install using the sudo command you show.
The problem is I'm not getting the path correct I think.
The downloaded package is in a folder on my desktop.
I originaly installed it by just double clicking on the icon. Maybe that was the wrong thing to do.
Where should the package be to use your command line?
thanks

---

### Post by dstew on 2007-03-21
Your desktop folder is in your home directory. The full path name of your desktop should be

/home/<your user name>/Desktop

The character '~' is used to abbreviate the stem path of your home directory:

~/Desktop

So, if the package is in your Desktop directory, you could either navigate to there using **cd**, then execute it, or you could put the following on the command line from anywhere:

**sudo dpkg -r ~/Desktop/sl-modem-daemon**

If it is in a folder on your desktop, you have to modify the path name accordingly. I don't think it is important where the package is.

---

### Post by linuxjerk on 2007-03-21
sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
This is the complete name of the file. It seems to be a self executing file.
I still can seem to get sudo to install it using the path.
When I first installed it I just double clicked on it and the package installer installed it.
Is this wrong?

---

### Post by linuxjerk on 2007-03-21
I went back to this site: [http://packages.ubuntu.com/cgi-bin/d...i386&type=main](http://packages.ubuntu.com/cgi-bin/d...i386&type=main) 
and downloaded from another mirror.
The 2 files are different. The new one is smaller.
I installed this one and tried modprobe slamr and this time only the slamr module wasn't there.
What's going on here? I thought these files were identical?
wvdial still can't find the modem

---

### Post by oilchangeguy on 2007-03-21
this is 2007, not 1997. why suffer with dial-up? is broadband available in your area?

---

### Post by linuxjerk on 2007-03-21
no

---

### Post by oilchangeguy on 2007-03-21
how do you get tv signals? ant., sat., cable? if you use satellite, highspeed should be available from your satellite provider.

---

### Post by linuxjerk on 2007-03-21
Are we even sure this is the right package for my mode. Scanmodem calls it a pctel.

I'm to far from the local tel for dsl. And sat is a bit expensive for me.
Besides I can do dialup with every version of windows I have. Why shouldn't I be
able to with linux?
It's a principle.

---

### Post by oilchangeguy on 2007-03-21
i understand what you're saying. the point i was trying to make is todays internet is much different from years ago (it was mostly text). and many cable and phone companies are making lower level high speed packages available (400-500kbs vs the maybe 50kbs for dial-up) at prices that rival those of dial-up. so for you, and others like you, it's too bad high speed is not available. you're missing alot.

---

### Post by X-626 on 2007-03-21
That should be the correct package.  SmartLink (which is what that package is for) makes the chipset that the PCTel modems use.  The modem that i have is also PCTel, but that driver worked for it.  You may not have the type of PCTel modem that the driver package works with (and to be honest, I'm not sure of what types of PCTel modems are compatible with it).

I'm sorry that this is causing you so much trouble.  It took me a while to figure out how to dial-up to my ISP (they change a few things before sending it) and then I had to figure out how to get my modem working.  I had to do a lot of research on the topic.  Do you know the exact type of modem you have?  Mine is HSP56 MR.  I don't really know what could be causing you so much trouble.

---

### Post by dstew on 2007-03-21
Double-clicking a debian package should work fine. For some reason, the installation is not working. To see why, you need to do the installation, then print out the system log using the command **dmesg**. This will show what the installation program did with the slamr module.

---

### Post by dstew on 2007-03-21
OK, one mistake I made. The slamr kernel module is a separate package from  sl-modem-daemon. I am trying to find an appropriate package to install. Also, the package for sl-modem-daemon I think should be:

sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb

---

### Post by will_in_wi on 2007-03-21
Sadly modems in linux are not always the easiest things in the world to set up.

There are two types of modems, winmodems and hardware modems. Simply, the difference is that winmodems have all of the software that tells it how to dial and connect in the driver that runs on the operating system. Hardware modems have all of that information on the physical card. This means that while hardware modems require the programmer to write one piece of software that will run all brands of hardware modems easily, software modems (winmodems) require a special piece of software for each individual modem. You probably have a software modem.

A couple of years ago it was nearly impossible to get anything other than a hardware modem working on linux. Fortunantly this has changed. However it is still a little harder to get a software modem working under linux. It seems that you have done the hard part and gotten the driver working. To verify this could you open a terminal (Applications -> Accessories -> Terminal), type dmesg and hit enter, then post the output.

I think the modem you have is very similar to the one I had (I now have broadband).

In any case you want to open the Add/Remove utility located at the bottom of the Applications menu and install Gnome PPP. When you select it to install, it might say that it conflicts with another piece of software. If this is the case then open synaptic (System -> Administration -> Synaptic Package Manager) and search for resolvconf. Uninstall resolvconf then go back to the Add/Remove Utility. Try installing Gnome PPP again. If it works then in the Internet menu should be an entry entitled Gnome PPP. Open this utility and it should be self explainatory.

Thanks for using Ubuntu!

---

### Post by dstew on 2007-03-21
My last contribution for today:

There is another kernel module besides slamr that will work with slmodemd. It is called ALSA. It is a sound module, but you can use it for a winmodem too. And it is already present in Ubuntu. You can use these two commands to see if it will work:

```
modprobe snd-intel8x0m
slmodemd -a hw:1
```

If you get a good response from the second command, then try wvdial.

---

### Post by linuxjerk on 2007-03-22
X-626: This modem is a HPS56 using the  C-Media CM8738 chip I think.

dstew: Thanks I am going to try that. Can you tell me what slamr is?

Here is some docs showing output and other info from scanmodem.

I couldn't figure out how to save the output from the terminal while sl-modem was installing

so I will just type it in:

Selecting previously deseleted package sl-modem-daemon
(Reading database ... 88197 files and directories currently installed.)
Unpacking sl-modem-daemon (from .../sl-modem-daemon_2.9.10+2.9.9d-6ubuntu.i386.deb)...
Setting up sl-modem-daemon (2.9.10+2.9.9dubuntul) ...
Installing new version of config file /etc/modprobe.d/sl-modem-daemon.modutils ...
Installing new version of config file /etc/inot.d/sl-modem-daemon ...
FATAL: Module slamr not found.
Smartlink modem driver not available for this kernel. Please read README.Debian or try to install the package sl-modem-modules-2.6.17-10-generic. Exiting... invoke-rc.d: initscript
sl-modem-daemon, action "start" failed.


OUTPUT FROM scanmodem:

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0f.1	13f6:0211	13f6:0211	Communication controller: C-Media Electronics Inc CM8738 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:0f.1 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  00:0f.1
   Class 0780: 13f6:0211 Communication controller: C-Media Electronics Inc CM8738
      Primary PCI_id  13f6:0211
 Support type needed or chipset:	PCTEL
 

    At [http://linmodems.technion.ac.il/pctel-linux](http://linmodems.technion.ac.il/pctel-linux)
 Get the pctel-0.9.7-9-rht-7.tar.gz
 Unpack under Linux with:
    tar zxf pctel*.tar.gz
 and read instuctions therein.
  Read Pctel.txt and Modem/YourSystem.txt for follow through guidance.

 Writing Pctel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 15:13 /usr/sbin/pppd

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


PCTEL INFORMATION TEXT:


 Vendor=134d is PCTel, but their modem sector has been sold to Conexant,
 and Conexant is Not providing official code updates.
 The volunteer maintainer for current updates is Robert Thornburrow, with
 downloads from  [http://linmodems.technion.ac.il/pctel-linux/](http://linmodems.technion.ac.il/pctel-linux/)
 
 The AMR variants are supported by the pctel driver only under 2.4.n kernels 
 Under 2.6.n kernels, the AMR Pctel variants and the HSP56 MicroModem 688T 
 have support through the Smartlink software.  The rest of this text is only 
 cogent to modems using the 2.6.n driver triplet: pctel, ptserial and linmodem.
 
 Under 2.6.x kernels, these modems are supported by the pctel-0.9.7-9-rht-7 
 From the README file therein:

PCI ID (x)  Name                                       Chip(set)      HAL
~~~~~~~~~~  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  ~~~~~~~~~~~~~  ~~~~~~~
134d:7890   PCtel HSP MicroModem 56                    PCT789T-C1     pct789
134d:7891   PCtel HSP MicroModem 56                    PCT 789T       pct789
134d:7892   PCtel HSP MicroModem 56                    PCT 789T-A     pct789
134d:7893   PCtel HSP MicroModem 56                    S911 K017      pct789
134d:7894   PCtel HSP MicroModem 56                    FT13           pct789
134d:7895   PCtel HSP MicroModem 56                    PCT789T-C1     pct789
134d:7896   PCtel HSP MicroModem 56                    PCT789T-C1     pct789
134d:7897   PCtel HSP MicroModem 56                    PCT789T        pct789
13f6:0211   C-Media CM8738                             CM8738         cm8738

  Do the following preliminary steps:
	Unpack with command:       tar zxvf pctel-0.9.7-*.tar.gz
  	Change directory:             cd pctel-0.9.7-9 (for example).
  	Read README file	        less README   (space bar goes to next page)
 	Is a compiler installed?  Test with:           gcc 
  	If not found, install it from your Linux distribution.
  	Become root:                     su  root
  	Seeing lspci?             	 lspci
	  If not, install the package   pciutils .
	Now you can follow instructions in README

 The ISA card pct388p modem is not supported by the current driver series.
 
 During PCtel code installations, the node made is character device /dev/ttyS_PCTEL0  c 62 69
 Check with:
     ls -l /dev/ttyS_PCTEL0
     
 There is a pre-compiled binary component in the Pctel code which was assembled with a gcc 2.95 compiler
 A consequence is the loading fails under kernels compiled with gcc 3.n , 
 unless forcing (-f) is used:
 	# insmod -f pctel
	# insmod ptserial
This can be automated by adding the following lines to /etc/modules.conf
 
####### for pctel modem ######
alias char-major-62 pctel
alias /dev/modem ptserial
install pctel /sbin/insmod "-f" "pctel"
post-install pctel /sbin/insmod ptserial

# country code for pctel modem, for USA
options ptserial country_code=1
######## pctel end ####

then run:
# depmod -a
to inform the System and thereafter
# sudo modprobe ptserial
will load all three drivers,

 For some Systems, PCTel function requires disablement of apmd power monitoring function.

 System problems of various severity have been reported after modem usage.
 These may be alleviated by the following steps after a modem usage session.
 Log into a console as:
 # su - root
 # lsmod 
 to display loaded modules.
 # sudo modprobe -r ptserial
 # lsmod
 ====== end Pctel section =======

---

### Post by linuxjerk on 2007-03-22
dstew:

modprobe snd-intel18x0m yields:

FATAL: Module snd_intel18x0m not found.

slmodemd -a hw:1 yields:

error:  mixer setup: attach hw:1 error: No such device
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
error: alsa setup: cannot open playback device 'hw:1': No such device
error: cannot setup device 'hw:1'

Hope this tells you what you need to know.

---

### Post by linuxjerk on 2007-03-22
Looks like I found 2 differnt versions of the sl-modem
Doesn't matter cause neither work.

ver 2.9.9d spe 22 2005
ver 2.9.9e-pre1 may 28 2006

Anyone know of other versions? Maybe an older one would work.

---

### Post by dstew on 2007-03-22
Hi again. We need to find a driver (kernel module) that will work your modem. The original suggestion by the ScanModem output was to use the module in the package pctel-0.9.7-9-rht-7.tar.gz. You said you downloaded it, but it seems you were unable to compile it. Is that correct? Maybe that is our best hope for the present. There may also be an already complied module in the linmodems.technion site, called pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz. However, you would have to go back to the 2.6.15-23-386 kernel to use it. Otherwise, it looks like you will have to try to compile the module in pctel-0.9.7-9-rht-7.tar.gz. You probably do not need to compile a whole custom kernel, but I think in order to compile the module correctly you might need the kernel source code, which you can get. But, this is getting complicated, especially since you don't have an internet connection on the computer!

---

### Post by linuxjerk on 2007-03-22
Hi
Yes I did download the file that scanmodem recommended. I have not tried to compile it.
I'm not a very good programmer so I sort of got stuck there.
I'll try anythin you want. I don't have much to loose.
Thanks

---

### Post by linuxjerk on 2007-03-22
Can you tell me what this slamr module is?
Where is it suppose to be?
Every time I try to install it always the same error slamr module not found?

---

### Post by linuxjerk on 2007-03-23
I guess everyone is right. this seems to be a hopeless cause.

---

### Post by linuxjerk on 2007-03-23
I have succeded in loading the modem drivers. Now I'm having trouble with wvdial.
Anyone have experience with setting wvdial up?

---

### Post by dstew on 2007-03-23
I have put my Conexant winmodem back in my box to try to set it up. I took it out before I installed Linux because I had DSL, but like you I want to solve this problem. Unfortunately, I have been unable to download the scanmodem program (site does not answer). I will keep trying.

Regarding wvdial, I would say look at the man pages (enter **man wvdial** in the terminal).

---

### Post by linuxjerk on 2007-03-23
I have everything working now, sort of. The wvdial thing was those semicolons used to
make comment llines. I wasn't expecting that.
I'm glad I went back to the original scanmodem recommended driver. But I needed a lot
of help to get it installed.
If you want I can email scanmodem to you it's not very big. If that is acceptable practice.
Shoot me your email and I'll send it to you.

---

### Post by dstew on 2007-03-25
Thanks linuxjerk. I was finally able to get scanmodem from the technion site. I think it was resting on the Sabbath. It detected my modem, and I went to the linuxant site and got the driver package. I tried the dpkg installation method, had to install linux-headers for my kernel version. It built and installed correctly, and wvdial worked fine after that.

---

