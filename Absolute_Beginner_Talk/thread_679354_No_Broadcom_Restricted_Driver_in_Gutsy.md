---
title: "No Broadcom Restricted Driver in Gutsy"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by BeardedOne on 2008-01-26
I've got the notorious

---

### Post by BeardedOne on 2008-01-26
Sorry about my abbreviated post before - I got cut off mid-sentence.

I'm using an HP DV2000 with the notorious Broadcom 4310 wireless built-in. In the Community Docs - WifiDocs/Driver/bcm43xx/Gutsy - it says that this driver should appear in the Restricted Drivers Manager - but not on my install. Is that a problem with my install or has something changed since the docs were written?  

I used the troubleshooting idea from the same docs to reload the driver module with "sudo modprobe bcm43xx" and can see it now listed after using "dmesg", but there is no sign of it after trying "iwconfig" (reads 'no extensions') and no listing in the Restricted Drivers Manager.

---

### Post by buccaneere on 2008-01-26
[IMG]http://images.corvetteforum.com/images/smilies/dupe.gif[/IMG]
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4213585](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4213585)

---

### Post by buccaneere on 2008-01-26
[IMG]http://images.corvetteforum.com/images/smilies/dupe.gif[/IMG]
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4213547](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4213547)

---

### Post by txbikerider on 2008-01-26
I've got an HP DV2710 with Gutsy installed as well and I am having the same problem.  I've installed from a Live CD.

I do show a wireless windows driver installed using the System>Administration>Windows Wireless Drivers menu.  It's listed as bcmwl6.  I downloaded it from the HP web site.

What does the output of the following command show on your system?

sudo lshw -C network

---

### Post by BeardedOne on 2008-01-27
Thanks for your reply.

Here's the output to "sudo lshw -C network"

 *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: ec:f3:42:72:1d:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.72 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by jan quark on 2008-01-27
it seems you are not alone

perhaps the solutions posted in this link will help you
[http://ubuntuforums.org/showthread.php?p=4213173](http://ubuntuforums.org/showthread.php?p=4213173)

---

### Post by BeardedOne on 2008-01-27
Thanks.

I'll try that and report my results.

Should I use the same driver as in the Dell article, or is there a better one for my HP DV2000 w/ BCM 4310 rev 01?

---

### Post by txbikerider on 2008-01-27
I tried the solution in the link posted by jan quark.  No joy.  I did use a driver I downloaded from HP versus the Dell driver.  Like you, I wondered if I should have used the Dell driver.

The output of the lshw command looks like what I see as well.  

Did you load the 32 bit or 64 bit of the OS?  I've loaded the 32 bit version and I'm seriously considering blowing that installation away and going with the 64 bit version but I'm not sure that's going to change the situation any.

---

### Post by txbikerider on 2008-01-27
One other item of note.  I'm dual booting my DV2710 with Vista Home.  The wireless device works with no problems when booted into Vista.  The driver listed is the bcmwl6 driver.

---

### Post by BeardedOne on 2008-01-27
I copied and pasted the commands from the Dell site and got this errror.

bill@BearHeart:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
[sudo] password for bill:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
bill@BearHeart:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
bill@BearHeart:~$ sudo ndiswrapper -i /tmp/DRIVER/bcmwl5.inf
sudo: ndiswrapper: command not found
bill@BearHeart:~$

---

### Post by BeardedOne on 2008-01-27
Thanks txbikerider.  I didn't have much luck with jan qark's method either.  Thanks for the correct driver.  I did figure out how to load ndisgtk, but it said I had an invalid driver.

---

### Post by BeardedOne on 2008-01-27
I saw on the forum that the bcmwl6 driver is just for Vista (perhaps meaning just 64 bit).  I'm running 32bit gutsy because I heard that 64 bit has got some problems.  

I loaded bcmwl5.inf through the windows wireless drivers window and it shows as detecting the hardware, but it still doesn't show up on my network manager.

---

### Post by BeardedOne on 2008-01-27
While under Vista, a blue light lit up when the wireless switch was moved right, in gutsy the light stays amber whichever way the switch is moved.  Is this significant?

---

### Post by txbikerider on 2008-01-27
Based on the error message you got, it doesn't look like the ndiswrapper program was properly installed.  What happens when you type

ndiswrapper -l

You should get something like:

bcmwl5  :  driver installed
                device (14E4:4315) present

I installed ndiswrapper from source code just to make sure I had all the pieces and it installed properly.

I went back and looked at my set up. I'm using the bcmwl6 driver.  When I fire up the Wireless Network Drivers control panel (System>Administration>Windows Wireless Driver), it shows the bcmwl6 driver and indicates that the hardware is present.  When I use the bcmwl5 driver, the control panel lists the hardware as "not" present.  Either way, the wireless adapter doesn't show up in the To my knowledge, I'm not running a 64 bit version of Vista so the driver may just be the Vista driver (as opposed to the XP). Are you running Vista or XP?

The blue light indicates the wireless card is active.  I experienced the same thing.

---

### Post by BeardedOne on 2008-01-27
Thanks.  That helps.

Right now I'm needing my new laptop for work (the old one died).  Is there a USB connected wireless card that will work our of the box with gutsy? I can get that going while I work on the built in problems.

---

### Post by txbikerider on 2008-01-28
Do you mean a wireless usb type dongle? 

Either way, I don't know.  I imagine you could find one that would work.  

I did some more research last night and found out that the problem may be that using the ndiswrapper approach may not work because the driver does not turn on the radio.  On another forum someone suggested the use of the bcm43-fwcutter program but lead me to believe you needed to start with a clean install to really make sure it would work.

I've got a line on a different wireless card.  I'm going to try that first.  If that doesn't solve the problem, I'm going to reload from scratch and try the fwcutter program.  If that doesn't work, I may jump over to FreeBSD.  I've used is extensively with my servers but never messed with putting it on a laptop.

---

### Post by SyCo123 on 2008-01-28
this worked for me
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by BeardedOne on 2008-01-29
Thanks txbikerider

Yes, I think you're right.  It doesn't turn on the wireless.

Here's a summary of where I am now.

I can see the bcm4310 driver loaded (lshw -C Network)
But it is UNCLAIMED and I assume this means it's not recognized by the system
I've loaded ndisgtk and bcmwl5 and it recognizes the hardware
But no option comes up in network manager to use wireless
I've looked at the fwcutter articles but can't tell which driver to use with my 4310

I put in my Atheros based card that works in another machine running 7.04
In my HP DV2000 running 7.10, no restricted driver shows up in the manager

---

### Post by BeardedOne on 2008-01-29
WOW! I reinstalled gutsy, reinstalled ndisgtk, reinstalled bcmwl5
and it works.

---

### Post by BeardedOne on 2008-01-29
Ok, I rebooted and lost it.

It now appears that the bcmwl5 driver will work, but only if I reload it after every reboot. Is there a fix for this?

---

### Post by txbikerider on 2008-01-29
Did you do the clean install from a LiveDisk?  If so, then what you experienced is what I've read about on other forums.  Something about the LiveDisk install turns on the radio and everything is cool until you reboot.  

Was your success with the original BroadCom card or with the other card?

---

### Post by BeardedOne on 2008-01-29
I'm using my built-in Broadcom wireless

I reinstalled Gutsy from the LiveCD.
Immediately installed ndisgtk
Immediately installed bcmwl5.info in the Wireless Window Drivers
I tried to blacklist the old driver - but I don't think that worked
I used sudo gedit /etc/modprobe.d/blacklist   then added "blacklist 43xx"
but the old driver is still there when I reboot (before I reinstalled the driver in Windows Wireless)
I must be blacklisting it wrong or something

By the way, the wireless light is working now - don't ask me why

I really, really don't know what I'm doing.  I read and then it's monkey see, monkey do.

Any ideas?

---

### Post by BeardedOne on 2008-01-30
Got it working!

Here's what I did

On a very fresh install from Live CD...

I downloaded ndisgtk with Admin > Synaptic

I unpacked bcml5.inf and any associated binary files into ONE directory

I blacklisted the default driver
sudo gedit /etc/modprobe.d/blacklist  -- then add 'blacklist 43xx'

I installed bcml5 driver under Admin > Windows Wireless Drivers

I made ndiswrapper load the driver on reboot
echo ndiswrapper | sudo tee -a /etc/modules

Good luck txbikerider and everyone with a Broadcom setup

---

### Post by beerorkid on 2008-02-04
been going crazy with this for about a week.

hp dv2710us with the BCM4310

I figure since you are running a dv2000 this might just work.  Have reinstalled about 10 times already, might as well do one more.

Bearded one, where did you get the bcmwl5.inf?  I figure any of them might work, I have gotten it from many different locations.

---

### Post by SurferGTO on 2008-03-03
so far ive got nothing working either. ive tried several different methods and nothing seems to be working. i show the driver as being installed in the windows wireless drivers. but i got nothing....

---

### Post by ronaldv2li on 2008-03-03
try this one.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

