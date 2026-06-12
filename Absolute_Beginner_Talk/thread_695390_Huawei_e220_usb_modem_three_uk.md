---
title: "Huawei e220 usb modem three uk"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-02-13
Just installed Ubuntu on a separate partition total newbie when it comes to linux although i reckon im getting the hang of it 

im having trouble getting connected to the internet with my huawei e220 usb modem

im on xp at the minute thats why i can access the net

iv been reading forum after forum post after post trying things but i still cant get it going i read a while ago a post on here saying to download the vodafone drivers i did that but nothing happend iv changed setting in the vwdial.conf file aswell

just to make sure did i download the correct vodafone driver this is the name on the one i used

vodafone-mobile-connect-card-driver-for-linux-20080104-installer.run

has anyone else got a away to get this modem working?

im really limited in what i can do atm on ubuntu with no internet


cheers.

---

### Post by spiderbatdad on 2008-02-13
I just spent nearly two days helping someone NOT get his modem working!
I see there is a deb.for Gutsy at that download site. It would install with a click. Unfortunately, it doesn't seem to include any documentation...apparently it's a driver and operator script...another modem with two modes.  But it looks like you will ultimately, after installing that package, still have to learn about either kppp, wvdial, or pppconfig. These are applications (or programs) that are used to connect to the internet by dial-up in Linux.   Kppp will probably be the easiest.  Though ppp through the network monitor included with Ubuntu, might work just fine.

---

### Post by coubury on 2008-02-13
I tried wvdial with no joy

---

### Post by spiderbatdad on 2008-02-13
Have you tired the deb package for the modem? Surely you'll need it...if it works, not to connect but to configure the modem.

 1.0	 2007-10-09 08:19
  nozomi-kmod-2.21-1.9-91.fc7.i386.rpm	
73 KB	337	i386	.rpm
  vodafone-mobile-connect-card-driver-for-linux-1.0-1.fc7.i386.rpm	
902 KB	1,107	i386	.rpm
  vodafone-mobile-connect-card-driver-for-linux-1.0-15.1.opensuse103.i586.rpm	
851 KB	375	i386	.rpm
  vodafone-mobile-connect-card-driver-for-linux-1.0-SLED101.i586.sh	
6.89 MB	1,001	i386	Other Source File
  vodafone-mobile-connect-card-driver-for-linux-1.0.tar.gz	
1.18 MB	1,970	Any	Source .gz
  vodafone-mobile-connect-card-driver-for-linux_1.0_edgy_i386.deb	
334 KB	522	i386	.deb
  vodafone-mobile-connect-card-driver-for-linux_1.0_feisty_i386.deb	
334 KB	3,455	i386	.deb
**  vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb**


Here's a how to that may be helpful. [http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by coubury on 2008-02-13
I downloaded this

 vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb 

and a similar one

got an error when i tried to run it

"ERROR DEPENDENCY IS NOT SATISFIADE PYTHON-TWISTED!

---

### Post by spiderbatdad on 2008-02-13
hmmm. python-twisted is in synaptic as a Ubuntu package...so if you sudo apt-get install python-twisted...and cd is enabled as a source, it should ask you to insert the cd, and you can install the package. Heres a screenshot...there are a number of Python-twisted-devs and what-not.

---

### Post by coubury on 2008-02-13
when i goto system repositories it says my list is out of date and i cant add anything

and i cant update it as i dont have any intenet access

---

### Post by spiderbatdad on 2008-02-13
If you navigate System>>Administration>>Software Sources, do you see the CD selected as a download source? If not, select it. Run ```
sudo apt-get update
sudo apt-get install python-twisted
``` I don't know it it will work, but worth a try.

---

### Post by ideogram_lon on 2008-03-09
Hello All,

I recently bought a huawei e220 from 3 mobile to use PAYG (with the student offer it's just 50 quid)

Here's how I get connected with gutsy gibbon:

Combo of:

1. 
sudo modprobe -r uhci_hcd
sudo modprobe uhci_hcd

2. 
rmmod usb-storage
rmmod usbserial
(the later might create an error.)

lsusb
- The last command shoul show the device connected similiar to:
Bus 001 Device 003: ID 12d1:1003

Run:
modprobe usbserial vendor=0×12d1 product=0×1003

Now, disconnect the Huawei E220 USB-modem and wait a few seconds before connecting it again.

- As soon as the device have stopped blinking green you should find three new USB-devices by running the command:
ls -al /dev/ttyU*

3. wvdial.conf
[Dialer Defaults]
Phone = *99#
Username = three
Password = three
Stupid Mode = 1
Dial Command = ATDT

[Dialer three]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","3internet"

4.
editing /etc/resolv.conf to add
nameserver 172.31.140.69
nameserver 172.30.140.69


Thanks to:
[http://www.mohdshakir.net/2007/12/05/huawei-e220-in-gutsy-gibbon-kubuntu](http://www.mohdshakir.net/2007/12/05/huawei-e220-in-gutsy-gibbon-kubuntu)
[http://www.inorp.com/blog/2007/03/13/ubuntu-guide-to-using-hsdpa-usb-modem-huawei-e220-with-the-tre-network/](http://www.inorp.com/blog/2007/03/13/ubuntu-guide-to-using-hsdpa-usb-modem-huawei-e220-with-the-tre-network/)

Regards, Ideogram

---

### Post by idefixuk on 2008-03-24
Hi,
Been trying for weeks to connect with this modem. I have Ubuntu 7.10.
I went through steps 1. and 2. of your instructions. But then, when I type ls -al /dev/ttyU* I get 'No such file or directory'.
Any idea of what else I can do? 
I am using here a windows laptop but I don't have connection on the one with Ubuntu.
Regards,

idefixuk

---

### Post by sa87 on 2008-03-25
follow the first post instructions (steps 1 to 6) in the following thread to get to the stage of having the 3 /dev/ttyUSB* devices.

[http://ubuntuforums.org/showthread.php?t=595064](http://ubuntuforums.org/showthread.php?t=595064)
One thing that's not mentioned is that you should reboot after step 5. Until I rebooted, I was only getting 2 /dev/ttyUSB devices listed.

Once there, you can then think about using the Vodafone Mobile Connect app.
It doesn't matter if you are not using Vodafone, this application is suitable for any carrier. You just need the access point name and login details (and probably also the DNS servers).

Also, if you are trying to use the Vodafone Mobile Connect application, you'll need to also install all of the python-twisted packages and associated dependences
 
You should do this BEFORE trying to install the vodafone-mobile-connect-card-driver-for-linux_1.99.xx_i386.deb file (this version I mention is the current one that I have successfully installed and am using while away from the office).

If you have already installed the Vodafone app, then the following code should be the complete list of python packages related to the install. If you still get errors from apt then add the requested package names to the command.

```
sudo apt-get install python2.4 python2.4-minimal python-twisted python-crypto python-pysqlite2 python-serial python-twisted-bin python-zopeinterface python-twisted-core python-twisted-conch python-twisted-mail python-twisted-web python-twisted-names python-twisted-news python-twisted-runner python-twisted-lore python-twisted-words python-tz
```

Then download the .deb file from: [https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Install it using
```
sudo dpkg -i {downloaded package name}
```

Once downloaded, you should see the app listed in the Applications>Internet menu.
On first start, you'll be asked to setup a profile, this is different depending on your carrier.

**28 Apr 2008: 2 Issues & Workarounds found with further use:**
1. Clicking on the "connect" button has no effect (ie, no progress bar), solved by launching the client with ```
sudo vodafone-mobile-connect-card-driver-for-linux
```
2. Having a VPN manager sometimes modifies & changes the permissions on /etc/ppp/chap-secrets (seen by a dialog box appearing when launching the vodafone-mobile-connect-card-driver-for-linux), solved by resetting the permissions before launching the client```
sudo chmod 660 /etc/ppp/chap-secrets
```

---

### Post by anatol_w on 2008-04-16
i'm using the app from the betavine crew and everything seems to be working out fine
check if you have the right numbers and names filled in for your provider (DNS and APN host)
you should use static nameservers and let it manage the /etc/ppp/.. stuff.
however i'm still looking for a solution to use the sim card for sms directly and can't figure out how to access the device itself without the use of the vodafone app (wich is quite crappy for sms use)
hints anyone?!

---

