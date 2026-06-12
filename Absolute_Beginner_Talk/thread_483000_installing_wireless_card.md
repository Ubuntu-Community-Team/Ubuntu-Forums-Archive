---
title: "installing wireless card"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by brownietodd on 2007-06-24
Ok ..hi guys.. Ive had a look in the forums and there is some info there but Im newer than new when it comes to linux... I have a netgear wg511 v2 wireless card... now I've spent a better part of 6hrs trying to get ubuntu to work with this card... I've been through the help docs and tried things within the terminal  ...no idea... and it still means very little to me.

any one that can help in simple terms willbe in my gratitude for life.

Todd

---

### Post by chamberlain2006 on 2007-06-24
Hi there.  From what I see, your card will need to be installed using a utility called "ndiswrapper".  Can you please post the output of "lspci" in terminal.

---

### Post by kevdog on 2007-06-24
Read this....[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
I know it seems technical, however you will learn a lot a probably understand it.

Begin at the section Install Windows Driver, second paragraph.

---

### Post by brownietodd on 2007-06-24
ok which part of the output

---

### Post by mattg89 on 2007-06-24
> **brownietodd said:**
> ok which part of the output

All of it would be useful.

---

### Post by brownietodd on 2007-06-24
0002:00.0 Ethernet controller: Marvell Technology Group LTD 88w8335 [libertas] 802.11b/g Wireless (rev 03)

---

### Post by chamberlain2006 on 2007-06-24
There should be a line about "ethernet controller" or "network controller".  Any of them that have to with that I will want to see, thanks.

---

### Post by brownietodd on 2007-06-24
0002:00.0 Ethernet controller: Marvell Technology Group LTD 88w8335 [libertas] 802.11b/g Wireless (rev 03)

---

### Post by chamberlain2006 on 2007-06-24
Perfect.  Do you have a wired internet connection right now?

---

### Post by brownietodd on 2007-06-24
I'll move my operations over to the modem... see you in a minute

---

### Post by brownietodd on 2007-06-24
ok I'm getting out onto the net

---

### Post by chamberlain2006 on 2007-06-24
Ok.  Type these commands into the terminal exactly.

```

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
wget http://matt-chamberlain-go.ath.cx/WG511v2.INF
wget http://matt-chamberlain-go.ath.cx/WG511v2.cat
wget http://matt-chamberlain-go.ath.cx/WG511v2.sys
sudo ndiswrapper -i WG511v2.INF
sudo ndiswrapper -l
##That last command should show that the driver was installed and hardware was installed##
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo iwconfig
##Should show wlan0##
sudo iwconfig wlan0 essid "YOURNETWORKNAME"
sudo ifdown wlan0
sudo ifup wlan0

```

And you should be good to go.  Let me know!

---

### Post by brownietodd on 2007-06-24
hey Matt comes up after each command as an error

---

### Post by chamberlain2006 on 2007-06-24
Pardon?  I don't understand.

---

### Post by brownietodd on 2007-06-24
comes up as error 404 :not found ... for the .inf file

---

### Post by chamberlain2006 on 2007-06-24
It's case-sensitive.  So wg511v2.inf isn't the same as WG511v2.INF.  Make sure you type is EXACTLY like you see it.

---

### Post by brownietodd on 2007-06-24
exactly all the others worked... just the .inf file not found

---

### Post by brownietodd on 2007-06-24
seen the mistake...sorry

---

### Post by brownietodd on 2007-06-24
Matt it keeps telling me command not found when i do this line ...sudo ndiswrapper -i WG511v2.INF

---

### Post by chamberlain2006 on 2007-06-24
Have you done "sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common"?  Did it run without errors?  Did you type it properly?

---

### Post by brownietodd on 2007-06-24
E: couldn't find package ndiswrapper-utils-1.9

I need the disc in????

---

### Post by chamberlain2006 on 2007-06-24
Ahhh.  Your problem is (I think) that you don't have the repos enabled.  Type "gksudo gedit /etc/apt/sources.list" and delete the #'s from in front of any of the lines starting with deb or deb-src.

So,

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
would become
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

Then, when you're done, go back to terminal, type "sudo apt-get update" and then try again.

---

### Post by brownietodd on 2007-06-24
ok Im down to  iwconfig and it says    error for wireless request "set essid" (8b1a):  set failed on device wlan; no such device

---

### Post by chamberlain2006 on 2007-06-24
Do you mean "wlan0"?  Did it show up when you just typed iwconfig?

---

### Post by brownietodd on 2007-06-24
no it didn't      it came up as       lo                no wireless extensions
                                                   eth0           no wireless extensions

---

### Post by chamberlain2006 on 2007-06-24
What is the output of ndiswrapper -l?

---

### Post by brownietodd on 2007-06-24
Matt its 2am here and I have to go to bed I start work at 6am and i've already been up for 20 hrs today... so I might say good night and thank you for your help so far and I'll try again in the morning when i get to work. have a good one Matt.
Todd

---

### Post by chamberlain2006 on 2007-06-24
Ahh I'll talk to you later then.

---

### Post by brownietodd on 2007-06-24
ok matt here goes

install/manage windows drivers for ndiswrapper


usage :  ndiswrapper OPTION

-i infile                    install driver described by infile
-a devid driver       use installed driver for devid
-r driver                 remove driver
-l                            list installed drivers
-m                          write config.. for modprobe
-ma                        write module alias  config.. for all devices
-mi                         write module install  config.. for all devices
-v                          report version information


where devid is either PCIID or USBID of the form xxxx:xxxx,
as reported by 'lspci -n' or 'lsusb' for the card     
todd@todd-laptop:~$

---

### Post by chamberlain2006 on 2007-06-27
You forgot the "-l" switch at the end.  Please post the output of "ndiswrapper -l"

---

### Post by brownietodd on 2007-06-27
todd@todd-laptop:~$ sudo ndiswrapper -l
autorun : invalid driver!
wg511v2 : invalid driver!
todd@todd-laptop:~$

---

### Post by chamberlain2006 on 2007-06-27
You seem to have an "autorun" driver.  Don't know what's with that.  Please do this:

sudo ndiswrapper -r autorun
sudo ndiswrapper -r wg511v2

and then re-add the wg511v2 driver.  Make sure that you have the .inf and the .sys files in the same directory.

sudo ndiswrapper -i WG511v2.INF

---

### Post by chamberlain2006 on 2007-06-28
Hi.  Someone asked me to post the drivers, so here they are.

---

### Post by noobonastick on 2007-06-29
Thank You Heaps xD

---

### Post by brownietodd on 2007-06-29
hey Matt how was your week??

---

### Post by brownietodd on 2007-06-29
Matt, Here is what I've just done...


todd@todd-laptop:~$ sudo ndiswrapper -r autorun
Password:
todd@todd-laptop:~$ sudo ndiswrapper -r wg511v2
todd@todd-laptop:~$ sudo ndiswrapper -i WG511v2.INF
installing wg511v2 ...
couldn't open WG511v2.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
todd@todd-laptop:~$ 


Todd

---

### Post by brownietodd on 2007-06-29
Just redone it...

todd@todd-laptop:~$ sudo ndiswrapper -r autorun
Password:
todd@todd-laptop:~$ sudo ndiswrapper -r wg511v2
todd@todd-laptop:~$ sudo ndiswrapper -i WG511v2.INF
installing wg511v2 ...
couldn't open WG511v2.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
todd@todd-laptop:~$ sudo ndiswrapper -i WG511v2.INF
driver wg511v2 is already installed
todd@todd-laptop:~$

---

### Post by brownietodd on 2007-06-29
todd@todd-laptop:~$ sudo ndiswrapper -iWG511v2.INF
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
todd@todd-laptop:~$

---

### Post by brownietodd on 2007-06-29
todd@todd-laptop:~$  sudo ndiswrapper -i WG511v2.INF
driver wg511v2 is already installed
todd@todd-laptop:~$

---

### Post by brownietodd on 2007-06-29
ok.. just rebooted but it still didn't see the card

---

### Post by brownietodd on 2007-06-29
network manager that is

---

### Post by brownietodd on 2007-06-29
The hardware device manager can see it and list its driver

---

### Post by chamberlain2006 on 2007-06-29
NetworkManager is known to have problems.  Try going to System>Administration>Network to configure it.

---

### Post by chamberlain2006 on 2007-06-29
Ok, glad to see you're having success.  Todd (I think that's your name), how about the output from ndiswrapper -l now.  Also, are you sure that you have the INF file in the directory and that you're spelling it right?

---

### Post by brownietodd on 2007-06-29
Morning Matt, system>admin>Network still doesn't see it.

Todd

---

### Post by brownietodd on 2007-06-29
todd@todd-laptop:~$ sudo ndiswrapper -l
Password:
wg511v2 : invalid driver!
todd@todd-laptop:~$

---

### Post by brownietodd on 2007-06-29
todd@todd-laptop:~$ ndiswrapper l
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
todd@todd-laptop:~$

---

### Post by brownietodd on 2007-06-29
todd@todd-laptop:~$ sudo ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
todd@todd-laptop:~$

---

### Post by chamberlain2006 on 2007-06-30
Hmmmm, do you have the ndiswrapper-utils-1.9 package installed?

---

### Post by brownietodd on 2007-06-30
Matt, how do I find out if its installed??

Todd

---

### Post by kevdog on 2007-06-30
Type the following at command line:
sudo aptitude install ndiswrapper-utils-1.9

---

### Post by Antonio44 on 2007-06-30
Just letting you know that I am rooting for you. I switched one of my computers to Mint just because of this card. I hope you get it to work!


A.

---

### Post by chamberlain2006 on 2007-06-30
Yupp.  sudo apt-get install ndiswrapper-utils-1.9 **OR** sudo aptitude install ndiswrapper-utils-1.9, whichever.

---

### Post by brownietodd on 2007-06-30
todd@todd-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
todd@todd-laptop:~$

---

### Post by chamberlain2006 on 2007-06-30
Hmmmm.  Try ndiswrapper -v again.

---

### Post by kevdog on 2007-06-30
If the version still comes back Error no utils version found or something similar then you are going to have to install ndiswrapper from source.  That's what I always recommend anyway!

---

### Post by chamberlain2006 on 2007-06-30
Source is always harder :P, but if it must be done.  I'll just see if something fixed itself somehow.

---

### Post by kevdog on 2007-06-30
Installation of source:

Run following commands
sudo rm -R /etc/ndiswrapper *

Use synaptic to uninstall ndiswrapper

sudo aptitude install build-essential
mkdir ~/ndiswrapper
Download ndiswrapper-1.47 (place in ~/ndiswrapper directory) from: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Check if its installed properly:
ndiswrapper -v

Now was that so hard!!

---

### Post by chamberlain2006 on 2007-06-30
I know how to do it! ;) It's just much harder to explain to people

---

### Post by brownietodd on 2007-06-30
todd@todd-laptop:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
todd@todd-laptop:~$

---

### Post by brownietodd on 2007-06-30
I don't know whats going on???

---

### Post by chamberlain2006 on 2007-06-30
I'm sorry bout that.  I've got to go for now, and tomorrow is Canada Day, so I'll be pretty busy, but I'll be back later.  Sorry to leave you hanging like this.

---

### Post by brownietodd on 2007-06-30
Matt, I'm going to reinstall xp and then put ubuntu into a another drive and we''ll start again??
todd

---

### Post by tracer2009 on 2007-07-06
glad i came across this thread, made my wireless card install a lot easier. i too have a netgear wg511 v2 wireless card on an ibm t21 thinkpad.  this is what i did (from memory!)

doing lspci led me to a similar line as yours - 0002:00.0 Ethernet controller: Marvell Technology Group LTD 88w8335 [libertas] 802.11b/g Wireless (rev 03)

i then downloaded the three files on another pc then transfered them across with a usb stick

i renamed WG511v2.INF to WG511v2.inf so all the file extensions are now lower case . makes no difference i know, especially when using tab to autofill but hey i feel better

i then followed on to the next line :- sudo ndiswrapper -i WG511v2.inf

when i entered this command it gave an error as it was looking for WG511v2XP.sys

so i removed the driver :- sudo -r wg511v2

then renamed the file WG511v2.sys and made it WG511v2XP.sys

then ran ndiswrapper again :- sudo ndiswrapper -i WG511v2.inf

this time it looks better, so i do ndiswrapper -l and all is ok

i then did :- sudo modprobe ndiswrapper

when i entered it went back to the command line.  so i pulled the card out and shoved her back in again and lights started flashing, yey!

i then did a bit of trial and error with the network-admin menu but it only gives option for WEP

i then sussed that there is a config up in the top right hand corner of the screen for wireless which gave me the correct login options i was looking for.

connected straight away.

---

### Post by Count Doofus on 2007-10-21
Lookin' Way too hard ! Type the name of the .INF in the correct case.

 had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !


had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !

todd@todd-laptop:~$ sudo ndiswrapper -i WG511v2.INF
installing wg511v2 ...
couldn't open WG511v2.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

try bla@blabla:~$ sudo ndiswrapper -i wg511v2.INF (or Inf OR INf whatever check the case when the file is listed with the dir command)

open the inf with gedit and check the case there  might not be the same remember you can get downright sloppy in windows.

had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename is wrong !

todd@todd-laptop:~$ sudo ndiswrapper -i WG511v2.INF
installing wg511v2 ...
couldn't open WG511v2.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

try bla@blabla:~$ sudo ndiswrapper -i wg511v2.INF (or Inf OR INf whatever check the case when the file is listed with the dir command)

open the inf with gedit and check the case there might not be the same remember you can get downright sloppy in windows.

had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

