---
title: "Networking with Ubuntu on Intel iMac"
date: 2009-06-11
forum: Apple Hardware Users
---

### Post by bheibert on 2009-06-11
Hi,

On my iMac in MacOS X I connect to my wireless network using Airport.
Although Apple has drivers for Windows for Airport as far as I know they don't have Linux
So what do I do?

I want to be able to access the internet via Airport. I think I have a Airport Extreeme.

Is there any support for Airport on Linux?

Thanks,

Brian

PS: I have a Intel iMac and a MacBook Pro
and I installed Ubuntu onto my Intel iMac

---

### Post by pxwpxw on 2009-06-11
Ubuntu has drivers for the Apple Airport chip, depending on Mac model and ubuntu version.

MactelSupportTeam/CommunityHelpPages
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

In ubuntu, get the wireless chip name this way -
```

	lspci | grep Net

```

See the MacBook Pro installation for wireless setup, but it varies.
The Imac installation info is incomplete, but may be identical for the same wirless chip.
Depends on your Mac model.

---

### Post by bheibert on 2009-06-12
Thanks I will look into this.

I appreciate the help.

Brian

---

### Post by bheibert on 2009-06-12
Hey,

I went to that website 
MactelSupportTeam/CommunityHelpPages
[https://wiki.ubuntu.com/MactelSuppor...unityHelpPages](https://wiki.ubuntu.com/MactelSuppor...unityHelpPages)

But couldn't find information on airport

Here is the information from Ubuntu about the wireless chip in my computer
04:00.0 Network Controller:Broadcom Corporation BCM4328 802.119/b/g/m (rev 05)

Where do I need to look to find out how to get internet working on my Intel iMac running Ubuntu Linux?

Brian

---

### Post by pxwpxw on 2009-06-13
> **bheibert said:**
> Hey,

I went to that website 
MactelSupportTeam/CommunityHelpPages
[https://wiki.ubuntu.com/MactelSuppor...unityHelpPages](https://wiki.ubuntu.com/MactelSuppor...unityHelpPages)

But couldn't find information on airport

Here is the information from Ubuntu about the wireless chip in my computer
04:00.0 Network Controller:Broadcom Corporation BCM4328 802.119/b/g/m (rev 05)

Where do I need to look to find out how to get internet working on my Intel iMac running Ubuntu Linux?

Brian
The BCM4328 is the Apple Airport chip, not specifically referred to as Airport in the Ubuntu help.

See the MacBookPro4-1Jaunty page - Wireless (Broadcom), Hardware Driver.

If this is not provided (in some Jaunty(904) releases for amd64), the driver code can be downloaded and compiled from Broadcom - 
   [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
(or google <Broadcom linux sta driver> )
After downloading, restart and recheck the Harware drivers, it my now appear - but if not, installation instructions are in the README.txt, but you may need help from previous threads about Broadcom installation. You will probably need to install linux-headers and the build-essential package before compiling.

---

### Post by cyberdork33 on 2009-06-15
You should be able to enable the "Broadcom STA" driver in System > Administration > Hardware Drivers

---

