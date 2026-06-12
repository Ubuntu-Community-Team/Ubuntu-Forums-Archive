---
title: "Cannot get WiFi [b43-fwcutter] to work on my Powerbook G4"
date: 2014-05-08
forum: Apple Hardware Users
---

### Post by robert94 on 2014-05-08
Hello

I'm running Lubuntu 14.04 [from a live DVD and with a dead ethernet port]

I have done the following for my [COLOR=#333333][FONT=Ubuntu]BCM4306 (rev 03)

[/FONT][/COLOR]sudo dpkg -i b43-fwcutter*

sudo modprobe -r b43 bcma
sudo modprobe -r brcmsmac bcma
sudo modprobe -r wl


sudo modprobe b43 
[COLOR=#333333][FONT=Ubuntu]
Note I used [/FONT][/COLOR][b43-fwcutter_018-2_powerpc.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/b43-fwcutter_018-2_powerpc.deb")[COLOR=#333333][FONT=Ubuntu]  and also tried [/FONT][/COLOR][b43-fwcutter_015-9_powerpc.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/b43-fwcutter_015-9_powerpc.deb") when the former didn't work
[COLOR=#333333][FONT=Ubuntu]
Yet when I run nm-tool or iwconfig i see now wlan ?

What else can I try to diagnose or get working ?


[/FONT][/COLOR]

---

### Post by rsavage on 2014-05-08
b43-fwcutter is a tool to extract firmware.  It doesn't contain firmware.  Also, Lubuntu should already have b43-fwcutter installed so there is no need to install it.

The link I gave to you had the instructions to download and extract the firmware.  The instructions haven't been updated yet for 14.04, but you should be able to work it out by following the links (or just follow the 12.04 instructions).

---

### Post by rsavage on 2014-05-08
> **rsavage said:**
>   The instructions haven't been updated yet for 14.04

I updated them so it would be good if you could test them.

---

### Post by robert94 on 2014-05-08
> **rsavage said:**
> I updated them so it would be good if you could test them.

rsavage

I am now posting this from the G4 ! :)

ok now I realise what I was not doing,

In regards to the documentation I suggest for beginners such as myself I kindly suggest that you make it even more obvious ;) that in addition to downloading the b43-fwcutter package and installing it that one must _also_ download and install the firmware. I assumed step 2 was only needed if one already had internet access ! [since it said with Internet access...]

Note I checked and b43-fwcutter _is not_ on my live DVD i.e. in /cdrom/pool/main/b

After seeing the wlan from nm-tool I then used preferences/network connections to create the WLAN connection

1. Now that I know it works and want to install as dual boot. Do you know any way to make the existing MAC OS 10.3.9 partition smaller. My undersanding is I can from 10.5.x without detroying what is there but I am still trying to locate the Leopard media install, are there alternatives even 3rd party for  example could or *should* I use gparted to make the existing one smaller ?!
2. I note running from the live DVD the cpu is often 100% and half or more of that is taken from task pcmanfm, what is it or is the high cpu and task due to running from a live dvd ?
3. How do I get a network icon on the task bar/tray [where time and  power is etc] so I simply click on the available wifi network[s] as I do  with Xfce ?

Thank you heaps for kindly replying to this post and helping :D

---

### Post by rsavage on 2014-05-09
> **robert94 said:**
> 
1. Now that I know it works and want to install as dual boot. Do you know any way to make the existing MAC OS 10.3.9 partition smaller. My undersanding is I can from 10.5.x without detroying what is there but I am still trying to locate the Leopard media install, are there alternatives even 3rd party for  example could or *should* I use gparted to make the existing one smaller ?!

Others are probably best to answer this as I don't use mac os x.  The few times I've tried to resize I just get fed up with how long it's taking and I abort it.  There is a bit in the FAQ about dual booting that I wrote, but I wish others would contribute to it as, like I say, I don't consider myself an authority on it.

> 
2. I note running from the live DVD the cpu is often 100% and half or more of that is taken from task pcmanfm, what is it or is the high cpu and task due to running from a live dvd ?

No idea.  I don't use 14.04 as it is noticably slower.

> 
3. How do I get a network icon on the task bar/tray [where time and  power is etc] so I simply click on the available wifi network[s] as I do  with Xfce ?

The network icon should be there, unless it has crashed and that is what is causing your high CPU.  Apport (the crash handler) can be a CPU hog.  

I'm guessing you have a nvidia card.  You can try disabling acceleration with the yaboot parameter nouveau.noaccel=1 .  In 12.04 some people reported the network icon disappeared due to a graphics glitch, but I had assumed that was nolonger present.

---

### Post by alan26 on 2014-05-13
If 14.04 is slower, what are you using?

---

### Post by Ket_Lubun on 2014-05-25
Sorry, but I am extra dense today and I have trouble following robert94's instructions, such as where to download b43-fwcutter package and where to download the firmware for installation.  I.e. end-to-end installation process.

After 2 weeks, I successfully installed dual boot on PowerBook G4 with OS X 10.5 and LUBUNTU 14.04 desktop.  My airport wifi works with 10.5 but not 14.04.  I suspect your solution will get my wifi working.  Many thanks in advance.

---

### Post by robert94 on 2014-05-25
Hi Ket

At this [location]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access") is the latest documentation, refer in particular to the section titled installing b43/legacy firmware

BTW I am about to dual boot my G4 with Lubuntu 14.04 too, in the install did you use install alongside MAC OS X or 'other' [to specify partition etc]

---

### Post by tgalati4 on 2014-05-26
Typically you would use the Disk Utility within OS X to resize the Mac partition.  Yes, it takes a long time, and yes it is risky, so back up important data.  The other way to dual boot is to take the old disk out, put in a new, bigger disk and put the old disk in a FireWire enclosure.  You can then boot OS X using the Option-T and select the FireWire drive and install Ubuntu on the new internal disk.

Installing a new disk is not trivial--watch the youtube videos on how to do it.

You can also clone your existing Mac OS X disk to a LaCie Firewire 800 external disk, then use the LaCie disk to boot from.  You will also find that it is faster than the orginal Powerbook disk drive.  Then wipe the internal drive and install Ubuntu and keep the LaCie for those times when you need OS X.

---

### Post by Ket_Lubun on 2014-05-26
Hi Robert, thanks for the location info.  After burning the b43 package and the firmware to a CD, now I realize that I do not even know how to access CD files in 14.04!  (embarrassed!)  cd /cdrom/pool/main/b/b43-fwcutter/ did not work for me.  (Got "No such file or director message".)  HELP!
As far as dual boot, I partitioned my HD into 2.  Installed 10.5 in one first, then installed 14.04.  Aftet 14.04 is installed, it automatically gave me the dual boot feature with YABOOT.  Hope this helps.

---

### Post by Hadaka on 2014-05-27
Hi Robert94,your broadcom card should be a simple driver load.
to begin..broadcom numbers their cards,,yours is BCM4306 this 
number is the card number only and does not determine the driver.
for the correct number the PCI-ID ...open a terminal and do...

```
lspci -nnk | grep -iA2 net
``` this will give you the [14e4:XXXX] 
PCI-ID for your wired and wireless broadcom cards.More than likely yours is  [14e4:4320]
next..prepare after a new os install to load the driver...in this case it is the LINUX-NONFREE driver
first load the updates this also helps the driver..do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
The purge is used to get rid of the bcmwl-kernel-source which is loaded by default
since 12.04 and causes much stress...the next line deletes a file that the bcmwl-kernel-source
created that blacklists modules needed for the b43 dirver.
now...let's load the driver you need,,,please do
From a wired connection...connected to the internet.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
this should get you up and running.
*There is a sticky on the Network & Wireless page that walks you through this if you get stuck
post back good news

---

### Post by Ket_Lubun on 2014-05-28
Problem solved by installing the alternate install iso

---

