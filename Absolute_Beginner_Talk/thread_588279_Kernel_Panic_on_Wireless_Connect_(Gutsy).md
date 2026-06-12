---
title: "Kernel Panic on Wireless Connect (Gutsy)"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by The Rocketeer on 2007-10-23
I did the forum search thing to see if I could find anything similar, but didn't see anything decently new.

Did a clean install (dual boot with Vista) on a Gateway MT3707 laptop (intel dual core processor running 1.6GHz each, 1 GB ram, Realtek 8185 integrated wireless adapter)

Everything runs fine with Gutsy - games, open office, etc and looks beautiful to boot however when I attempt to connect to a (detected) wireless network I get a kernel panic. No dump screen, no nothing. Just locks up.

I have never, ever dealt with Linux before in my life so I am the ultimate noob when it comes to this, but I am determined to have a machine that is completely free of Windows sometime soon. I was thinking of rolling back to Dapper, but when I booted Dapper from the LiveCD, I was able to detect the network (again) but not connect at all.

Do you all think this is a driver problem, or not? What can I do to fix this? Gutsy is useless to me without internet :(

I looked up the Realtek device on a website which says Dapper should provide support out of box...so there shouldn't be a problem...I think.

Thanks in advance!
R

---

### Post by The Rocketeer on 2007-10-23
update:

Went to school and tried a wired connection, and works just fine. Was able to connect on the school's open protocol....wonder if it's a problem with encryption?

---

### Post by OhioYJ on 2007-10-23
What are you using for Wireless drivers?

Ubuntu can detect a wireless card is there by default, but it can't use it, something about license issues. So when you install Ubuntu it sees the wireless and it looks like its installed but you can't use it.

I use bcmfwcutter to correct the wireless issue on my laptop.

---

### Post by The Rocketeer on 2007-10-23
another update:

I am able to get the card working on an open encryption protocol but it keeps tripping on WPA encryption. When I get home from class I'm going to try and change the settings on the router and test WEP encryption as I would prefer not to have an open protocol in the middle of a student ghetto...

---

### Post by Zetheroo on 2007-10-26
Hey ... I have had no end of trouble on 2 of my machines .... all over wireless networking.

On one of the machines it will not ever connect to a WEP encrypted network and will just either freeze up entirely or sit for 10+ minutes trying to connect. It has nothing to do with the Atheros card or driver since I tested out a Netgear PCMCIA card as well on the same machine and it still would not connect to the WEP encrypted wireless network.

On the other machine I can connect to wireless encrypted and non-encrypted networks from fine. However is I attempt to switch between wired and wireless... I get in trouble. Machine freezes solid and I have to power off with the power button. Then when I boot back up I get a Kernel Panic and have to power off and back on AGAIN!... no fun there....

Both machines are no more than a few months old. the first has an Atheros wifi chip and the other an Intel wifi chip. Both are high-end Thinkpads ... and on both Feisty was working well in all these points.

So what up???

---

### Post by fuelvolts on 2007-10-26
I have the same probelm on my Gateway MT 3423 AMD Turion X2 with same wireless card.  It detects my WEP encrypted linksys, but when it tries to connect, it just freeze up and I have to hold down the power button and hard reset.  Glad to know that I am not the only one.

---

### Post by headtowall on 2007-10-26
> **fuelvolts said:**
> I have the same probelm on my Gateway MT 3423 AMD Turion X2 with same wireless card.  It detects my WEP encrypted linksys, but when it tries to connect, it just freeze up and I have to hold down the power button and hard reset.  Glad to know that I am not the only one.

I am really glad to have found you guys.  I'm using a Gateway MT3422.  AMD Athlon x2, nvidia and realtek.  I am having the EXACT same problem.  Is your error message something about the timer not connected?  Error message # 8254.  It says "run with noapic kernel parameter."

Here's the thing, I can't really get this to work.  I was able to get the network manager, (I think that is what it is called), to finally see my wireless connection, but when it connects it freezes up, just like you have stated.

Have you been able to figure out anything with this.  Any help would be super appreciated.  Plus, I would love to help with this too.  I really want to learn more about this, but so far troubleshooting has been really hard for me.

Very very very very new to this.

---

### Post by headtowall on 2007-10-27
Here is a follow up:

I have tried 7 different boot paramters, (iI think that is was it is called), of the 7 that I tried, 3 would boot with no problem, and would see my wireless network.  But all three would hang when logging in to the network.

These are the 3:

noapic nolapic
noapictimer
noapictimer irqpoll

Since the error message that I saw referenced the "noapic kernel parameter" these seemed liked viable options.

(just to summarize the issue again, installed 'Bu 7.10 on Gateway MT3422 as dual boot with Vista Home Premium, AMD 64 Athlon x2, nvidia graphics and Realtek wireless; there has been a kernel panic since installation and gave the error message "MP bios bug: 8254 timer not connected to IO-APIC... try using the 'noapic' kernel parameter; will boot; freezes when connecting to wireless network.)

---

### Post by PreviousN on 2007-10-28
You may want to take a look at this thread:[http://ubuntuforums.org/showthread.php?t=585712](http://ubuntuforums.org/showthread.php?t=585712)

Or...here's the info that helped people before:

"lsmod | grep 8180"
"modprobe -r name of driver from above"

then use NDISwrapper for the driver. I am using a driver(rtl8185) from the Realtek website. Google it or the driver you need and you should be able to find one for your card/chipset.

I'm told the problem is that ubuntu mis -detects the wireless card.

---

### Post by manbou on 2007-10-28
I have the same problem. Tried "modprobe -r" came with error saying device in use or operation not permitted. I have an Airlink wireless card. This is a dual boot system. I know the wireless works because in Windows I can connect.

---

### Post by alan34 on 2007-10-29
Hi all,

I might be able to help those with a rtl8185 chipset.

My card is a Peak pci wireless card with rtl8185 chipset I also had the kernel panic when I tried to connect to my wireless router, really annoyed as the card worked with Edgy and Fiesty.

The solution is to use the Window drivers and ndiswrapper and blacklist the linux r818x driver.

Get the Window files - should have something,inf and something.sys in the same directory. I got net8185.inf and rtl8185.sys from the cd that came with my card.

In System - Administration - Software Sources make sure there is a tick against the Ubuntu 7.10 cd. Load the cd:)
(you may have to untick all the other software sources just note which ones are ticked now!!)

In System - Administration - Synaptic Package Manager search for ndiswrapper and install.

In a terminal change directory to where the Window files are then (in my case)

sudo ndiswrapper -i net8185.inf
sudo depmod -a
sudo modprobe ndiswrapper  
sudo ndiswrapper -m 
sudo ndiswrapper -l  
------------You should see something like this

alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)

Now to load the driver when you boot

sudo gedit /etc/modules
----------You should see something like this add ndiswrapper at the end of  the file

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


Now we blacklist the linux driver

sudo gedit /etc/modprobe.d/blacklist
 ---------------At the end of the file add

# wireless network card driver
blacklist r8180

Reboot and you should be okay well at least I was. Only re-installed three times to get it to work:(

Good luck

---

### Post by manbou on 2007-10-30
I'll try that. Also, did you save the *.inf file to desktop or move it to some other directory.

---

### Post by alan34 on 2007-10-30
You need both the .sys and .inf in the same directory.

In a terminal 

cd

mkdir ndiswraper

Extract your files to ~/ndiswrapper     (~ is your home directory)

cd ndiswrapper

ls -l

should look something like this

alan@alan-desktop:~/ndiswrapper$ ls -l
total 296
-rw-r--r-- 1 alan alan  14276 2005-12-09 07:51 net8185.inf
-rw-r--r-- 1 alan alan 282240 2005-10-20 12:05 rtl8185.sys

Then follow the commands in my first post.

There are many Howtos on ndiswrapper should be one in the Ubuntu help file although the one in Gutsy calls for using a package ndisgtk which is a graphical user interface I am sure this is not on the cd so if you are not on the internet at all you are stuck. Heres a link for you


[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by manbou on 2007-10-30
Thanx. Worked perfectly. Guess drivers were bad. Instructed worked. Ndiswrapper works for airlink model AWLH3028

---

### Post by Rxallen on 2007-10-31
Hello,

I tried to follow your instructions. I get the following...

rxallen@rxallen-ubuntu:~$ sudo ndiswrapper -l
net8185 : invalid Driver!

HP Pavillion zv5000ua
P4(r) 3.00GHz
1128mb RAM
NIC: Realtek RTL8139 Family PCI Fast Ethernet

Duealboot: Ubuntu 7.10 | Win XP Home

Does this mean that I don't have the correct Driver file? I Read in another post that I needed the rtl8185 even if you have an 8139 NIC... Any info would be greatly appreciated!

P.S. Ubuntu: It works well when physical connected to the network, just no wireless. Win XP: Works perfect.

Thanks!

~Rick

---

### Post by alan34 on 2007-10-31
Hi It sounds like you have the wrong driver for your card your driver should be for the rtl8139 card not the rtl8185 which is one I have. I got this driver from the Realtek site

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false)

use Netrtlx.inf instead of net8185.inf as in my first post.

Or use the one on the cd which came with the card - that would be best its the first one I would try

Cheers

Is this your wireless network card or your "cable" network card?

In a terminal

lspci

should look like this

alan@alan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
03:02.0 Communication controller: Agere Systems LT WinModem (rev 02)
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

See the Wireless info at the bottom whatever your output says thats the driver that you need

---

### Post by Rxallen on 2007-10-31
I'm going to try this tonight, Thanks! I'll let you know my results! :-)

---

### Post by Rxallen on 2007-10-31
Ok, tried to install and I get this...



rxallen@rxallen-Ubuntu:~/ndiswrapper$ sudo ndiswrapper -i netrtlx
installing netrtlx ...
couldn't open netrtlx: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.


I checked the directory and the file IS in there... I even tried from the terminal by using DIR and it was seen there as well. I looked at line 181 in the ndiswrapper1.9 and it was just the error message code...

I'm lost!

Any More Hints?

~Rick

---

### Post by alan34 on 2007-11-01
We need to know what hardware you are using. Is this a wireless network pci card or a "cable" network card in other words there is a cable from your pc to a modem then out through the telephone socket.

The rtl8139 drivers from what I found out today are for a "cable" network card not a wireless one so no surprise it has not worked.

Is your wireless device a pci card or a usb device?

Okay then open up a terminal window and for a pci card type

lspci and enter and post the output

And for a wireless usb device type

lsusb and enter and post the output.

I'll do my best for you but I need to know what card you have before we can get any further. Good luck.

Sometimes getting a wireless connection on a unsupported card is just not worth the hassle for a few pounds/dollars buy one that is supported.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Rxallen on 2007-11-02
I'm out of town the the weekend so I'll respond on Monday. thanks for you help thus-far. Thanks!

---

### Post by Rxallen on 2007-11-02
rxallen@rxallen-Ubuntu:~$ lspci

00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)

00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)

00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16)

00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c

00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)

01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)

02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)

02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

02:07.0 USB Controller: NEC Corporation USB (rev 43)

02:07.1 USB Controller: NEC Corporation USB (rev 43)

02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)


I lied, I was able to get to the internet...

Thanks!

---

### Post by getaboat on 2007-12-06
Having install gutsy on my sons dual boot PC it was shame that wireless would not work with the realtek 8185 pci card. However having followed these instructions - almost - it worked OK for me - thank you very much. 

The deviation I made was that ndiswrapper utils would not install from the install CD I had used the previous day - so I ticked all the software sources - unticked the CD and it installed OK.

Thanks again.

---

### Post by SebRok on 2008-02-25
I have a Fujitsu Siemens Amilo 1840 D with a Realtek 8180 WLAN Mini-PCI NIC and got it working with NDISWRAPPER in WEP-encryption now!! FINALLY!! THANK YOU!!!

I used the v1.73 XP driver from here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L)

Rename the files, so that capital-letters get small:

NET8180.INF --> net8180.inf
and 
RTL8180.SYS --> rtl8180.sys

or something like that.. :)

it gave me an error message after "sudo ndiswrapper -l"
saying it is an invalid driver, but i just went on, it works brilliant with WEP 64bit

THANX A MILLION!:guitar:

---

### Post by manij on 2008-04-23
Hi Alan,

I was able to follow your instructions and get my Airlink101 AWLH3028 to work on Hardy heron. 

What I can' figure out is how do I get Knetwork manager to recognize and manipulate the settings.

The internet is working but, I have to into system setting or utilities to set the network, passphrase and all that.

Thanks in advance 
Mani

---

