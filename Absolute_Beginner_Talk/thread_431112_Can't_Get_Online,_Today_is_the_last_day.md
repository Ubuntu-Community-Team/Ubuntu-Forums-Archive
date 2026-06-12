---
title: "Can't Get Online, Today is the last day"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by fruitsofherwomb on 2007-05-02
If I don't get online with Ubuntu today I might as well uninstall it. It doesn't seem like its helpful to post here, since I've done it like 5 times. Heres my sauce: 

I have: 

**Modems:**
A external Modem: Actiontec 56k External USB/Serial (EX5600)
A software modem that came with the PC
A Creative Soundblaster Modem Internal 

THREE MODEMS, I need ONE To freaking connect

**ISP:** 
People PC

**OS:**
Dual boot
Windows XP Home Edition
Ubuntu 7.04 

Known Problems: 

I did a scan with the Software Modem that came with my PC, It said it was supported but the drivers never installed not matter what I tried.

My Ubuntu Detects the Actiontech modem, it makes noises and then it drops and never connects

:( I'm a sad Panda, I need help urgent. 

**[COLOR="Red"]WARNING:[/COLOR]** I can't get online on Ubuntu so if you are going to submit codes or want me to get something I have to download it on Windows portion. Thanks You.

---

### Post by oilchangeguy on 2007-05-02
it's 2007, not 1997. why would you use dial-up anyway? what part of calif. are you in? most phone and cable companies have entry level highspeed packages available with prices at or near those of dial-up. and alot faster 300-500kps instead of the maybe 50kps you get with dial-up. it's time to upgrade your internet connection.

---

### Post by annda on 2007-05-02
> **oilchangeguy said:**
> it's 2007, not 1997. why would you use dial-up anyway? what part of calif. are you in? most phone and cable companies have entry level highspeed packages available with prices at or near those of dial-up. and alot faster 300-500kps instead of the maybe 50kps you get with dial-up. it's time to upgrade your internet connection.

either that, or get a modem that has linux drivers, or better yet - uses an open standard covered by linux.

check out those links:
[http://www.linux-drivers.org/](http://www.linux-drivers.org/)
[http://www.linuxquestions.org/hcl/index.php/cat/121](http://www.linuxquestions.org/hcl/index.php/cat/121)

---

### Post by fruitsofherwomb on 2007-05-03
> **oilchangeguy said:**
> it's 2007, not 1997. why would you use dial-up anyway? what part of calif. are you in? most phone and cable companies have entry level highspeed packages available with prices at or near those of dial-up. and alot faster 300-500kps instead of the maybe 50kps you get with dial-up. it's time to upgrade your internet connection.

I live in the country, Don't badger me, dude.

---

### Post by fruitsofherwomb on 2007-05-03
> **annda said:**
> either that, or get a modem that has linux drivers, or better yet - uses an open standard covered by linux.

check out those links:
[http://www.linux-drivers.org/](http://www.linux-drivers.org/)
[http://www.linuxquestions.org/hcl/index.php/cat/121](http://www.linuxquestions.org/hcl/index.php/cat/121)

I got the Actiontec external cause I was told it was a hardware modem.:confused:

---

### Post by crav on 2007-05-03
> **fruitsofherwomb said:**
> I live in the country, Don't badger me, dude.
I think what he's really trying to say is that nowadays, so few people use dialup and so many people use broadband that it isn't worth many developers' time to write drivers for dialup modems.

---

### Post by imdidactic on 2007-05-03
Your Actiontec modem is NOT open source.  On their website they state clearly that it is only Windows compatible.  [Here]("http://www.actiontecsupport.com/files/USBModemDrivers.exe") is the driver file, although it won't do you any good in linux.

The Zyxel 630-11 is a linux supported usb modem.

---

### Post by fruitsofherwomb on 2007-05-03
Alright, I scanned the one that came with my old computer and someone did a topic but I couldn't get the drivers working, since I have to install them offline. 


I might scan my Creative Modem but I doubt it will have drivers. 

```
Only plain text email is forwarded by the DISCUSS@linmodems.org List Server.
Do use the following as the email Subject Line:
SomeName, YourCountry Ubuntu 6.10 kernel 2.6.17-10-generic
This will alert cogent experts, and distinguish cases in the Archives.
YourCountry will enable Country Code guidance.
Occassionally responses are blocked by an Internet Provider mail filters.
So in a day, also check the Archived responses at http://www.linmodems.org .
Local Linux experts can be found through: http://www.linux.org/groups/index.html
-------------------------- System information ----------------------------
CPU=i686, Ubuntu 6.10
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
scanModem update of: 2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

PCI slot PCI ID SubsystemID Name
---------- --------- --------- --------------
00:09.0 11c1:044e 1235:044e Communication controller: Agere Systems LT WinModem

Modem interrupt assignment and sharing:

--- Bootup diagnositcs for card in PCI slot 00:09.0 ----

=== Finished modem firmware and bootup diagnostics section. ===
=== Next deducing cogent software ===

For candidate modem in PCI bus: 00:09.0
Class 0780: 11c1:044e Communication controller: Agere Systems LT WinModem
Primary PCI_id 11c1:044e
Support type needed or chipset: Agere.DSP



The modem has a supported Lucent/Agere Mars or Apollo DSP (digital signal
processing) chipset. Support packages for 2.6.n kernels are at:
http://phep2.technion.ac.il/linmodem...l-2.6/martian/
For a temporary fix for 2.6.18 kernels see

See AgereDSP.txt for Details.
DSP=1

Vendor 11c1 is Lucent Technologies or subsidiary Agere Systems, Inc. Their Linux
code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its
continued maintenance is only initiated at the request of a major chipset buyer,
or comparable sponsor. Several different modem chipset types are produced,
and two have support under Linux:
Device ID Support Name Comment
--------- ------------- ----------- -----------------------------
0480 serial drivers Venus controller chipset 1673JV7
0440-045d martian Mars/Apollo DSP (digital signal processing) chipsets
0462 none 56K.V90/ADSL Wildwire
048(c,d,f) none SV2P soft modem
0600 none soft modem, very few in the field.
062(0-3) none SV92PP,Pinball soft modem, in some HP desktop PCs

0x044e -- Mars 3 Mercury data fax only
-------------- end Agere Systems section -------------------

Completed candidate modem analyses.

The base of the UDEV device file system is: /dev/.udev

Versions adequately match for the compiler installed: 4.1.2
and the compiler used in kernel assembly: 4.1.2



Compiling resources appear complete:
make utility - /usr/bin/make
Compiler version 4.1
kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
-rwsr-xr-- 1 root dip 260920 2006-07-10 12:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
http://phep2.technion.ac.il/linmodem.../msg02637.html

To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd

Checking settings of: /etc/ppp/options
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
see http://linmodems.technion.ac.il/biga.../msg04656.html


Don't worry about the following, it is for the experts
should trouble shooting be necessary.
================================================== ========

Checking for modem support lines:
--------------------------------------
/device/modem symbolic link:
slmodemd created symbolic link /dev/ttySL0:
Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*", SYMLINK+="modem"
Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-baseptions snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-baseptions snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
Within any ancient /etc/devfs files:

Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
```

The person said this should be the code for the modems, but obviously I have to be online to install them. 

```
sudo apt-get install linux-headers-$(uname -r) build-essential wvdial
mkdir ~/modem
mkdir ~/modem/tmp
cd ~/modem
wget http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-20061203.tar.bz2
wget http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz
tar xjvf martian-20061203.tar.bz2
tar xzvf martian-full-20061203.tar.gz -C tmp
cd martian
cp ../tmp/martian/modem/ltmdmobj.o modem
make clean
make
sudo make install
sudo depmod -a
sudo modprobe martian_dev
sudo martian_modem
sudo wvdialconf /etc/wvdial.conf
```

Anymore help will be appreciated.

---

### Post by fruitsofherwomb on 2007-05-03
Bump For Ultimate Help < Wtf Over 9000

---

### Post by LaurelLynn on 2007-05-03
The modem not working on Edgy(6.10) is why I went back to Dapper(6.06LTS).  Dapper will be supported till 2009 and it works fine for me.

Searching for a solution, I found a thread that implied a developer trying to upgrade the modem software mistyped one of the modem commands, adding an extra character. I tried editting the file and changing the settings listed, but it didn't work for me (may have just missed one). No idea where that thread is anymore.

It was just easier for me to go back than to keep trying. Would be nice to know a solution though.

---

### Post by fruitsofherwomb on 2007-05-03
What modem? i listed 3 ;)

---

### Post by Wake Rider on 2007-05-03
I had exactly the same problem, despite a lot of posts here and trying numerous suggestions, I couldn't get Ubuntu to connect to the internet using a modem. In the end I had to convince my father to upgrade to broadband which Ubuntu connects with quite happily.

---

### Post by LaurelLynn on 2007-05-03
This thread shows that you share this problem with quite a few others:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304)

It implies that installing the older problem gnome-ppp will allow you to get a modem connection.

Haven't try it though, since going back a version worked for me.

This page has some alternatives:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02)

From the reading I did a month ago, I got the impression that the problem started in the latest Debian upgrade, and was propogated to Ubuntu. Seems everyone is waiting for Debian to fix the problem :(.

---

### Post by jitsu on 2007-05-03
Hi Laurel:

I have the same problem that you have--my serial modem works with Ubuntu 6.06 and won't work with Ubuntu 6.10. 

I've inquired about broadband but it is not available out here in the boondocks and I'm going to have to live with dialup. Hopefully there can be some type of fix that will help the dial up users.

good luck,
jitsu

---

### Post by lenooh on 2007-05-04
why don't you take your computer to someone that has a broadband internet connection and run that apt-get command that's supposed to make your modem work?

or why don't you get another (windows) pc, connect it with your modem, set it as a gateway, and then run the apt-get command on your pc?

:confused:

---

### Post by seshomaru samma on 2007-05-04
double post......sorry...

---

### Post by seshomaru samma on 2007-05-04
there is wget for windows , get it [here ]("http://www.christopherlewis.com/WGet/WGetFiles.htm")
run the wget command ,(
```
wget http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-20061203.tar.bz2
wget http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz
```) put the files on a USB stick or on an XP partition which you can see from Ubuntu and follow the rest of the instructions (that you posted )

---

### Post by paulphillips on 2007-07-18
I had problems connecting with a hardware modem also.  I fixed by installing Gnome-ppp and setting the options as follows (see screen snapshot).

Until I set these options I was getting "Request Denied" errors and "Authentication Failed" errors.

Hope this is of some help.

---

### Post by edwardLS on 2007-07-18
I am not completely certain about this, but I believe that the PeoplePC requires the use of a proprietary dialer to operate correctly.  I had at one time planned to switch to PeoplePC, but in discussion with the Support team I came to the conclusion that Linux and PeoplePC was a"non-starter".  

I believe that any ISP which requires that you download a small software-download will not be compatible with Linux.  I use both external and WinModems in my Ubuntu installations (Dapper and Feisty) with my ISP.  They all work well; however, the WinModem did require some additional work.

Good luck.

---

### Post by Bartender on 2007-07-19
edward -
I haven't tried it personally, but believe you are correct regarding PeoplePC.  They are probably one of the worst as far as proprietary software.  Some friends wanted PeoplepC so I tried to install to their XP machine.  The PPC CD wanted to install several programs, but it kept crashing on the last one.  I uninstalled PPC and hooked them up with Copper.net, which does work with Linux.
I don't know if the OP has figured out his problems yet, but can confirm that the Edgy/Feisty Networking GUI for dial-up is broken.  You have to use wvdial or pppconfig
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

### Post by misfitpierce on 2007-07-19
People PC need to upgrade :)

---

