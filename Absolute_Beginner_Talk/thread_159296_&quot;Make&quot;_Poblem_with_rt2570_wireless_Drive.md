---
title: "&quot;Make&quot; Poblem with rt2570 wireless Drivers"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by mantrasu on 2006-04-12
Hello, I am trying to install my DLINK Wireless Adapter USB device (DWL-G122 H/W ver::B1 F/W Ver.:2.02) and have been encountering a problem. It appears that I have to compile the driver to work on my system.

I have a Pentium 3 733 MHz, 256 MB RAM, Kubuntu Breezy Badger, on a Dell Dimension 4100.
```
"uname -a" says:
Linux SethKubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
```

I have been following the guides listed below:
[https://wiki.ubuntu.com/WifiDocs/Device/DWL-G122_(Rev_B](https://wiki.ubuntu.com/WifiDocs/Device/DWL-G122_(Rev_B))
[http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
[http://rt2x00.serialmonkey.com/wiki/index.php/Mandrake_10_rt2570_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Mandrake_10_rt2570_Howto)


When I go to "make" the untarred files, it produces the following error messages:

```
sethman@SethKubuntu:~/rt2570-cvs-2006041119/Module$ sudo make
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

```

I got the file from : [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
It said that there was no file when I entered ./configure in the untarred folder  . The error msg was:
```
root@SethKubuntu:/home/sethman/rt2570-cvs-2006041119/Module# ./Configure
bash: ./Configure: No such file or directory
```

In the first guide, it says to "Please make sure you have the appropriate Kernel-Headers and GCC in place.." I do not know if I have done this. I did a search and read some wiki and this was one thing I found:
	sudo aptitude install build-essential
It did not work; same messages.  I also found and tried these commands:

```
sudo apt-get update
 sudo apt-get install build-essential
 sudo apt-get install kernel-package
 sudo apt-get install gcc
 sudo apt-get install gcc-3.4 (this is required only for Breezy users)
 sudo apt-get install libncurses5
 sudo apt-get install libncurses5-dev
 sudo apt-get install libqt3-mt-dev 
```

Same result, same errors. I do not know where to look next, besides here for help.  :confused: 

Also, I read about network-admin in some documentation. I have not been able to find network-admin, the GUI Network Tool, in Kubuntu. Is it only for GNOME environment? Is there a similar utility to network-admin in the KDE environment?

Thank you for any help.

mantrasu

---

### Post by angkor on 2006-04-12
[quote=mantrasu]n the first guide, it says to "Please make sure you have the appropriate Kernel-Headers and GCC in place.." I do not know if I have done this.[/quote]

If you're not sure you can check if the kernel-headers are installed with:

```
apt-cache policy linux-kernel-headers
```

and install them with:

```
sudo apt-get install linux-kernel-headers
```

You can also do a search in synaptic for 'kernel-headers'

Don't know if this will solve your problem though, because I have no experience with wireless. Good luck!

---

### Post by mantrasu on 2006-04-12
Hello angkor,

Thank you for the reply. I tried what you suggested and this is the results:

```

root@SethKubuntu:/home/sethman/rt2570-cvs-2006041119/Module# apt-cache policy linux-kernel-headers
linux-kernel-headers:
  Installed: 2.6.11.2-0ubuntu13
  Candidate: 2.6.11.2-0ubuntu13
  Version table:
 *** 2.6.11.2-0ubuntu13 0
        500 cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
        500 http://us.archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status

```

It looks like they are installed. The more I look at the problem, the more I am wondering about the ./configure file. I have not compiled source code under Linux before. Is the ./configure file necessary to do this? The tutorials don't mention it, they just say to use "make" command, and the ./configure file is not included with the source code (I have untarred it a couple times), but when I look at other wiki about compiling drivers, they all seem to mention the /.configure file.

Thank you for your time,
mantrasu

---

### Post by dante.regis on 2006-04-14
Hi,

I'm having problems with DWL-G122 too. I have also tried to install rt2570 with no sucess. My problem was at other point, but I have found a page that might help you: [http://www.ubuntuforums.org/showthread.php?t=106846&highlight=2500]("http://www.ubuntuforums.org/showthread.php?t=106846&highlight=2500").

It is an interesting thread, though I could not make my wlan work. The system recognizes the card, my iwconfig output is:

```

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:xxxxxxx
          Mode:Managed  Channel=0  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but I just can't "sudo ifup eth1". It says it is already configured. But ifconfig doesn't shows it up. Well, if you get any luck, give me a word, and I'll try here.

Thanks,
Dante

---

### Post by mantrasu on 2006-04-15
Hello dante.regis,

Thank you for your reply and the url. I am still having problems getting my driver to "make". I am beginning to wonder if I can compile anything. You have a DLINK DWL-G122 H/W ver.:B1, not ver.:A1, correct? It appears that the two have different chipsets, so it was just something I wanted to check on with you. 
If you have a similar computer to mine, a Pentium 3, 733 MHz, 256 MB RAM, Kubuntu Breezy Badger, 5.10, 2.6.12-9-386, (hope those are all the needed numbers), would you be willing to compile the driver for me and attach it to a post or email it to me at [email]yonnagrun37@yahoo.com[/email]? If you could, it would be greatly appreciated. Then I can maybe get further into the installation and see if anything pops up that I might be able to help you on too.


I posted this message in a different thread ([http://ubuntuforums.org/showthread.php?t=159857](http://ubuntuforums.org/showthread.php?t=159857)), hoping to get more attention, but have gotten no replies, so I will post it here too, in hopes of someone addressing the issue. If feel kind of sunk right now. The post said:

I went onto IRC and got some help, but the person left before the problem was fixed. I was messing around with "/lib/modules/2.6.12-9-386/build" and "/usr/src/linux-source-2.6.12". I untarred "/usr/src/linux-source-2.6.12" and then made "/lib/modules/2.6.12-9-386/build" a soft link to "/usr/src/linux-source-2.6.12", which was what the person who was helping me thought might work, but then left before I tested it. Before, "/lib/modules/2.6.12-9-386/build" was just an empty folder.
Here are the commands he/she had me use:

```

cd /usr/src tar -jxvf linux-source-2.6.12.tar.bz2 
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux 

ls -ld /lib/modules/2.6.12-9-386/build 
rm -rf /lib/modules/2.6.12-9-386/build 
ln -s /usr/src/linux-source-2.6.12 /lib/modules/2.6.12-9-386/build

```

It got rid of the first set of errors and now generates thousands of errors, but it does look like" make" is doing something this time. Here is the end of the error messages it generated:

```

{standard input}:3939: Error: symbol `security' is already defined
{standard input}:3969: Error: symbol `data' is already defined
{standard input}:4069: Error: symbol `destructor' is already defined
{standard input}:4075: Error: symbol `open' is already defined
{standard input}:4093: Error: symbol `poll' is already defined
{standard input}:4195: Error: symbol `dev' is already defined
{standard input}:4219: Error: symbol `func' is already defined
{standard input}:4225: Error: symbol `data' is already defined
{standard input}:4297: Error: symbol `driver' is already defined
{standard input}:4303: Error: symbol `version' is already defined
{standard input}:4368: Error: symbol `data' is already defined
{standard input}:4374: Error: symbol `version' is already defined
{standard input}:4386: Error: symbol `data' is already defined
{standard input}:4602: Error: symbol `reserved' is already defined
{standard input}:5069: Error: symbol `nlink' is already defined
{standard input}:5075: Error: symbol `size' is already defined
{standard input}:5099: Error: symbol `owner' is already defined
{standard input}:5105: Error: symbol `next' is already defined
{standard input}:5111: Error: symbol `parent' is already defined
{standard input}:5123: Error: symbol `data' is already defined
{standard input}:5435: Error: symbol `release' is already defined
{standard input}:5459: Error: symbol `dev' is already defined
{standard input}:5543: Error: symbol `context' is already defined
{standard input}:5549: Error: symbol `complete' is already defined
{standard input}:5561: Error: symbol `pipe' is already defined
{standard input}:5591: Error: symbol `complete' is already defined
{standard input}:5627: Error: symbol `u' is already defined
{standard input}:6659: Error: symbol `KeyMaterial' is already defined
{standard input}:6719: Error: symbol `Ssid' is already defined
{standard input}:6773: Error: symbol `Bssid' is already defined
{standard input}:6851: Error: symbol `data' is already defined
{standard input}:7402: Error: symbol `Bssid' is already defined
{standard input}:7534: Error: symbol `Ssid' is already defined
/home/sethman/rt2570-cvs-2006041119/Module/rt2570sw.h:1510: error: storage size of `iw_stats' isn't known
/home/sethman/rt2570-cvs-2006041119/Module/rt2570sw.h:1571: error: storage size of `SendTxWaitQueue' isn't known
{standard input}:8097: Error: symbol `KeyLength' is already defined
{standard input}:8163: Error: symbol `Len' is already defined
{standard input}:8523: Error: symbol `BSSID' is already defined
{standard input}:8613: Error: symbol `WirelessPacket' is already defined
{standard input}:9015: Error: symbol `Key' is already defined
{standard input}:9063: Error: symbol `SupportedRates' is already defined
{standard input}:9537: Error: symbol `AvgRssi' is already defined
{standard input}:10076: Error: symbol `next' is already defined
{standard input}:10454: Error: symbol `next' is already defined
{standard input}:10472: Error: symbol `head' is already defined
{standard input}:10478: Error: symbol `tail' is already defined
{standard input}:10496: Error: symbol `head' is already defined
{standard input}:10502: Error: symbol `tail' is already defined
{standard input}:10520: Error: symbol `head' is already defined
{standard input}:10526: Error: symbol `tail' is already defined
{standard input}:11646: Error: symbol `Input' is already defined
{standard input}:11658: Error: symbol `data' is already defined
{standard input}:11712: Error: symbol `signal' is already defined
make[2]: *** [/home/sethman/rt2570-cvs-2006041119/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/sethman/rt2570-cvs-2006041119/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
rt2570.ko failed to build!
make: *** [module] Error 1

```


Any suggestions/corrections you can give me about how to fix this or what "/lib/modules/2.6.12-9-386/build" should really be (a folder with contents or a soft link) or what to look into next?


Thanks for any help,

mantrasu

---

### Post by dante.regis on 2006-04-23
hey mantrasu, I was travelling on business this week, could not read you (since I got no wifi on the laptop). I wish I could compile it to you, but I am using Ubuntu Dapper, with kernel 2.6.15-20, i don't know if it will work. I can try anyway. 

My computer is a Satellite laptop, Pent IV, 512MB ram, Ubuntu Dapper Drake 6.06, kernel 2.6.15-20 386. I could not make it work in Breezy, only could see the interface on iwconfig with Dapper Drake. Don't know if it would be good to you, since it is still beta.

Hoping to help.

---

