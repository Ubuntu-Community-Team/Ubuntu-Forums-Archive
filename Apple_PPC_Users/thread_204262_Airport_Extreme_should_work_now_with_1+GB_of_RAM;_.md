---
title: "Airport Extreme should work now with 1+GB of RAM; Can anyone confirm?"
date: 2006-06-26
forum: Apple PPC Users
---

### Post by plush on 2006-06-26
As of the 2.6.15-25.43 update, the IOMMU changes in the kernel should allow for full DMA functionality.  Hence the Aiport Extreme's patches to make it work with people's computers with +1 GB of RAM should be implemented and functioning!  Unfortunately for me it is not, so I'd like to see if this is particular to my computer/airport extreme card/system/etc.

---

### Post by rasec on 2006-06-29
It works for me on my powerbook with 1280 megs of ram. 

Keep in mind that ubuntu/debian's kernel upgrade deb for the powerpc requries a little extra work to install, at least for me. I had to add an entry for the updated kernel in my yaboot.conf and run ybin after to get the new kernel to boot.

The bcm43xx driver is a little flaky though. It refused to work with network manager for me so I resorted to the old /etc/network/interfaces ifup/ifdown scripts and eventually got everything working.

---

### Post by plush on 2006-06-29
Thanks.  It may be specific to the 64bit kernel.  I'll try as you suggested.  Did you fw-cut your firmware or use the reverse engineered open source bcm43xx driver?  Could you give a like to the script that worked for you too if you don't mind, or perhaps send it to me?  Thanks

---

### Post by rasec on 2006-06-29
For the firmware I used fw-cut on wl_apsta.o which I found in one the millions of bcm43xx threads. 

As for the scripts that set up my network, there wasn't any. ifup/ifdown come preinstalled with ubuntu. You need to modify you interfaces file to control them. I'll explain how I modified my interfaces file below. What type of encryption are you using? I'm using wpa so this may be different for you.

First thing you need to do for a wpa network is run wpa_passphrase using your access point's ssid (name) as the first parameter and the pass phrase as the second. For example, lets assume your access point name is router and your pass phrase is "home router". Execute `wpa_passphrase router "home router"` and you should get back something that looks like this:

network={
        ssid="router"
        #psk="home router"
   
psk=563acdeb5056d3625e86b7e660505e7c4731f94a34b2077f5d248c40c46f9d82
}

Now edit /etc/network/interfaces and look for the lines:

auto eth1
iface eth1 inet dhcp

Immediately following the iface eth1 inet dhcp add:

        wpa-driver wext
        wpa-ssid router
        wpa-key-mgmt WPA-PSK
#       wpa-passphrase "home router"
        wpa-psk 563acdeb5056d3625e86b7e660505e7c4731f94a34b2077f5d248c40c46f9d82
}

Where the parameter to wpa-ssid if your router's name and wpa-psk is the PSK given to you from wpa_passphrase.

After you saved the interfaces file, run sudo ifdown eth1, followed by sudo ifup eth1. Now there should be some message displayed that its trying to request an ip address though dhcp or something. If it takes longer than a second press control-c to stop it, followed be sudo ifdown eth1; sudo ifup eth1 and it should connect instantly. It usually takes my laptop two ifup/ifdown cycles to connect to the network.

As means for debugging this, you can open up another terminal and do a `sudo wpa_cli -i eth1` while you run the ifup/ifdown scripts and you can see if wpa_supplicant working. 

If you need more info for configuring your interfaces file look at /usr/share/doc/wpasupplicant/README.modes

That should be it, at least it was for me.

---

### Post by rasec on 2006-06-30
If that /etc/network/interfaces method is too complicated, I finally figured out how to get NetworkManager to work. When either nm-applet or knetworkmanager asks you for a password for your network do not enter the plain text version, instead use the one that wpa_passphrase gives you. I don't know exactly why this is happening, but I noticed that when I changed the wpa-passphrase line in my interfaces file to use wpa-psk instead, my laptop was able to connect to the wireless network. So I tried using the ecrypted psk with network manager and it worked.

By the way, for the ppc network maintainer here, I suspect that this problem has something to do with the way that either wpa_supplicant or network manager generates the psk from the plain text pass phrase. I have no problems entering a plain text pass phrase on my dell, so I'm guessing either wpa_supplicant's or network manager psk generator isn't big endian friendly.

---

