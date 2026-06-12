---
title: "How to get wireless (BCM4331) working on Macbook Pro 8,2/8,1/8,3 + Natty"
date: 2011-09-23
forum: Apple Hardware Users
---

### Post by proycon on 2011-09-23
As you probably all know, Macbook Pro 8.x owners, with a Broadcom 4331 wireless card, ) have had to endure the hardship of being tethered with a network cable to the wall, or use the flaky ndiswrapper locking up our precious systems at random moments (read: whenever we are doing something important and haven't saved our data yet).

But no more of this now: After some search I found that there is a solution to get our wireless working properly with the newest open-source b43 driver (recall that the proprietary wl driver *STILL* provides no support for the BCM4331). The solution is here and whilst it does involve compiling a kernel module, (but not upgrade the entire kernel to 3.0+), the steps are well laid out and should be easy to follow:

[http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

I have tested this and it works great on Ubuntu 11.04 (natty). This post is written and published without any strings attached!

Note 1: If you later do a kernel update through the package manager you will also have to recompile the module as it will probably get overwritten.

Note 2: If the wireless.kernel.org link in the post is not working (kernal.org is down after their unfortunate security mishab), then get the required package from for example [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

---

### Post by inphektion on 2011-09-23
Would the same have to be done on oneric?  or less steps needed?

---

### Post by proycon on 2011-09-24
I haven't tried oneiric yet (waiting for the final release), but if the b43 driver with oneiric doesn't work out of the box yet, then the same procedure can be applied.

---

### Post by cuppido on 2011-10-15
Instructions from [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html) are working in my MBP 8,2 in Oneiric.

---

### Post by inphektion on 2011-10-16
so when kernel updates are out via the repo these steps need to be redone, correct?
Edit:  yes.  

any chance an update in oneric will have builtin support?  or we looking at precise pangolin for that?

---

### Post by ymccarthy on 2011-12-08
I have just followed the instructions ( [http://homepage.uibk.ac.at/~c705283/..._81/index.html](http://homepage.uibk.ac.at/~c705283/..._81/index.html) )  to install the b43 driver on MacBook Pro 8,2 running Ubuntu 10.04 LTS (Lucid) and it worked like a charm!!! My Wireless is up and running! :D Thanks a lot!

---

### Post by jerwilkins on 2011-12-15
This is on a 8,3 Macbook running Oneiric:

Followed the instructions to the letter and got:
```
FATAL: Error inserting b43 (/lib/modules/3.0.14-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid argument
FATAL: Error running install command for b43
```
after the ```
sudo modprobe b43
``` step.
(That path may not be exact; I'm typing it from memory, but when I was on the machine I double-checked to make sure the .ko file was where it ought to be.)

This is using the latest files from the above-linked site.

Any notions?
Thanks much in advance!

---

### Post by aliyanage on 2012-02-26
Hi,

I've managed to install the driver and I can also see the interface being available when doing an ifconfig:

```

root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr c8:2a:14:0a:02:30  
          inet addr:10.0.1.58  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca2a:14ff:fe0a:230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24779 (24.7 KB)  TX bytes:22580 (22.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1073 (1.0 KB)  TX bytes:1073 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr e0:f8:47:1a:87:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

But as you can see it doesn't get an ip address, would someone be able to help me out on this?

---

### Post by jmr423 on 2012-03-10
hey I'm getting this error 

```
FATAL: Error inserting b43 (/lib/modules/3.2.6/updates/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

At the last step, ```
sudo modprobe b43
```

What do i do :S?

---

### Post by heathman001 on 2012-11-15
I see this is an older thread, but I'm also getting the following when I run modprobe b43
> FATAL: Error inserting b43 (/lib/modules/3.2.0-32-generic/updates/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg output:
> cfg80211: Unknown symbol simple_open (err 0)


Has anyone figured out the solution? I've tried a number of versions from [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) They all compile without issues, but they all fail with the same message from modprobe.

---

### Post by varunendra on 2012-11-15
> **heathman001 said:**
> I see this is **an older thread**,..For the same above reason ^^ you should post your own thread in networking and wireless section, and besides a complete description of the problem, as well as what all you have tried so far, please also post the result of what is suggested in this post - [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Then wait for a while and see if someone experienced picks it up. If not, you may PM me its link so I can follow (consider this last resort since I'm not familiar with this card nor compat-wireless drivers).

---

