---
title: "MacBook Pro 8.1 WiFi Problem"
date: 2012-12-06
forum: Apple Hardware Users
---

### Post by machumamu on 2012-12-06
I have a MacBook Pro 8.1 and had the wifi working just swell up until an hour ago... Now nothing having to do with wifi shows up anywhere. I tried downloading ndiswrapper but dont know how to open it. It happened after I rebooted after waking up from being suspended and poof! no wifi....

Ubuntu 12.10 64bit on MacBook Pro 8.1 Intel i5

---

### Post by trogdor1138 on 2012-12-06
May I ask why you are using ndiswrapper?

I believe we share the same Wi-Fi controller, the Broadcom 4331. Generally, it's recommended to use the b43 driver for this chip. However, Broadcom has been slow to support open-source software, so this driver depends on proprietary firmware available only in their closed-source drivers.

This means that Ubuntu can't distribute the appropriate firmware with the OS. Instead, you need the b43-fwcutter utility to extract the firmware and place it where the driver expects to find it.

I'm guessing Wi-Fi is your primary network connection, and you're grabbing files on a different machine. In this case, simply follow these instructions to get everything you'll need: [http://linuxwireless.org/en/users/Drivers/b43#Other_distributions_not_mentioned_above](http://linuxwireless.org/en/users/Drivers/b43#Other_distributions_not_mentioned_above)

---

### Post by machumamu on 2012-12-06
I read somewhere to use ndiswrapper and use it to change a driver file, idk.. I was looking everywhere, and tried everything to get it working again. I got it working easily in the beginning, but now it just went away. Ok, now please forgive me, but does "/lib/firmware" need to be replaced and the directory in which the downloaded file needs to be inserted there? And, same thing with "$FIRMWARE_INSTALL_DIR"? Please forgive me, I am still learning.

---

### Post by coffeecat on 2012-12-06
> **machumamu said:**
> I read somewhere to use ndiswrapper

That's always the problem with "somewhere" on the internet. There's a lot of misguided information out there, unfortunately.

> **machumamu said:**
> please forgive me, but does "/lib/firmware" need to be replaced and the directory in which the downloaded file needs to be inserted there?

Don't try to replace system directories. Installing the Broadcom firmware is very easy, but first you need to double-check that you do have the Broadcom chipset that trogdor1138 mentions. Have a look at this Ubuntu community documentation page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

There's far more there than you need, so first identify your wireless chipset as described under "Identifying Your Broadcom BCM43xx Chipset (PCI)".

If yours is a Broadcom, check it against the b43 list. If b43 is appropriate for you, go to:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29-1](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29-1)

You'll need to be connected to your router with an ethernet cable for this bit. If you can't establish a wired connection, you can install the firmware from the Ubuntu CD, or by downloading the package via another computer, as here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Hope that helps. If it turns out that your Macbook has another Broadcom chip or another make of wireless, post back and someone will be able to help.

---

### Post by machumamu on 2012-12-06
Thank you coffeecat, worked like a charm... :D

---

