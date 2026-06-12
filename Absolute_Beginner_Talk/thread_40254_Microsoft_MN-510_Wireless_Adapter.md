---
title: "Microsoft MN-510 Wireless Adapter"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by Mr. Electric Wizard on 2005-06-08
Hello all,
Complete newbie to Linux...
I have a MN-510 wireless adapter that I would like to use with Hoary Hedgehog.
I found this page that indicates that it will work with Linux...
[http://www.linuxquestions.org/hcl/showproduct.php?product=673&sort=8&cat=146&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=673&sort=8&cat=146&page=1)

I also downloaded this tar.gz file from an ftp site.
Once I have this file (downloaded onto my working xp box) what do I need to do with it?
It is only 326K, so it will fit on a floppy, and  I can copy it to my Ubuntu box.  But what do I do with it after I copy it?

---

### Post by Mr. Electric Wizard on 2005-06-11
Something else...
I finally got to run the ndiswrapper for this the mn510.inf driver and now it shows up in device manager, but doesn't show up in /etc/network/interfaces?
Anybody have any idea how I can use this device?

It seems like if it shows up in device manager that I should be able to use it, no?

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=Mr. Electric Wizard]Something else...
I finally got to run the ndiswrapper for this the mn510.inf driver and now it shows up in device manager, but doesn't show up in /etc/network/interfaces?
Anybody have any idea how I can use this device?

It seems like if it shows up in device manager that I should be able to use it, no?[/QUOTE]

try this command:

sudo modprobe ndiswrapper

---

### Post by Mr. Electric Wizard on 2005-06-13
When I ran sudo modprobe ndiswrapper, I got a Fatal Error!
I think that if I get this line working, the adapter will start working...
Any help would be much appreciated.

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=Mr. Electric Wizard]When I ran sudo modprobe ndiswrapper, I got a Fatal Error!
I think that if I get this line working, the adapter will start working...
Any help would be much appreciated.[/QUOTE]

Can I see the exact fatal error please?

---

### Post by Mr. Electric Wizard on 2005-06-13
I had a feeling you would ask that. :) 
I am at work right now, but when I get home tonight I will respond with error syntax.
Thanks for sticking with me PHG.

---

### Post by CubanCorona on 2005-06-13
I'm also trying to get my mn-510 to work.  But I can't find the driver files (inf and sys)!  Is there any way you can send me a copy of them? I would REALLY appreciate it.  My email is [email]CubanCorona@gmail.com[/email].  I hope you get it working OK.

---

### Post by Mr. Electric Wizard on 2005-06-14
Email sent!
If you get it working let us know what you did... :wink:

---

### Post by Mr. Electric Wizard on 2005-06-14
Ok PFG, hereis my error...

```
FATAL:  Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko):  Operation not permitted
```

---

### Post by Mr. Electric Wizard on 2005-06-15
I read in another post that I might have an invalid driver?
This is the only driver I have...
Anybody else have a MN510 driver that they know works?

---

### Post by illuvatar on 2005-06-15
Mr.Electric: It seems that you try to use modprobe as a local user. It's only allowed for the superuser, so try sudo modprobe, or become root first.

---

### Post by Mr. Electric Wizard on 2005-06-15
become root by sudo, no?
If that's what you mean, then yes, I tried that...
Is there another way to become root other than sudo?

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=Mr. Electric Wizard]become root by sudo, no?
If that's what you mean, then yes, I tried that...
Is there another way to become root other than sudo?[/QUOTE]

sudo -s

---

### Post by Mr. Electric Wizard on 2005-06-15
OK guys, I think I'm spinning my wheels here...
Sudo -s will become root, but is there any difference in doing this, and just doing:
sudo modprobe?

---

### Post by somuchfortheafter on 2005-06-15
are you sure you used sudo?
also try unistalling and then reinstalling ndiswrapper and linking the drivers again, followed by a reboot.

---

### Post by Mr. Electric Wizard on 2005-06-15
No dice guys...

```

root@ubuntu:~# sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

Seriously, is it a lost cause?  Should I just do some attic work, and run a cable?
Doesn't seem like it wants to work... :|

---

### Post by Mr. Electric Wizard on 2005-06-15
Wow, I don't know what I just did, but it worked...
The correct driver is installed! :razz: 
Now that I have modprobed this driver what is the next step to get this wireless adapter working???

---

### Post by adg57 on 2005-06-15
[QUOTE=Mr. Electric Wizard]Wow, I don't know what I just did, but it worked...
The correct driver is installed! :razz: 
Now that I have modprobed this driver what is the next step to get this wireless adapter working???[/QUOTE]


I am getting the EXACT same error as you.  Do you have any details as to what you did to overcome?

Thanks in advance.

EDIT:

I solved the issue, it was the wrong inf file!

---

### Post by fastluck on 2005-06-15
[QUOTE=Mr. Electric Wizard]Wow, I don't know what I just did, but it worked...
The correct driver is installed! :razz: 
Now that I have modprobed this driver what is the next step to get this wireless adapter working???[/QUOTE]

Add your modprobe statement to /etc/init.d/bootmisc.sh.

Fastluck

---

### Post by Mr. Electric Wizard on 2005-06-15
I removed the mn510 driver using:
sudo ndiswrapper -e mn510.inf

Then reinstalled it.
Then modprobed it and it worked...
Seems a little wierd.  Make sure you don't have it installed already, using:

sudo ndiswrapper -l

Good Luck!

---

### Post by Mr. Electric Wizard on 2005-06-15
[QUOTE=fastluck]Add your modprobe statement to /etc/init.d/bootmisc.sh.

Fastluck[/QUOTE]

Add modprobe statement?

---

### Post by Mr. Electric Wizard on 2005-06-15
Before I worry about booting it up with the modprobe, I need to figure out how to get it to show up in System-->Administration-->Networking...
How do I do that?

When I:
sudo ifup wlan0 **I get Ignoring Unknown Interface wlan0=wlan0...**

---

### Post by Mr. Electric Wizard on 2005-06-16
Bizump!
I think I'm almost there guys, don't give up on me yet... [-X 
Well after many attempts at trying to configure this card, I have gotten nowhere.

My question to you is:
If my usb interface installed correctly with modprobe ndiswrapper, at that point should it have come up in "Networking" and /etc/network/interfaces?
Or is there some thing else that I have to do?

some code:
```
root@ubuntu:~# sudo /sbin/dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```



```
root@ubuntu:~# ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```



So am I screwed or what?

---

### Post by evader on 2005-06-29
[QUOTE=Mr. Electric Wizard]become root by sudo, no?
If that's what you mean, then yes, I tried that...
Is there another way to become root other than sudo?[/QUOTE]


I am getting that modprobe error as well.
Anyone have the CORRECT working MN510.INF file? the one I found from an old XP installation says its INVALID! when I try it. Someone hook it up! my email is brownking2005 at hotmail.com.


I found some other driver on google, but I can't do a modprobe. Help!! 


Thanks

---

### Post by Mr. Electric Wizard on 2005-06-30
So far, I haven't found anyone that actually got this adapter working with Ubuntu...
It probably works, probably just user error, but I gave up and just ran a Cat5 to my Ubuntu PC. :-| 
Good luck with your wireless foray.

---

### Post by evader on 2005-06-30
I can get Ndiswrapper working, it detects the hardware and everything. Modprobe ndiswrapper doesn't seem to do anything. Nothing shows up in network-admin program.

Ubuntu was going to replace XP :( but internet doesn't work  :?

---

### Post by Mr. Electric Wizard on 2005-06-30
[QUOTE=evader]I can get Ndiswrapper working, it detects the hardware and everything. Modprobe ndiswrapper doesn't seem to do anything. Nothing shows up in network-admin program.

Ubuntu was going to replace XP :( but internet doesn't work  :?[/QUOTE]

Same thing happened to me, no errors when running any of the ndiswrapper functions or anything.  In device manager, my 510 showed up as a USB network device, but would not configure, or show up in Networking...
I fought it for a long time, then just bit the bullet and ran cable.  It's much faster anyways...

---

