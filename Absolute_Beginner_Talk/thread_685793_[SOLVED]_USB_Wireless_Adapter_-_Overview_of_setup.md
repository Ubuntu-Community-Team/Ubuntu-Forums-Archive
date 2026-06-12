---
title: "[SOLVED] USB Wireless Adapter - Overview of setup?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-02-02
My Dell Optiplex GX620's wired connection works great. However I'd like the option of getting my Linksys WUSB12 USB wireless adapter to work as well.

I plugged it in and nothing happened. I opened Network Manager; a new 'Wired connection' appears, named 'wlan0', but after switching to this connection the internet doesn't seem to work.

After reading through some threads and googling I'm not really clear on exactly what I'm supposed to do to get this working. I gather it's something like:

- Install the manufacturer's drivers
 -or-
- Use 'ndiswrapper'
 -and/or-
- A whole bunch of other stuff

Can someone describe/point me toward an explanatory overview of how to set this up? And why is installing a USB wifi adapter so much different from, say, plugging in a thumb-drive and having it work? I mean I know I have to configure the *connection* to link to my router or whatever, but are all the drivers for these devices distinct and proprietary or something (as opposed to the standard protocol used for thumb-drives)?

Thanks.

---

### Post by Cato2 on 2008-02-03
See [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) for overview and list of supported cards, and search the forums for 'WUSB12' for help with this device.

USB flash drives all look exactly like hard drives to the OS (the electronics on the drive make this happen) so they work with a single driver.  Most hardware you plug into Linux is fairly well supported, and there are open source drivers that are maintained pretty well.

WiFi is difficult because, for legal/regulatory reasons, most manufacturers don't release source code or detailed docs on the WiFi card or USB stick.  Hence the Linux developers must 'decrypt' the details of the device by reverse engineering, or in some cases just use NDISwrapper, which takes a Windows 'NDIS' network driver and wraps it for use by Linux.

This device doesn't look that well supported, so if you spend more than a few hours on this it may be better to check the WiFi hardware lists under the HOWTO and pick one that is more likely to work.  Be sure to check for WPA capability under Ubuntu as that's the hardest part and required for a secure setup.

If it helps, I have a 3Com USB WiFi stick that works pretty well with Ubuntu - model is 
3CRUSB10075.

One other tip - if you have trouble with NetworkManager for WiFi, try installing 'wicd' which is an alternative tool that works pretty well.

---

### Post by jjsonp on 2008-02-03
I got it working with the following steps:

    *  Downloaded the Windows device drivers for the adapter
    * Installed ndisgtk via Synaptic.
    * Ran 'gksudo ndisgtk' and installed the driver (device's .inf file).
    * Plugged in the device, and configured its connection via Network Manager. 

I tried it in the reverse order (plugging in the USB adapter first) and this did *not* work.

---

