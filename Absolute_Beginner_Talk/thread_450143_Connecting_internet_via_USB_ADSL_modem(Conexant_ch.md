---
title: "Connecting internet via USB ADSL modem(Conexant chipset) on Ubuntu 7.04 Feisty Fawn"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Felcon on 2007-05-21
Hi...

I've just installed ubuntu 7.04 and now trying to get my internet connection up and running. I'm using an conexant AccessRunner USB ADSL modem and when I boot up Ubuntu the red light start blinking and stay on..So I knw that my modem is working. Now I'm trying to install an Internet client to connect to the internet but when I try to install rp-pppoe-3.8 I get this message

Quote:
lloyd@Felcon:~/rp-pppoe-3.8$ ./go
Running ./configure...
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Oops! It looks like ./configure failed.
According to the Readme which comes with rp-pppoe-3.8 , I need to have pppd preinstalled. I googled it but couldn't find that package..How could I install it.

I'm really interested in using ubuntu and learn it..But without internet I can't do anything..So can you please help me with this problem.. Since I'm a newbie I appreciate if you can give me step-by-step instructions..tnkz..

---

### Post by jiminycricket on 2007-05-21
[http://www.mbeaton.id.au/debian/debian-7.html](http://www.mbeaton.id.au/debian/debian-7.html)

This has some info on installing pppoe.  You will need to download the packages ([pppoe]("http://packages.ubuntu.com/feisty/net/pppoeconf") and [pppoeconf]("http://packages.ubuntu.com/feisty/net/pppoeconf")) on your other OS or computer first, then transfer and install them (sudo dpkg -i namesofPackages)

rppoe is also available as a Debian package: [http://packages.ubuntu.com/feisty/source/rp-pppoe](http://packages.ubuntu.com/feisty/source/rp-pppoe)

You shouldn't need to configure programs that are in Ubuntu repositories, since you can download them as .deb files offline too in cases like this.  Anyways, the compile failed because you needed to install a metapackage called build-essential before doing ./configure.

---

### Post by Felcon on 2007-05-21
Thanks JiminiCricket.. 
                             I installed build-essential package and was successful installing rp-pppoe-3.8..But When configuring it asks what is my interface eth0 or eth1..  Since I have a USB modem I think I can't enter eth0 or eth1 there cuz they are ethernet   interfaces and there is no option for USB.. I think I have to change some files like /etc/network/interfaces, but have no clear idea abt what they are and what i should do ..  My ISP's network is a pppoe .. So can you again help me with this please..

many thnkz...

---

### Post by lohan on 2007-05-22
I too have a similar problem. I have a USB modem but when I try to cinnect using the conventional method it detects only the ethernet interface. How should I get my USB modem working. Is there an online guide for USB modems?

---

