---
title: "Will Netgear Wireless Adapter work with Ubuntu 7.04?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-25
Here below is the description of my Netgear Wireless adapter. The specific model I purchased is WG111v2.  Please let me know if it can be configured to work with Ubuntu 7.04:


The NETGEAR 54 Mbps Wireless USB 2.0 Adapter WG111 gives you ultimate mobility in your
office or while you are traveling. It frees you from traditional Ethernet wiring and helps you create
a wireless network for sharing your broadband Internet access among multiple PCs in and around
your home. It is designed for PC computers running Microsoft® Windows®. It is a USB 2.0 device
and is backwards compatible with USB 1.1 ports.

---

### Post by Seisen on 2007-06-25
It might but you have to use ndiswrapper to ge it to work.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

---

### Post by Songwind on 2007-06-25
We have one of those, it works nicely, but Seisen is right - it requires NDISWrapper.

---

### Post by swarup on 2007-06-25
> **Songwind said:**
> We have one of those, it works nicely, but Seisen is right - it requires NDISWrapper.

Many thanks to both of you. That's great news!  I'll try getting NDISWrapper now and see if I can get it up and running.

---

### Post by swarup on 2007-06-25
I went to the site NDISWrapper. Here below is the Netgear adaptor with four different distro options. Please let me know if the Netgear item I found is the correct item, and if so, then which of the below distro options would be proper--if any--for Ubuntu 7.04. I could not find one that says it is directly for Ubuntu 7.04.

It gives various additional info which I do not know about, such as the chipset and the "usbid". Also, the first entry says "made in Taiwan" whereas my unit is made in China.

#1 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter (made in Taiwan)

    *
      Chipset: Realtek RTL8187
    *
      usbid: 0846:6a00
    *
      Distro: Ubuntu 6.06 LTS, kernel 2.6.15-25
    *
      Driver: (BAD) Realtek RTL8187L Win98SE/WinME driver v 1.221 from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187) - DriverVer 5.1221.0412.2006. Uses name netrtuw.inf. This works for a while, but after ~5 minutes of ssh/file copy traffic, the machine hung and had to be rebooted (reproducibly).
    *
      Driver: (BAD) Netgear wg111v2 1.40 (?) from [http://kbserver.netgear.com/release_notes/D102948.asp](http://kbserver.netgear.com/release_notes/D102948.asp) (labeled as 2.00 on [http://kbserver.netgear.com/products/wg111v2.asp](http://kbserver.netgear.com/products/wg111v2.asp)) - DriverVer 5.1213.06.0327. Ndiswrapper will load this driver successfully and find the device, but iwlist scans will fail and the device won’t associate.
    *
      Other: MUST rmmod, or blacklist kernel driver r8187 (in /etc/modprobe.d/blacklist) - it will claim the device before ndiswrapper gets a chance. The r8187 driver will associate with an AP and appear to work, but won’t actually transmit any data.

#2 Card: NETGEAR WG111 version 2 802.11g Wireless USB2.0 Adapter

    *
      Chipset: Prism54 (Intersil 3886 and NetChip NET2280) or
    *
      Chipset: ? (Intersil 3887 without NetChip NET2280) [http://yoshiyo.ath.cx/seb/images/wg111_4.jpeg](http://yoshiyo.ath.cx/seb/images/wg111_4.jpeg)
    *
      usbid: 0846:4240 (both Chipsets !)
    *
      Driver: Netgear windows driver Version: NETGEAR, Inc.,10/05/2004, 2.1 from [http://www.netgear.com](http://www.netgear.com) or shipped with the setup CD. To get the driver, unzip it. The ndis drivers are in the ndis directory. Used kernel Running Slackware v10.1 (kernel 2.6.10) ndiswrapper ver 1.1rc3 . There is a native driver for Prism54 that is working on USB support. View its status at [http://www.prism54.org](http://www.prism54.org) Prism54.org
    *
      Other: With the driver for Sitecom WL-142, this device supports WPA2, keeps the device “alive” (with driver from netgear, device stops working after a while) and correct some connection problem : [http://www.sitecom.com/showdownload.php?id=1928](http://www.sitecom.com/showdownload.php?id=1928). Note that the device ID for Sitecom is different, so you need to create alias for it for WG111, e.g., with ‘ndiswrapper -d 0846:4240 wlanuig’, after which ‘ndiswrapper -l’ should show ‘hardware present’.
    *
      Other: Works nearly well (several daily crashes in Summer 2005).
    *
      Distro-specific: Debian Sarge 2.6.8.1, Ndiswrapper 0.10 Distro-specific: Debian Sid 2.6.8.X, Ndiswrapper 0.12+1.0rc2-1, without rfmon
    *
      Other project without ndiswrapper : [http://jbnote.free.fr/prism54usb/](http://jbnote.free.fr/prism54usb/) (seems incomplete in january 2006 - not supporting WEP or WPA).

#3 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

    *
      usbid: 0846:4240 Distro-specific: Ubuntu 4.10 “The Warty Warthog”
    *
      Driver: Netgear windows driver Version: NETGEAR, Inc.,06/04/2004, 3.0.18.201 shipped with the setup CD
    *
      Other: “ndiswrapper -l” produces “hardware not present” for the “netwg111” driver, but the adapter works anyway

#4 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

    *
      usbid: 0846:4240 Distro: Gentoo 2005.1, kernel 2.6.12-r6
    *
      Driver: Windows XP driver from Windows Update / preinstalled?, Version: 3.0.18.201. Taken from Windows directory (XP full pathname: right-click Device Manager’s Netgear icon, Properties, Driver details)
    *
      Other: ndiswrapper 1.5. athlon-xp, (preempt=yes,smp=yes). Reboot was necessary to get lights a-blinkin. Logging claimed modprobe error -22 until after reboot. Currently misconfigured with setting tx_power failed (80000005) but hope to resolve.

---

### Post by Songwind on 2007-06-25
use the command "lsusb" while you have the adapter plugged in.  It will show you the USB ID of the device and you can compare it to the ones listed on the page.

---

### Post by swarup on 2007-06-25
I found some more. Perhaps one of these would be the proper one, for my Netgear WG111v2 with Ubuntu 7.04:

#1 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

    *
      Chipset: Realtek Semiconductor Corp. RTL8187L
    *
      usbid: 0846:6a00 Distro-specific: Debian “sid”
    *
      Driver: realtek-driver for Windows 98SE/ME from [http://www.realtek.com.tw/](http://www.realtek.com.tw/) look for RTL8187L or take Win-ME-driver from 1.4.0 driver from Netgear
    *
      Other: Distro: Kanotix, kernel Linux version 2.6.17.6, ndiswrapper utils version: 1.8 ndiswrapper driver version: 1.21. Some XP/2K drivers could see ESSID but didn’t transfer bytes, others did not even scan ESSID of AP. With ME-driver it seems to work quite well.

#2 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

    *
      usbid: 0846:6a00 Distro-specific: Debian “sid”
    *
      Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD
    *
      Other: tested debian-kernel 2.6.8 with ndiswrapper 1.1 and vanilla-kernel 2.6.12.3 with ndiswrapper 1.2 - everything works fine as far as i can tell.

#3 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

    *
      usbid: 0846:6a00
    *
      Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD
    *
      Distro-specific: SuSE 10.0
    *
      Other: tested SuSE Kernel 2.6.13-15.11 with ndiswrapper 1.21 - 128bit WEP and data transfer work fine. Ndiswapper 1.17 and previous kernel did not work (flaky operation + kernel oops).

#4 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

    *
      Chipset: Realtek Semiconductor Corp. RTL8187L
    *
      usbid: 0846:6a00
    *
      Driver: Realtek Windows XP drivers Version: Realtek Semiconductor Corp.,05/04/2005,5.112.05.0504 from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187) (2.00 2005/05/31)
    *
      Other: Extract ZIP file and install driver in WINXP directory. Kernel 2.6.12.6 with WE 18 and ndiswrapper 1.2/1.4 &#8658; 128 bit WEP works perfectly, but WPA-PSK TKIP seems not to work with current wpa_supplicant version

---

### Post by swarup on 2007-06-25
> **Songwind said:**
> use the command "lsusb" while you have the adapter plugged in.  It will show you the USB ID of the device and you can compare it to the ones listed on the page.

I see. Ok-- I'll try this now.

---

### Post by swarup on 2007-06-25
> **Songwind said:**
> use the command "lsusb" while you have the adapter plugged in.  It will show you the USB ID of the device and you can compare it to the ones listed on the page.

I tried that command, but only got the following reply:

swarup@swarup-laptop:~$ Isusb
bash: Isusb: command not found

---

### Post by swarup on 2007-06-25
I also tried the same "Isusb" command with "sudo" before it, but it didn't make any difference.

swarup@swarup-laptop:~$ Isusb
bash: Isusb: command not found

swarup@swarup-laptop:~$ sudo Isusb
Password:
sudo: Isusb: command not found

---

### Post by honda on 2007-06-25
It should be lsusb with a small ' L'  not a capital i

---

### Post by swarup on 2007-06-25
Would someone familiar with this kindly review the various options I pasted above from NDISwrapper and let me know which one is proper for using with Ubuntu 7.04? Thanks!

---

### Post by swarup on 2007-06-25
> **honda said:**
> It should be lsusb with a small ' L'  not a capital i

Thanks-- I hadn't seen your reply as it was on the 2nd page. 

I followed your direction with small L, and got the following response from terminal:

Bus 001 Device 016: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

So in view of this information, which of the options I listed above from NDISwrapper is the proper one for Ubuntu 7.04?

---

### Post by kevdog on 2007-06-25
This is what I found based on your information (sounds like the results may be unpredictable -- good luck!)

#
Card: NetGear, Inc. WG111 WiFi (v2)

    *
      Chipset: RTL8187
    *
      usbid: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
    *
      encryption: using WEP- 128bit
    *
      Driver: 04/04/2006,5.1221.0412.2006 (copied from netrtuw.inf); Realtek drivers v1221. (these are no longer on the realtek website google them); filename: rtlsetup-8187(1221)(0412).zip WIN98 folder; url: [http://www.majorgeeks.com](http://www.majorgeeks.com) (this is where I got it)
    *
      Other: The XP drivers did not work in this package, but the WIN98 ones did. In my experience, any driver for this adapter will load fine in ndiswrapper, but so far this is the only one that I got to find my AP. Other drivers even detected other AP’s, but not mine (which was closer than the detected ones). I also could not set the ESSID with other drivers. This one has neither of those problems.

---

### Post by DBStevens on 2007-06-25
I'd try:

Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD

And if that didn't work look into the WinXP driver on the Realtek site.

But hey can't say for certain.

---

### Post by honda on 2007-06-25
There is an ongoing project that is implementing an open source driver for that chipset at
[http://rtl-wifi.sourceforge.net/wiki/Main_Page]("http://rtl-wifi.sourceforge.net/wiki/Main_Page")
But using it requires compiling from source, and a bit worse, deleting or renaming a couple of modules in your kernel (see the installing link). A bit tricky but it can be done. I have a PCI rtl8185 based card that I finally got to work using that driver, ndiswrapper never worked for me (but my card was a pci card with rtl8185 chipset). I would try ndiswrapper first.

---

### Post by swarup on 2007-06-25
Many thanks for each of your kind replies (the prior three). 

I am hoping that someone like Songwind (who wrote already in this thread) will tell me which one they used from NDISwrapper because he already has this Netgear item working perfectly on his system. So if I use what he used, then there is no guesswork involved. It is obvious that something from NDISwrapper will work for me, because it worked for Songwind. So its just a question of which one.

All the items from NDISwrapper I posted above are for the same Netgear item, the WG111v2. I think it is pretty clear that this is the one I need. But each NDISwrapper entry I posted above is for a different linux distro. THAT is what I am in doubt about. Because none of them was listed for Ubuntu 7.04. The closest thing I found was for Dapper (6.06). Is that the one I should use? Or is perhaps another distro listed above closer to Ubuntu 7.04?

---

### Post by swarup on 2007-06-25
I'm wondering if anyone has experience with this particular Netgear wireless adapter, the WG111v2, with Ubuntu 7.04-- and could tell me which of the links on NDISwrapper I should use to get the WG111v2 working. I've listed the ones above, which seemed most likely when I went to the NDISwrapper website. But without someone's concrete experience, it is somewhat guesswork which one works with Ubuntu 7.04. If someone could tell me which worked for them, it would be a big help. Thanks!

---

### Post by uputer on 2007-10-06
swarup, did you get your usb adapter to work yet?  

Check this link out:
[http://ubuntuforums.org/showthread.php?t=493958&highlight=Netgear+WG111v3](http://ubuntuforums.org/showthread.php?t=493958&highlight=Netgear+WG111v3)

It all depends on two things from what I can tell:
1) Which kernel you're using - most of the chipset/driver webpages list the updates and changes in various kernels
2) which chipset is in your usb dongle - as this effects which driver you use and how complex the configuration is, although, most seem to need ndiswrapper.   

I found virtually all of the so-called Linux drivers not working all that well yet.   Perhaps, Prism ones but it's mostly older adapters or cards that use the Prism chipset.   But, Prism seems to have advanced Linux drivers more than other companies.

You need to find out which chipset your Netgear uses:
I would try:
# lsmod | grep prism (to see if it's the prism chipset)
or
# lsmod | grep rtl8187  (to see if it's the realtek chipset)
If neither bring anything up, try rtl8185 and then rtl8180

---

### Post by kennedyjch on 2007-11-12
Odd. My NetGear WG111v2 worked "out of the box", "plug-'n-play" in my Ubuntu 7.04 installation. Have not installed ndiswrapper... 

Only problem I have is that after several hours it has the habit of dropping the connection and the only way I've found to bring it back to life is to reboot. Any suggestions to this effect would be wonderful.

---

### Post by Songwind on 2007-11-12
> **kennedyjch said:**
> Odd. My NetGear WG111v2 worked "out of the box", "plug-'n-play" in my Ubuntu 7.04 installation. Have not installed ndiswrapper... 

Only problem I have is that after several hours it has the habit of dropping the connection and the only way I've found to bring it back to life is to reboot. Any suggestions to this effect would be wonderful.

Yeah, once we got upgraded to Feisty (then Gutsy) we had the same experience of not needing ndiswrapper.

Have you tried unplugging and replugging the adapter?  I have not had the same issue you are describing, but when it does manage to lose connection, a quick replug seems to take care of it.

---

### Post by Pro75357 on 2007-12-02
nvm

---

### Post by ethan1701 on 2007-12-22
> **kennedyjch said:**
> Odd. My NetGear WG111v2 worked "out of the box", "plug-'n-play" in my Ubuntu 7.04 installation. Have not installed ndiswrapper... 

Only problem I have is that after several hours it has the habit of dropping the connection and the only way I've found to bring it back to life is to reboot. Any suggestions to this effect would be wonderful.

I've had the same exact issues, on Feisty and Gutsy. I'd be very happy to resolve this issue once and for all.

Any idea how I might do that?

-Ethan

---

### Post by GuitarRocker2562 on 2007-12-22
um, i use that but not NDISwrapper, works out of the box!

---

### Post by PS Nancarrow on 2008-01-11
I've been going 'round and 'round with this. I installed Xubuntu 7.04 on an older Dell Dimension l667r. My Netgear WG111v2 worked out of the box on that installation (as long as I plugged it in *after *the machine booted). Xubuntu wasn't getting any updates, so I switched over to Ubuntu 7.04. Again the WG111 worked out of the box. I had an ill-fated flirtation with OpenSUSE, decided to go back to Ubuntu, installed with the very same LiveCD as before--and now the WG111 won't work. I want to avoid using NDISwrapper, if at all possible. I'd like to plug it in and have it work. Like "out of the box" is supposed to work. I had my fill of programming on the command line back in the 80s with CP/M and MS-DOS; I'd really like not to have to do a lot of terminal programming just to get on the web with an old second-string computer. These irregular experiences with the same system is *really *making me question if Ubuntu is ready for prime time.

PS Nancarrow

---

