---
title: "wlan0"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by cmfourie on 2006-07-25
I am new to linux and have been trying to get my belkin g usb installed. Can anyone help me. And if possible can any one give me the exact instructions (what to type in what order)

I have reached a point of frustration, I really want to use Linux but it is a struggle installing the right things.

Is there a distro that does plug and play

Thanks

-He who laughs last, is laughing at himself.-](*,)

---

### Post by lH)4~mK0e on 2006-07-25
Most newer distros will at the very least populate the device into the PCI bus so you can tell what device it is.  If you type in your terminal:

lspci

It should give you a list of devices installed in your machine even if the drivers or modules are not loaded.  Once you know the chipset you are dealing with, finding the right solution is easier.

---

### Post by Metacarpal on 2006-07-25
> **cmfourie said:**
> I am new to linux and have been trying to get my belkin g usb installed. Can anyone help me. And if possible can any one give me the exact instructions (what to type in what order)

I have reached a point of frustration, I really want to use Linux but it is a struggle installing the right things.

Is there a distro that does plug and play

Thanks

-He who laughs last, is laughing at himself.-](*,)

Which Belkin USB wireless device do you have?  You're looking for a part number or model number starting with F5D....

If it's a F5D6050, it's as easy as going into System > Administration > Networking, then selecting WLAN0 and clicking Activate.  You may also need to Configure WLAN0 to choose your network.

If it's a F5D7010, see [this how-to]("http://www.ubuntuforums.org/showthread.php?t=187004&highlight=F5D7010")

If it's a F5D7050, view [this thread]("http://www.ubuntuforums.org/showthread.php?t=210035")

If it isn't one of those... well, try doing a search of the forums with your model number. :)

---

### Post by djbentrem on 2006-07-28
I have a Belkin F5D7050 with the proper driver already installed using ndiswrapper. But it's not showing up in networking. Any suggestions? It's a used card so maybe I just got a bad one?

---

### Post by New-buntu on 2007-02-10
I've got the same chipset, but mine is IEEE 802.11b / 11 Mbps, Is it the same process?

---

