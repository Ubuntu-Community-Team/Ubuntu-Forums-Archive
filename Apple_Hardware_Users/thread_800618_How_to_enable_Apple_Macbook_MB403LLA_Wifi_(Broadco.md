---
title: "How to enable Apple Macbook MB403LL/A Wifi (Broadcom Corp. BCM4328 802.11a/b/g/n)"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by vanakush on 2008-05-20
1. type ***sudo lshw*** for hardware information.
search for 
                description: Network controller
                product: BCM4328 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0

OR type ***lspci***
search for 

                02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

[COLOR="Red"]If you have this network card Download this file and extract it to ubuntu desktop[/COLOR] [ATTACH]70815[/ATTACH]

2. Go to ---->Applications--->Add/Remove-->System Tools----->and search for application---> Windows Wireless Drivers Ndiswrapper driver installation tool.

3. check the box for Windows Wireless Drivers Ndiswrapper driver installation tool and click Apply Changes. now you have ndiswrapper installed on your system.

4. Now go to System--->Administration--->Windows Wireless Drivers.

5. click Install New Driver--->select inf file location (e.g. /home/ubuntu/Desktop/bcmwl5.inf)

6. click Install.

7. Now go to System--->Administration-->Network--->select Wireless connection and click properties --> uncheck Enable roaming mode.

8. a)  now select your ESSID (e.g.DLINK_WIRELESS)
     b)  Password type (e.g.WPA2 Personal)
     c) Network Password -----------
     d) Connection settings----(depending upon your network)

9. click ok 

10. Done.

---

### Post by cyberdork33 on 2008-05-20
Does not include the 64bit driver. Also could you please name the source of the driver file?

---

### Post by hajk on 2008-05-23
> **cyberdork33 said:**
> Does not include the 64bit driver.Yes it does, because this driver is both for 32/64-bits.> Also could you please name the source of the driver file?I've unzipped both files and compared them with those on the DVD #1 (BootCamp stuff) that came with my MBP 4,1 -- they're identical. Note that the OP has a rev 03 wireless chip; the newest is rev 05. The zip-file isn't needed as all MBP 4,1 owners will have that DVD...

---

### Post by cyberdork33 on 2008-05-23
> **hajk said:**
> Yes it does, because this driver is both for 32/64-bits.
The .sys file is the actual driver... the inf is a descriptor and is valid for both 32 and 64 bits, but you still need the 64bit sys file. check on the dvd package.

---

### Post by MidnightRider617 on 2008-05-31
It keeps telling me that its an invalid driver whenever I try to install it in the Windows Wireless Drivers app.

---

### Post by cyberdork33 on 2008-05-31
> **MidnightRider617 said:**
> It keeps telling me that its an invalid driver whenever I try to install it in the Windows Wireless Drivers app.
then you are not using the right driver for your hardware.

you can see the installed drivers with ```
ndiswrapper -l
```

using the names you see from the output of the above command, you can remove the "bad" drivers with:
```
sudo ndiswrapper -r drivername
```

---

### Post by hudarsono on 2008-07-08
I also always get invalid driver, athough I use the same macbook which is MB403 and with Broadcom BCM4328 as you.

I wonder if you are using 32 bit version of ubuntu? Since I am using 64 bit version.SO if the driver is got from win Xp which is 32bit, it won't work on 64bit ubuntu. 

Do you have driver from vista?

---

### Post by cyberdork33 on 2008-07-08
> **hudarsono said:**
> I also always get invalid driver, athough I use the same macbook which is MB403 and with Broadcom BCM4328 as you.

I wonder if you are using 32 bit version of ubuntu? Since I am using 64 bit version.SO if the driver is got from win Xp which is 32bit, it won't work on 64bit ubuntu. 

Do you have driver from vista?

The Leopard DVD contains a driver for both 32bit and 64bit WinXP. The Vista drivers do not work with ndiswrapper (not yet anyway).

---

### Post by hudarsono on 2008-07-08
> **cyberdork33 said:**
> The Leopard DVD contains a driver for both 32bit and 64bit WinXP. The Vista drivers do not work with ndiswrapper (not yet anyway).

Would you explain to me how to extract 64bit Broadcom driver from Leopard DVD?

Or is the driver can be got from somewhere?

Thanks

---

### Post by cyberdork33 on 2008-07-08
> **hudarsono said:**
> Would you explain to me how to extract 64bit Broadcom driver from Leopard DVD?

Or is the driver can be got from somewhere?
You use the same inf file for both. you just need to have the other files in the directory with it.

What Mac (and hardware version) do you have? I will show you the proper page to follow for your hardware.

---

### Post by Dinatius on 2008-07-11
I'm having the same problem, working with the BCM4328 card on a white Core2 Duo iMac, running 64-bit.

I've been trying several methods, but I can't seem to find a valid driver anywhere. If it really is on the Leopard install DVD, then any help you could give me in finding it would be..... well, helpful.

I don't exactly want to take a swat at finding it myself because I'm a bit afraid that I'll end up copying a) the wrong file II) only ONE of the right files, or 3) end up somehow deleting all of my system files.

---

### Post by cyberdork33 on 2008-07-11
> **Dinatius said:**
> I don't exactly want to take a swat at finding it myself because I'm a bit afraid that I'll end up copying a) the wrong file II) only ONE of the right files, or 3) end up somehow deleting all of my system files.just stick to copying files to your user directory and you should be OK. For you machine though, (same as mine) you should be able to use older drivers.

General directions to get the driver from your Leopard DVD are here:
[https://wiki.ubuntu.com/MacBookPro/Penryn#head-28d7a01f5c4e8c3c04e53fa61fba99291e079cf4](https://wiki.ubuntu.com/MacBookPro/Penryn#head-28d7a01f5c4e8c3c04e53fa61fba99291e079cf4)

This guide shows getting and using a Dell-supplied driver that should also work.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup]("https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup")

---

### Post by Dinatius on 2008-07-11
> **cyberdork33 said:**
> just stick to copying files to your user directory and you should be OK. For you machine though, (same as mine) you should be able to use older drivers.

General directions to get the driver from your Leopard DVD are here:
[https://wiki.ubuntu.com/MacBookPro/Penryn#head-28d7a01f5c4e8c3c04e53fa61fba99291e079cf4](https://wiki.ubuntu.com/MacBookPro/Penryn#head-28d7a01f5c4e8c3c04e53fa61fba99291e079cf4)

Well, everything appears to have worked, but I'm still having trouble connecting wirelessly.
This may just be noobishness on my part, but its still a little frustrating.

The driver appears to have installed, but nothing seems to have changed other than that. I still don't even seem to have the option of connecting to a wireless network.

---

### Post by cyberdork33 on 2008-07-11
> **Dinatius said:**
> The driver appears to have installed, but nothing seems to have changed other than that. I still don't even seem to have the option of connecting to a wireless network.

```
ndiswrapper -l
```
should list windows drivers installed and if they are the correct one for your hardware.

once that is verified, load ndswrapper:
```
sudo modprobe ndiswrapper
```
After it is loaded, you should have a wlan0 interface in the output of:
```
 ifconfig
```

---

### Post by Justin B on 2008-07-11
I am having the same trouble with my MAC, I cannot connect wirelessly. I CAN however connect via ehternet cord. Any suggestions?

---

### Post by cyberdork33 on 2008-07-11
> **Justin B said:**
> I am having the same trouble with my MAC, I cannot connect wirelessly. I CAN however connect via ehternet cord. Any suggestions?Can you try some of the suggestions already in the thread and post the output requested? "It doesn't work" makes it difficult to determine what the issue is.

---

