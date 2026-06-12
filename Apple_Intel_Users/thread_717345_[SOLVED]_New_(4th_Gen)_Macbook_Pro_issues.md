---
title: "[SOLVED] New (4th Gen) Macbook Pro issues"
date: 2008-03-06
forum: Apple Intel Users
---

### Post by MichaelSwengel on 2008-03-06
Has anyone been able to get Wi-Fi working on the newest (4th Gen, Penryn) Macbook Pro's?

It was running fine on my 3rd Gen - but there have been a few hardware changes since then.

The Wireless card is now Broadcom Wireless. Madwifi didn't seem to work here.

Has anyone had any luck with this? :confused: My wired connection is fine.

Also... Sound isn't working. Everything but those two things seem to be working great so far.

Any suggestions would be appreciated.

Thanks,
Michael

---

### Post by cyberdork33 on 2008-03-06
madwifi is for atheros-based cards, you have to used ndiswrapper and the windows driver from the Leopard DVD

It should be very similar to how it is done for the Macbook Air:
[https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7](https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7)

---

### Post by eitan on 2008-03-07
fyi:  i also just got a macbookpro (4th gen) which exhibits the same problems.
no sound and no wifi.  with hardy heron alpha 6.  main issues i have at the 
moment (aside from sound & wifi):
  - java 6 update 4 is broken.  need update 5 or revert to update 3.
  - pommed and gpomme versions in repository are 1.15.  only 1.16+ 
     support the 4th gen mbp's
/ eitan

---

### Post by wallace79 on 2008-03-24
hi!

I'm really interested in buying a MBP 4.1.

which are the still open issues with these machines?
-wifi?
-sound?
-hibernation/suspend?

Regards

Wallace

---

### Post by eitan on 2008-03-24
i got both wifi (with ndiswrapper) and sound (didn't do anything special outside the wiki instructions for santarosa notebooks) to work.

the main issues i have at this time are:
  - fn key not working
  - open office crashes x as soon as i touch any of the menus

thanks,
/ eitan

---

### Post by DrAma999 on 2008-03-24
Sound work just need to follow the wiki...wifi yes (ndiswrapper) without encryption, but no with wpa and wep protecttion.

---

### Post by manoloro on 2008-04-15
Hi,

I have a new MBP(4th Gen, Penryn) and my distro is a Gentoo 64 bits. I have followed all step to configurate my wifi but I can't. Is the module ohci  necesary? 

I give your some outs:

ndiswrapper -l
         bcmwl5 : driver installed
        device (14E4:4328) present

 lspci | grep Network
       0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 05)

Sorry for my poor english.

Regards!

---

### Post by cyberdork33 on 2008-04-15
> **manoloro said:**
> Hi,

I have a new MBP(4th Gen, Penryn) and my distro is a Gentoo 64 bits. I have followed all step to configurate my wifi but I can't. Is the module ohci  necesary? 

I give your some outs:

ndiswrapper -l
         bcmwl5 : driver installed
        device (14E4:4328) present

 lspci | grep Network
       0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 05)

Sorry for my poor english.

Regards!If the same bug exists in Gentoo, there was a problem with ndiswrapper conflicting with the ssb module in Ubuntu Hardy. You might look into that.

ohci is probably for usb or firwire support.

---

### Post by manoloro on 2008-04-16
When I have booted my mbp today, I have found a new interface: wlan0. :D. I can connect with my router and I can do ping to the gateway, but I still without internet :( . 

Regards

---

### Post by cyberdork33 on 2008-04-16
> **manoloro said:**
> When I have booted my mbp today, I have found a new interface: wlan0. :D. I can connect with my router and I can do ping to the gateway, but I still without internet :( . 

RegardsWell, if you can ping the gateway, and you have an IP, I would guess that there is a problem on the Router side.

---

### Post by plasmatonic on 2008-04-16
Power cycle your modem and router by simply unplugging the power on each device, allowing a short period to discharge, and plug it back in.

If you still have no internet, log into your router and verify you have an IP address from the WAN. If not, are you able to get online by plugging your modem directly into an ethernet jack to test? Else call your provider to ensure everything is ok on their end.

---

### Post by manoloro on 2008-04-16
Ups, I have limited the numbers of user in the routers. Thank you for the help.

Regards

---

### Post by tamytt on 2008-04-30
Can I download this window driver from somewhere? I don't have my Mac OX disk with me and wish to get wireless working.

---

