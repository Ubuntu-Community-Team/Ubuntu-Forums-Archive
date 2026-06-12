---
title: "Unsupported scanners"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by paradoc on 2007-06-25
In a previous post, I was advised to go to a French url [http://doc.ubuntu-fr.org/category/scanner/feisty ](http://doc.ubuntu-fr.org/category/scanner/feisty ) (N.B.Aug4-page now removed) to make my N1220U CanoScan useable.The coding was in English, but the instructions were in French. With a bit of help from BabelFish and my schoolboy French, I unravelled the text, > Launching

 (EDIT...)        bash:~$ sudo apt-get install scanbuttond

A couple of the parameters of scanbuttond should be reconfigured before use. These are are the (adjustable) examination timings ...The values are in microseconds: 
  *
 -p, -pollingdelay=DELAY The polling delay (ms), default: 333000 
  *
 -r, -retrydelay=DELAY The retry delay (ms), default: 2000000 

The default parameter -p of 333 milliseconds is the best choice. The parameter -r with a default of 2 seconds, should ideally be shortened for  safety.  (Best choice = 0.5 secs)
 
Thus, before launching xsane or kooka, it is  best to start with with the following setting:

 bash:~$ scanbuttond -r 500000 

(paradoc note: this was as far as I needed to go, as I got my Canon N1220U up and going with kooka, but here's the rest of the translation)

Then, open as normal, xsane or kooka. When done, it is probably best to kill the process 'scanbuttond' to stop it (but this is not obligatory):

 bash:~$ killall scanbuttond 

AUTOMATION BY SCRIPT

To avoid having to carry out all these operations for each scan, you could create a small script in  /usr/local/bin for xsane --replace 'xsane' by 'kooka' as necessary):

 bash:~$ sudo gedit /usr/local/bin/xsane

 And add the following 4 lines:

 #! /bin/sh 
scanbuttond -r 500000
/usr/bin/xsane
killall scanbuttond 

Save and close.  
  Note, You will also have to:

bash:~$ sudo chmod +x /usr/local/bin/xsane 

to make the script work, that's all!

 Each call of xsane ( Applications -> graphics or command line) will launch this small script instead of the program xsane itself. 
  (The sequence /usr/local/bin will have priority over /usr/bin when this program is launched)

 You can modify the above according to your own needs.

  The scanners involved were listed by the source,(in English)> supported scanners
------------------

Supported by the epson backend (via libusb):
* Epson Expression 1600 (expected to work)
* Epson Expression 1680 (expected to work)
* Epson Perfection 610 (expected to work)
* Epson Perfection 636U (expected to work)
* Epson Perfection 640 (expected to work)
* Epson Perfection 1200U (expected to work)
* Epson Perfection 1240 (expected to work)
* Epson Perfection 1640 (expected to work)
* Epson Perfection 1650 (working, tested)
* Epson Perfection 1660 (working, tested)
* Epson Perfection 2400 (working, tested)
* Epson Perfection 2450 (expected to work)
* Epson Perfection 3200 (expected to work)
* Epson CX3200 (working, tested)

Supported by the mustek backend (via libusb):
* Mustek BearPaw 2448TA (experimental)

Supported by the niash backend (via libusb):
* Agfa Snapscan Touch (expected to work)
* HP Scanjet 3300c (expected to work)
* HP Scanjet 3400c (expected to work)
* HP Scanjet 4300c (expected to work)

Supported by the plustek backend (via libusb):
* Canon CanoScan N1220U (expected to work)
* Canon CanoScan D660U (expected to work)
* Canon CanoScan N650U (expected to work)
* Canon CanoScan LiDE 20 (experimental)
* Canon CanoScan LiDE 25 (experimental)
* Canon CanoScan LiDE 30 (experimental)
* Epson Perfection 1260 (experimental)
* Hewlett-Packard ScanJet 2200c (experimental)

Supported by the plustek_umax backend (via libusb):
* UMAX Astra 3400/3450 (experimental)

Supported by the snapscan backend (via libusb):
* Epson Perfection 2480 (expected to work)
* Epson Perfection 2580 (expected to work)
* Epson Perfection 1670 (working, tested)

Note: the mustek, niash, plustek, plustek_umax and snapscan backends were
implemented using information gathered by "sniffing" the communication between
the Windows driver and the scanner, because there is no technical documentation
available for these devices! This means that there may be some weird issues
(e.g. button press events reported twice).

I hope this will help a few owners of unloved scanners, as it did for mine!

---

### Post by Golyadkin on 2007-06-25
There is also an official list here: [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)

---

### Post by paradoc on 2007-06-25
Please add this as intro to the previous post, it refers to the use of SCANBUTTOND and its installation to make the unsupported scanner function properly
     (BabelFish translation)
"scanbuttond is supposed to function on a given list of scanners (Ci after, according to the information provided in file README of scanbuttond). In the case of a scanner requiring a loading of firmware, scanbuttond can also take care some. See also file README of scanbuttond to configure the loading of the firmware of the scanner. Installation The installation of scanbuttond is very simple, this package forms part of the dépot universe. It can be done either via synaptic, or in line of order(command line):"

 bash:~$ sudo apt-get install scanbuttond

---

