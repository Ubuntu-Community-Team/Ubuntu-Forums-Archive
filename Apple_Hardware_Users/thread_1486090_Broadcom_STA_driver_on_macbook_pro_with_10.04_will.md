---
title: "Broadcom STA driver on macbook pro with 10.04 will not connect"
date: 2010-05-17
forum: Apple Hardware Users
---

### Post by KilianValkhof on 2010-05-17
After a (frustrating*) installation of 10.04 on my macbook pro 5,5, the wireless broadcom STA driver is now in a perpetual state of trying to connect to networks, and re-asking the same password about every minute. 

I tried reinstalling the driver, changed my wireless network to wpa2 instead of wpa personal but to no avail (as suggested somewhere). How can I fix this?

Edit: Today, maybe once or twice it'll spontaneously connect, but it will disconnect after some time.


*crashed on update, then a fresh install but various nVidia, kernel, wireless and webcam problems throughout the weekend, fresh install again today, no webcam despite isight-firmware-tools and no wireless as mentioned above. I hope fixes are available soon, because it's all very unstable :(

---

### Post by linuxopjemac on 2010-05-17
Why don't you try Karmic ?

Lucid installation instructions:
[https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Wireless](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Wireless)

Karmic:
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic)

---

### Post by KilianValkhof on 2010-05-17
That doesn't really solve the problem, does it? I came from Karmic, I updated, it stopped working.

---

### Post by dustym on 2010-05-17
Hi,

I have the exact same issue. Based on my research, it looks like an issue with certain wireless N devices. I have a dlink N router and I had to drop it to G and that sorta worked, but it is still inconsistent in connecting.

Here is a launchpad bug where other people seem to be having similar issues

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340)

---

### Post by linuxopjemac on 2010-05-18
I am just trying to help. Next time I will think twice to post anything for you.

---

### Post by KilianValkhof on 2010-05-18
Hey Dustym, I use a B+G router (sitecom). Hadn't found that bug yet, i'll be following it :)

---

### Post by kwiksand on 2010-05-18
Ah, others who are having the same problem as me, except I'm getting it on Three laptops (MBP and two Dells) all with different wireless cards.

I've reported it in the Networking/Wireless forum in thread [http://ubuntuforums.org/showthread.php?t=1485785](http://ubuntuforums.org/showthread.php?t=1485785)

Haven't found anything out as yet though,  but I definitely think its a Lucid/10.04 issue with wireless and WPA networks as opposed to anything to do withthe Broadcom drivers.

---

### Post by KilianValkhof on 2010-05-19
After looking around some more for broadcom STA and WPA, I switched my network from tkip to AES security, and was able to connect (easier).

---

### Post by KilianValkhof on 2010-05-19
...

---

### Post by kwiksand on 2010-05-19
Interestingly enough I noticed at the office today if I walk over to the router and let it connect while standing next to it it appears to work a lot quicker.

Good enough solution for me, for the time being(I guess).

---

### Post by KilianValkhof on 2010-05-19
Alas, after a restart, the same problems appear again. Anyone?!

---

### Post by breimer273 on 2010-05-20
I have been dealing with this same problem. I have a Netgear N router at home and a G router at work. I get the same problems. Both places except when I lower the encryption to WEP. No problems then. Right now at home I have WPA2 and at work its WEP and no problems at work but problems at home. It is very frustrating. Hopefully someone looks at that bug soon.

---

### Post by KilianValkhof on 2010-05-29
For anyone having problems, the solution here worked for me: [https://bugs.launchpad.net/ubuntu/+bug/572777/comments/35](https://bugs.launchpad.net/ubuntu/+bug/572777/comments/35)


> 
Go to to Debain Packages Organization and manually download (watch your arcitecture - i386 for 32-bit installs, AMD64 for 64-bit installs, etc, etc - do not use ia64 for standard 64bit installes - that specifically for the Intel Itanium CPU & will cause very large problems/headaches) 

wpasupplicant (here: [http://packages.debian.org/sid/wpasupplicant](http://packages.debian.org/sid/wpasupplicant) )
libpcsclite1 (here: [http://packages.debian.org/sid/libpcsclite1](http://packages.debian.org/sid/libpcsclite1) ) 
libssl0.9.8 (here: [http://packages.debian.org/sid/libssl0.9.8](http://packages.debian.org/sid/libssl0.9.8)). 

Once all three are downloaded, install the two library packages first with kpackagekit (for kubuntu - use gdebi for Ubuntu) then wpasupplicant. 

When done, reboot & you should have working wireless (post if not).


---

