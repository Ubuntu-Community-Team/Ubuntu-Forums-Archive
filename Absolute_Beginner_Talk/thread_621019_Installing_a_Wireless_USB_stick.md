---
title: "Installing a Wireless USB stick"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by teuma on 2007-11-23
I went down the shop today and purchased a Belkin G wireless USB.

Simple reason my mate wanted me to install Ubuntu on his laptop and does not have built in wireless

I followed instructions here
[http://ubuntuforums.org/showthread.php?t=202254](http://ubuntuforums.org/showthread.php?t=202254)

But installing Belkin

Its all done, I can see the routers but it comes up with the same error message as before i installed


> 
Error connecting to wireless network
the requested wireless network requires security capabilities unsupported by your hardware


If I go to Windows Wireless Drivers, it says  "Hardware not present"

BUt when i run
"ndiswrapper -l"
it says
> 
rt73 : driver installed
device (050D:705A) present (alternate driver: rt73usb)



All i want to do is be able to find a Wifi and connect to it.

---

### Post by teuma on 2007-11-23
bump****

---

### Post by nathanhillinbl on 2007-11-23
Is there any security on the network you are trying to connect to? (WPA, WEP) WPA connection requires a separate package (WPA-someting) to connect.

---

### Post by teuma on 2007-11-23
The Router security is WPA, I have wpasupplicant already installed.

But I have not connected this to the USB Device, does this happen automaticly or do i need to do something.

---

### Post by wieman01 on 2007-11-23
Does the Windows driver support WPA at all?

---

### Post by teuma on 2007-11-23
It should do, I was told it does.

It is a belkin Wireless G Network Adaptor, G 54mbps

---

### Post by wieman01 on 2007-11-23
Please post the results of:
> sudo iwlist scan
Does Network Manager detect your network?

---

### Post by jonnywombat on 2007-11-23
What version of ubuntu are you using??

 I have a belkin F5D5070B which runs the RT73 chip set.. this is natively supported in Gutsy (7.10) but not in any earlier version.. I gave up trying to make it work with WPA in Feisty but I did get WEP working (there is a how to somewhere on here but I have lost the link (will post if I find it)..

In the end for me it was a blessing when Gutsy came out!!

---

### Post by teuma on 2007-11-23
here it is

```

ryann@ryann-laptop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     No scan results
ryann@ryann-laptop:~$ 

```

Do you suggest upgrading to 7.10 and try WPA.

It has to be WPA

---

### Post by wieman01 on 2007-11-23
> **teuma said:**
> here it is

```

ryann@ryann-laptop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     No scan results
ryann@ryann-laptop:~$ 

```

Do you suggest upgrading to 7.10 and try WPA.

It has to be WPA
Yes, upgrading should help. It saves you a lot of trouble. No scan results generally mean that the device is not working.

---

### Post by Austin_KW on 2007-11-23
rt73 howto incl. WPA instructions
 [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

