---
title: "Trendnet TEW-424UB on PPC?"
date: 2007-09-03
forum: Apple PPC Users
---

### Post by ivan09193 on 2007-09-03
Did I just make a huge mistake in buying the Trendnet TEW-424UB wireless USB adapter for my iBook?  Is there any way of getting it working (hopefully with WPA-PSK)?

EDIT:
I'm currently running 6.06, but I'm more than willing to upgrade if it will make the USB stick work.

---

### Post by walter_f on 2007-09-04
> **ivan09193 said:**
> Did I just make a huge mistake in buying the Trendnet TEW-424UB wireless USB adapter for my iBook?  Is there any way of getting it working (hopefully with WPA-PSK)?



That depends on the version of the USB adapter, which means, on the chipset used in it.

This list

[http://zydas.rapla.net/](http://zydas.rapla.net/)

says that there is a "TEW-424UB A" version using a ZyDAS ZD1211 chipset. In this case you would find Open Source (Linux) drivers for your stick here:

[http://sourceforge.net/projects/zd1211/](http://sourceforge.net/projects/zd1211/)

It might be as well be a completely different chipset and you could be out of luck when looking for a working Linux solution for this hardware.

Regards,

Walter.

---

### Post by ivan09193 on 2007-09-04
The output of lsusb is the followig:

Bus 001 Device 002:  ID 0bda:8189 Realtek Semiconductor Corp.
Bus 001 Device 001:  ID 0000:0000
Bus 002 Device 001:  ID 0000:0000

I don't think that this is a Zydas chipset.  Is there anyway of getting the adapter to work?  I can't return it, and half the reason I switched from Mac OS X was for improved support for Wifi with WPA encryption.  I'm willing to do just about anything to go wireless with WPA on this laptop.

---

### Post by walter_f on 2007-09-05
> **ivan09193 said:**
> The output of lsusb is the followig:

Bus 001 Device 002:  ID 0bda:8189 Realtek Semiconductor Corp.

I don't think that this is a Zydas chipset. 

Certainly not. 

I could not find a wireless chip called 8189 or RTL8189 on Realtek's web site, either.

Maybe this page might be helpful to identify the Revision of your device:

[http://www.trendnet.com/en/downloads/info/TEW-424UB.htm](http://www.trendnet.com/en/downloads/info/TEW-424UB.htm)

Walter.

---

### Post by walter_f on 2007-09-05
> **ivan09193 said:**
> The output of lsusb is the followig:

Bus 001 Device 002:  ID 0bda:8189 Realtek Semiconductor Corp.

I don't think that this is a Zydas chipset.


Finally I found at least something:

---
Okay, I bought a TRENDnet TEW 424UB Wireless USB adaptor. It's said to work with ndiswrapper.

#14
Card: Trendnet TEW-424UB

*
Chipset: Realtek RTL8187B
*
usbid: (as reported by lsusb ) 0bda:8189
*
Driver: [http://www.realtek.com.tw/downloads/...wnloads=tr](http://www.realtek.com.tw/downloads/...wnloads=tr) ue used winXP driver contained in RTL8187B_logo_6.1074.0406_silent_install.zip
*
Other: Works with WEP, have not tried other encryptions, using ndiswrapper from kernel 2.6.20 (Ubuntu)

...
---

Full discussion thread is here:
[http://www.tjrforum.com/showthread.php?t=3279](http://www.tjrforum.com/showthread.php?t=3279)

You may find something useful here, too:

[http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)
[http://rtl-wifi.sourceforge.net/wiki/FAQ](http://rtl-wifi.sourceforge.net/wiki/FAQ)

Regards,

Walter.

---

### Post by ivan09193 on 2007-09-05
I attempted to install rtl-wifi drivers.  I had a problem when I tried to use make:

ivan09193@ivan09193-laptop:~/rtl-wifi$ make
make -C /lib/modules/2.6.15-26-powerpc/build M=/home/ivan09193/rtl-wifi modules
make: *** /lib/modules/2.6.15-26-powerpc/build: No such file or directory.  Stop .
make: *** [modules] Error 2

I'm not sure why this happened.  Is there any way around it?

---

### Post by ivan09193 on 2007-09-06
First of all, is rtl-wifi actually supported for the powerpc architecture, and does it work with my wireless stick?  I haven't been able to install the drivers, although I have been able to remove the old ones as the wiki advised.

---

### Post by ivan09193 on 2007-09-10
Still unable to get wireless working.  I've installed build-essential and everything.

---

