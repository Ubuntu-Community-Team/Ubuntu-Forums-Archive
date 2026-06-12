---
title: "Ubuntu Server"
date: 2011-08-09
forum: Apple Hardware Users
---

### Post by Bioinformaticist on 2011-08-09
Hello,
I am new to Linux. I have just purchased Apple MACPRO with 12 core, 32 GB RAM, 2TB hard drive, MAC OS Lion installed. I want to install Linux server on this machine.And can I run both MAC OS Lion and Linux Server side by side ?
Can anybody guide me how to install Linux server on this MACPRO. 
Any help Appreciated.
Thank you.

---

### Post by Lasastard on 2011-08-10
A fellow bioinformatician, how nice :)

Anyway: [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

This answers your general question, I think. However, since I have just done what you asked with my Mac Pro, one word of advice:

Use the latest version of Ubuntu server, to ensure that you get support for e.g. the blutooth mouse and other hardware. Make sure you have a wired mouse in reach, because the Blutooth one won't run until all drivers are installed. The pin code for pairing it with your mac is '0000' (you'll know what I am talking about once you get to that point).

As for dual booting - that is of course possible (see guide above) - but if you are running a raid array, then it seems difficult at best to run two OSs off that. Bootcamp won't be able to create a DOS partition on a raid array, but if you e.g. run the two operating systems off different drives, you should be fine (or if you only have a single drive without mirror).

Good luck!

---

### Post by Lasastard on 2011-08-10
This guide is even more appropriate because it specifically discusses strategies for dual booting (I chose to run only Ubuntu - not much under OSX I can't get on Ubuntu while avoiding many compilation troubles + apt-get > OSX any day)

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by Bioinformaticist on 2011-08-10
Thanks for your reply.

I want to install Bio-Linux that is built on Ubuntu Linux 10.04 base. Do I need to install any driver manually ?

If I make dual boot OS X Lion and Bio-Linux which way I can get better performance ?
Is VMware Fusion solution for this ? But it wont allow guest OS to use most CPU power.
 
I will be using Bio-Linux most time then OS X Lion.

Thanks again..

---

