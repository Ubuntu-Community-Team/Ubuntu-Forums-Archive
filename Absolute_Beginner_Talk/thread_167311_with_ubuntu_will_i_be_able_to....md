---
title: "with ubuntu will i be able to..."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by a_0000 on 2006-04-28
... go online with my USB wireless adaptor?? :confused:  PLEASE READ ON :( 

**i dont know how to install software or drivers if i am not online**

i have downloaded the 5.10 DVD and 6.06 CD and both have not detected my USB WiFi card, so I did some research all yesterday on the net and through the forums here on ubuntu and realised I need to install specific drivers. I am not a complete and total newbie but i AM a newbie and I realllly want to make the jump to linux->ubuntu and leave my spyware filled XP in the trash for good.

My WiFi USB adaptor: **3CRUSB10075** (3Com® OfficeConnect® Wireless 54Mbps 11g Compact USB Adapter)
Official drivers: [http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3CRUSB10075&order=desc](http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3CRUSB10075&order=desc)
Unofficial drivers: [http://zd1211.ath.cx/](http://zd1211.ath.cx/)

now i thought using the unofficial drivers would be better cos they are newer than 3com's one, but either way both need to be installed in the same way and that's where I am getting stuck, here are the instructions:

```

Installation ¶

    * Make sure you have your kernel sources in /usr/src/linux
    * Make sure your kernel is compiled with wireless extensions (CONFIG_NET_WIRELESS) and USB support
    * Make sure iwconfig is installed (Debian: wireless-tools package) 

    * Download latest drivers 

    * untar, make, make install
    * modprobe -v zd1211
    * lsmod - you should see zd1211 loaded (see dmesg otherwise)
    * ifconfig wlan0 up (iwconfig will not work otherwise)
    * iwconfig wlan0 essid youressid
    * dhclient wlan0 (or ifconfig.../route... for static IP) - use dhcpd or pump if your distribution does not feature dhclient 

    * With Debian you can optionally use zd1211-firmware and zd1211-source packages. 

```

I tried to use these instructions, i booted up with Dapper Drake in LIVE CD MODE and accessed my external USB drive where i had copied the downloaded drivers to, i tried to follow the instructions but terminal kept saying bad command when typing: "make", "makefile", etc... I can't use the debian method of install because i am not online yet.

can anybody tell me how i can "manually" install the driver so that i can get online then afterwards i can use apt-get properly... i would really appreciate step-by-step instructions so i can print them out on paper then reboot to the live CD and try it out... thank you for reading!

---

### Post by TrendyDark on 2006-04-28
You may be able to install them using the ndiswrapper utility that you can easily install via Synaptic. Then just use this tutorial:

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by trent dillman on 2006-04-28
You should install the build-essential and linux-headers packages. Try downloading them from packages.ubuntu.com. The linux-headers package should be the same version as your kernel. Be sure to get the dependencies for each package as well. When you bring the files to Ubuntu, you can install them with dpkg:
```
sudo dpkg -i package-name.deb
```

Just install each of them that way. If it errors, check the error for dependencies. Use dpkg to install them as well...

Of course, you could also try downloading the Debian packages with the drivers and using dpkg to install those...not to mention, I see the zd1211-source package in the repositories (for Dapper, anyways)....

---

### Post by Sef on 2006-04-28
> * untar, make, make install

You are being required to compile the drivers. 

To compile, build-essential needs to be installed.

Open the terminal (Applications > Accessories > Terminal)

First type this command:

sudo apt-get update

After it finishes updating, to get build-essential, type this command:

sudo apt-get install build-essential

Then on how to compile, read this tutorial:

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

### Post by a_0000 on 2006-04-28
Thanks...

How do i check what version my kernel is when I am booted in ubuntu?

---

### Post by Rinzwind on 2006-04-28
[QUOTE=a_0000]Thanks...

How do i check what version my kernel is when I am booted in ubuntu?[/QUOTE]
uname -a 

(IIRC (doing it from my memory)).

---

### Post by gr0kzer0 on 2006-04-28
> How do i check what version my kernel is when I am booted in ubuntu?

In a terminal type "uname -r" (without the inverted commas)

---

