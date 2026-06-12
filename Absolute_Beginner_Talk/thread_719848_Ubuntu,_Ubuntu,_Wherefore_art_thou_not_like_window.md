---
title: "Ubuntu, Ubuntu, Wherefore art thou not like windows"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by JacovW on 2008-03-09
Okay I've been told Ubuntu is extremely user friendly. Why then does the how to give me a list as long as the bible of things to do when i want to install my HUAWEI E220 USB Modem? and why the heck is there no Afrikaans dictionary when i was told there is (granted that was an outside source), and the one i downloaded didn't work either. I want to work on this thing but it is driving me to tears and mommy always said boys don't cry! please tell me Ubuntu can be as simple as windows...

---

### Post by kellemes on 2008-03-09
> **JacovW said:**
> Okay I've been told Ubuntu is extremely user friendly. Why then does the how to give me a list as long as the bible of things to do when i want to install my HUAWEI E220 USB Modem? and why the heck is there no Afrikaans dictionary when i was told there is (granted that was an outside source), and the one i downloaded didn't work either. I want to work on this thing but it is driving me to tears and mommy always said boys don't cry! please tell me Ubuntu can be as simple as windows...

Afrikaans dictionary for aspell.. I assume this is what you want?
from synaptic, browse for "aspell-af" and install it **or**
from terminal do the following..
```
sudo apt-get install aspell-af
```

Don't know anything about installing USB-modems..

---

### Post by Hmarroqu on 2008-03-09
no guarantees...It a better OS than windows in respect to a whole list of things....but keep in mind your machine and hardware was made to work for the OS that is basically all over the place and is the standard...Ubuntu is an alternative...people switch to it for various reasons and deal with the hardware incompatibilty and things that must be fixed because in the long run...its simply better...who knows tho...you might not like it...maybe you will,...get it to work and let me know how it goes from there.

---

### Post by Arthur Archnix on 2008-03-09
You need to be careful to pose specific questions, because posts about how Ubuntu is not like Windows, or Ubuntu is not as good as <insert OS here> because <reason> tend to get moved to either the Testimonials forum, or recurring discussion.

I've never read the bible, but I know where to find it if I wanted to. In this case, you apparently need help with some instructions on a HUAWEI E220 USB Modem. Why don't you post a link to the instructions and what problems you're having. Error messages, etc..

Second, where did you download an affikaans dictionary and what did you do to install it. How do you know it isn't isntalled, working etc.

---

### Post by Scarath on 2008-03-09
[http://ubuntuforums.org/showthread.php?t=439163](http://ubuntuforums.org/showthread.php?t=439163)

[IMG]http://farm2.static.flickr.com/1166/1454018245_5986b5e6c1.jpg[/IMG]

---

### Post by handydan918 on 2008-03-09
> **JacovW said:**
> Okay I've been told Ubuntu is extremely user friendly. Why then does the how to give me a list as long as the bible of things to do when i want to install my HUAWEI E220 USB Modem? and why the heck is there no Afrikaans dictionary when i was told there is (granted that was an outside source), and the one i downloaded didn't work either. I want to work on this thing but it is driving me to tears and mommy always said boys don't cry! please tell me Ubuntu can be as simple as windows...

Nope. It can't. It isn't Windows, and if that's what you want, you should use it. It will become easier to use when the device manufacturers start writing drivers for Linux, as many have begun to do. Until then, count up the money you've saved on Windows licenses and security software, and buy hardware that works with Linux. There are many sources on the net for finding out if a device is supported, not the least of which is the manufacturers web site.

---

### Post by Joeb454 on 2008-03-09
Have you actually tried following the instructions for getting your USB Modem to work?

---

### Post by skymera on 2008-03-09
have you ever considerd Linux ISN'T Windows.

---

### Post by fatality_uk on 2008-03-09
There's a number of ways to get the HUAWEI E220 USB Modem. If you are running it on a Vodafone network, simply visit [http://www.vodafonebetavine.net/web/guest/home](http://www.vodafonebetavine.net/web/guest/home) and install the Mobile Connect Card driver for Linux. Alternatively, if it Orange/O2 I can probably give you a beta version of their Linux drivers. It's not public but I am sure that I can swing it by them to get you a copy, Alternatively you could run GnomePPP.

You have to remember Linux isn't Windows. Think of it this way, if you have only ever driven an automatic, and then are given a manual, it's will take a few hours to get used to it.

---

### Post by ShodanjoDM on 2008-03-09
A simple search using google: "Huawei E220" returned many results. Here's one of them from - no other than - this forum circa 2006, don't know if you already know this, but just in case:

[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)

>  Re: Huawei's hsdpa modem Model E220
OK - PRETTY MUCH DISREGARD MOST ALL OF MY ABOVE POSTINGS AS I BRANCHED OFF THE WRONG TRACKS. MY HUAWEI E220 USB IS NOW WORKING.
================================================== =====================

The Huawei E220 is a USB 'dongle' for HSDPA connection through (for me, anyway) the Vodaphone network in New Zealand.

When inserted into a Ubuntu OS, it is immediately detected as a SCSI/CDROM type bulk storage device, and the files that are used by Windows appear attached to the filesystem similar to any other USB storage device.

Close any window that might be showing you those files. Then unmount the device (eject the CDROM icon you'll find on the desktop created when you inserted the device).

All commands I give here are just the commands - you will likely need to put 'sudo' in front of them so you have the permissions of root to carry them out...

Insert the device and give it a chance to settle down (enjoy watching the lights flash...)

When you insert the device and it gets recognised as a storage device, it will have created /dev/ttyUSB0. You can see that with:

ls -la /dev/ttyU*

You will likely only see one entry: ttyUSB0.

To make the modem work, you must first remove the module that is used for usb-storage devices. You can do that with:

rmmod usb-storage

If you are told it is in use, that is an indication you didn't close windows and eject the device first.

This next command may not be absolutely necessary, but it won't hurt anything (heh, heh...):

rmmod usb-serial

You are now going to re-insert that module, but giving the specific details of your modem. First, make sure you have the right details by using:

lsusb

You should see an entry similar to this in the output:

Bus 004 Device 004: ID 12d1:1003

The Bus and/or Device number might be different for you, but the important part is the ID. If yours is not 12d1:1003, you'll need to modify the next command, but I *think* it will be either that or 12d1:1001...

This command will insert the module with the device specific details:

modprobe usbserial vendor=0x12d1 product=0x1003

Now, remove the device, wait a bit for things to settle, and then plug it back in.

I *think* you may now have maybe three entries if you do:

ls -la /dev/ttyU*

Basically, what has been done is that you have removed the initial inclination to treat the device only as a bulk storage (removing the module that handles that). You've also manually caused the recognition of the device (using the modprobe command). So that when you re-plugged it, it should now be able to work with the *modem* part of the device addressing it as /dev/ttyUSB0, rather than that being the bulk storage device.

Use a text editor such as pico to edit or create if necessary the file to handle the dialling configuration. My /etc/wvdial.conf file looks like this:

# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem


I've only put in the relevant sections - the full file can be found at the address below this posting.

You can dial the modem with:

wvdial hsdpa

If all is happy, you'll see the messages in the terminal window to show how it is connecting, your IP address, your remote gateway and 2 nameservers the network provides for you.

Do remember the various need for 'sudo' unless you change ownerships/permissions. In particular, if it looks like you've connected but are not able to connect to any sites, etc, look for a message telling you that /etc/ppp/pap-secrets and /etc/ppp/chap-secrets are not able to be written to - that may well indicate that you for sure need to run the wvdial command as sudo (If you are running it as a normal user, that user would need to have the ability to write to those files for the connection to be able to work...)

I am writing this while standing on the shoulders of the knowledgeable and the helpful. In particular, see [http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726) - Post 1 in that thread, and Tazz_Tux who wrote and maintains it, has been invaluable. Go there if for no other reason than to get the latest version of wvdial.conf

Enjoy your Huawei E220 under Ubuntu!

Nick

Never knew the Bible is *that* long...

---

### Post by The Cog on 2008-03-09
You ask why the instructions to install a Huawei modem are so long. The answer is that they don't provide open source drivers that can be incorporated into the kernel. The manufacturers have decreed that the drivers cannot be incorporated into the OS. This is the manufacturers decision to restrict the usefulness of their hardware and drivers.

Actually, I would suggest that the easiest thing to do is to invest in an external ADSL router that has an Ethernet switch. These will work with any OS and you don't have to fanny around with drivers like that ever again. I actually find my 4-port switch useful for plugging other PCs into as well. Get rid of that proprietary junk on ebay.

I don't know about dictionaries I'm afraid.

EDIT:
I just remembered - my next-door neighbouor got ADSL last week, and he was supplied with a huawei "modem". This little thing had both a USB port (which needed drivers installing) and a perfectly normal Ethernet port. They called it a "modem" but in reality it was a router with NAT and a DHCP server. If you have one of those cute litttle boxes, just use the Ethernet port.

---

