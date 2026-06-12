---
title: "configure wireless network for UBUNTU"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by ksimpson on 2006-05-25
I successfully installed UBUNTU today on a 60 GB partition of a 120 GB slave disk on a PC running Win2K.  The remaining 60 GB on the slave disk was formatted as NTFS. 

I have a wireless network established at home, and I'd like to configure (if possible) my new UBUNTU OS to this network. 

On another PC (Win2K only) I have a Motorola wireless broadband router (WR850G) broadcasting in infrastructure mode on channel 11, using 64 bit encryption.   On this PC, with Win2K/UBUNTU (when the Win2K OS boots up) I use a pen size USB adapter (AOpen IEEE 802.11b) to receive the wireless hi-speed internet connection.  I also have a couple folders shared, and can transfer files between the PCs.

When I installed UBUNTU, the installation did not automatically detect my network settings (it was looking for DHCP...?). ](*,) 

Does anyone have suggestions for configuring the wireless network?

Thanks,

Kent

---

### Post by joshrobinson on 2006-05-25
[QUOTE=ksimpson]I successfully installed UBUNTU today on a 60 GB partition of a 120 GB slave disk on a PC running Win2K.  The remaining 60 GB on the slave disk was formatted as NTFS. 

I have a wireless network established at home, and I'd like to configure (if possible) my new UBUNTU OS to this network. 

On another PC (Win2K only) I have a Motorola wireless broadband router (WR850G) broadcasting in infrastructure mode on channel 11, using 64 bit encryption.   On this PC, with Win2K/UBUNTU (when the Win2K OS boots up) I use a pen size USB adapter (AOpen IEEE 802.11b) to receive the wireless hi-speed internet connection.  I also have a couple folders shared, and can transfer files between the PCs.

When I installed UBUNTU, the installation did not automatically detect my network settings (it was looking for DHCP...?). ](*,) 

Does anyone have suggestions for configuring the wireless network?

Thanks,

Kent[/QUOTE]

is the usb wireless adapter found in system > administration > networking?

are you using WEP or WPA?

---

### Post by dmizer on 2006-05-25
first of all, we need to get your ubuntu to see your usb adapter.  checking at the [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29") does not list your adapter, so you may not be in luck with it.

you can try a different adapter, or you can search the web for information about making your adapter work.  i did a few cursory googles, but didn't find anything quickly.

if you are able to get ubuntu to see your usb stick, then it shouldn't be too much trouble to configure your network from there.  keep in mind that linux does not support keyprhase encryption (so far as i know), so you'll have to enter the hex version of your key in order to get the wep to work.

---

### Post by crispy_420 on 2006-05-25
Try looking [HERE]("http://linux-wless.passys.nl/").

It seems to be good summary about what cards are supported in linux and what driver is needed. I would go with a PCI card and not USB as they seem to have less support, not my experience (never tried), just what I have read.

Also if you live in the US try newegg.com for parts. They are quick and cheap.
Here is a real cheap one they have that is natively supported in Ubuntu.

[Foxconn WLL-3350]("http://www.newegg.com/Product/Product.asp?item=N82E16833194001")

[Driver Support]("http://linux-wless.passys.nl/query_part.php?brandname=Foxconn")

My laptop is running wireless from the same chipset as this and it works fine. It helps that the chipset maker gives out it's source for continued development. And as a user of linux I feel it is good idea to toss your money to companies willing to support you as a user. Again with my opinions.

---

