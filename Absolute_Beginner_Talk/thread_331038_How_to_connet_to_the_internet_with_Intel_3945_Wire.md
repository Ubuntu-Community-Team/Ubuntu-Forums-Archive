---
title: "How to connet to the internet with Intel 3945 Wireless Card?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by supremo13 on 2007-01-04
I am absolutely new to Linux.  I have installed Ubuntu 6.06.  But I do not know how to get my card connected to the internet.  I have looked at this web page [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) but I do know know what exactly to type when installing anything.  If someone could walk me through it or type out what exactly I need to type out in the console then that would be great.  Thank you.

Matthew
[email]supremo13@gmail.com[/email]]

---

### Post by riven0 on 2007-01-04
Okay, first, can you give me the output of this command?:

> iwconfig

---

### Post by supremo13 on 2007-01-04
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0

sit0      no wireless extensions.

---

### Post by riven0 on 2007-01-04
It looks like your card is not detected. Try to install the driver from Debian. Open the terminal and copy and paste these lines one at a time:

> wget [http://http.us.debian.org/debian/pool/contrib/i/ipw3945/ipw3945-source_1.1.2-6_all.deb](http://http.us.debian.org/debian/pool/contrib/i/ipw3945/ipw3945-source_1.1.2-6_all.deb)

> cd Desktop

> sudo dpkg -i ipw3945-source_1.1.2-6_all.deb

> sudo apt-get update && sudo apt-get install network-manager

If there are no errors, then reboot...

---

### Post by supremo13 on 2007-01-04
I am not connected to the internet at all on the Ubuntu computer.  It is on this computer that I am using with Windows and I only have a wireless connection.  But I did download the IPW3945 package from Debian and put it on my thumb drive and copied it to my desktop in Ubuntu.  But I got errors.  Here they are:

supremo@supremo-laptop:~$ cd Desktop
supremo@supremo-laptop:~/Desktop$ sudo dpkg -i ipw3945-source_1.1.2-6_all.deb
Password:
Selecting previously deselected package ipw3945-source.
(Reading database ... 69971 files and directories currently installed.)
Unpacking ipw3945-source (from ipw3945-source_1.1.2-6_all.deb) ...
dpkg: dependency problems prevent configuration of ipw3945-source:
 ipw3945-source depends on debhelper (>= 5); however:
  Package debhelper is not installed.
 ipw3945-source depends on dpatch; however:
  Package dpatch is not installed.
 ipw3945-source depends on module-assistant; however:
  Package module-assistant is not installed.
 ipw3945-source depends on make; however:
  Package make is not installed.
dpkg: error processing ipw3945-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ipw3945-source

---

### Post by riven0 on 2007-01-04
Alright, since you don't have a wired connection, this will be tough. We'll have to manually download all the dependencies. So when you're on Windows, download these files:

[http://mirrors.kernel.org/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/m/make-dfsg/make_3.81-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/make-dfsg/make_3.81-2_i386.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12_i386.deb)


[http://http.us.debian.org/debian/pool/main/d/debhelper/debhelper_5.0.42_all.deb](http://http.us.debian.org/debian/pool/main/d/debhelper/debhelper_5.0.42_all.deb)

[http://http.us.debian.org/debian/pool/main/d/dpatch/dpatch_2.0.21_all.deb](http://http.us.debian.org/debian/pool/main/d/dpatch/dpatch_2.0.21_all.deb)

[http://http.us.debian.org/debian/pool/main/m/module-assistant/module-assistant_0.10.8_all.deb](http://http.us.debian.org/debian/pool/main/m/module-assistant/module-assistant_0.10.8_all.deb)

Try installing the packages in the same order. If you double-click on them, you should be able to install them. Post any other dependency errors here. If no errors, then try installing the ipw3945 driver again.

---

### Post by crackling on 2007-01-04
I couldn't get my wireless working either. I fixed it by installing network-manager-gnome via Synaptics Package Manager.

System > Administration > Synaptics Package Manager > search for network-manager-gnome > check the box > apply

I don't remember if a restart is required.

---

### Post by supremo13 on 2007-01-05
I was able to install the module-assistant_0.10.8_all.deb, make_3.81-2_i386.deb, libc6_2.4-1ubuntu12_i386.deb, AND dpatch_2.0.21_all.deb.  But the rest gave me a dependency error.  Do you need to see what the error looks like?

---

### Post by supremo13 on 2007-01-05
bump

---

### Post by Bachstelze on 2007-01-05
Why the hell do you want to install the drivers ? Your card is detected since it appears in iwconfig. All you have to do is setup the connection, for example :

```
sudo iwconfig eth1 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient eth1
```

---

### Post by supremo13 on 2007-01-05
Thanks I'll try it out.

---

