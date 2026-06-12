---
title: "Inconsistencies"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by alan_uk on 2007-04-05
I have been trying out Ubuntu on a second PC with a view to using it as my main platform for a couple of weeks.  I bought an excellent introductory book Ubuntu Linux for Non-Geeks by Rickford Grant and installed the accompanying Version 6.04.  A clean install with no problems picking up drivers etc. I soon learn't the basics and feeling more confident I downloaded 6.10 (same architecture) but scrolling down pages was choppy (Graphics problem). I then downloaded the beta version 7.04 and could not get the optimum resolution of 1024 x 768 - only 800 x 600.  Why are differences?

---

### Post by STREETURCHINE on 2007-04-05
i think you will find fiesty 7.04 hasnt been officially released yet, it is still in testing so you must expect a few bugs,if you dont like it wait for the official release or go back to edgy 6.10 or dapper 6.06

---

### Post by gary4gar on 2007-04-05
WHen asking help on forums always give your hardware information or put it in your siggy.

for your problem i think there is something wrong with xorg.config file. post it here
u will find it in /etc directory

---

### Post by alan_uk on 2007-04-05
Thank you for your replies.  The PC I'm testing it on is a cheap package from e-machines. I'm going to spend the time before the official release of fiesty 7.04 getting a good grip on the features and mechanisms of Linux (Ubuntu 6.04).  I'll then install fiesty 7.04 on my main PC which is: 
Processor: AMD ATHLON 64 X2 3800+ 
Motherboard: GIGABYTE M75SLI-S4
Graphics Card: Connect3D X1550 PCIE 512Mb 
PSU: ANTEC TRUEPOWER TRIO 430W ATX PSU
Memory: PNY 512MBx2 DMM DDR2 533Mhz PC4300
Adapter: BT Voyager 1040 PCI

---

### Post by gary4gar on 2007-04-06
hmm...
ATI there, linux does not go with ati so easily, for your graphic problem on fiesty
try [this]("https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/93861")
   Or if u can't go with this then stay with stable versions of ubuntu and wait for official release.

---

### Post by alan_uk on 2007-04-06
In the May 2007 edition of Linux Format Magazine on their DVD there is an ATI driver (graphics driver) included. Would this shell script solve the problem? ati-driver-installer-8.34.8-x86.x86_64.run

---

