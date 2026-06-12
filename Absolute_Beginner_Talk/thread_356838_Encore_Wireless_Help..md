---
title: "Encore Wireless Help."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Teh Dust on 2007-02-08
My mother recently got a hold of a old computer. <1ghz celeron processor and 256mb RAM. Rather than slowing it down with windows, I decided to load up ubuntu 6.10 to make it run smoother than it would with windows.

However, It came with a usb wireless adapter, a Encore ENUWI-G-ZDPR. This device has been giving me trouble. Ubuntu shows that the device is inserted and in the network settings shows a wireless device. When I went to the properties window to put in my router name "linksys" and WEP key it enables the device but does not send information back and forth from the router.

I searched around the forums and found some topics about the newer modle and ndiswrapper. I followed the directions and used first the newer drivers. It did not work so I found older drivers for the modle and attempted to install it with ndiswrapper.

I have two files in the driver folder ZD11UXP.inf and ZD11UXP.sys
This is what I put into terminal
```
sudo ndiswrapper -i ZD11UXP.inf
ndiswrapper -l
```
The list told me this:
```
Installed ndis drivers:
zd11uxp driver present, hardware present
```
I then read that to start the driver I should put this into terminal which I did.
```
sudo depmod -a
sudo modprobe ndispwrapper
```
The howto then said that by now the lights on the device should be blinking which they were not. I checked anyways to see if the device was sending a signal which it was not.

I checked around the forums a bit more and found nothing. If anyone can give me some help it would be greatly appreciated.

---

### Post by RomeReactor on 2007-02-09
Hi. After the steps you mentioned, you should also write in a terminal

```
sudo ndiswrapper -m
```

This will load ndiswrapper automatically when the wireless interface is used. Then

```
sudo gedit /etc/modules
```

When Gedit opens, write **ndiswrapper** at the end of the file (to load ndiswrapper automatically at boot time). Save and reboot.

---

### Post by Teh Dust on 2007-02-09
Thank You Rome. However, after doing what you have said, the device still fails to work. I looked arround in the network tools area and found that I only have 2 connections: lo, and eth1. Any other ideas or should I just go out and buy a newer device?

Also, after doing some more research, I have seen that some people have been able to use Encore usb devices with routers that are not encrypted. I have not tried taking off the WEP key and trying it yet since I am currently not at the computer but is there a way to do this and keep using WEP?

---

