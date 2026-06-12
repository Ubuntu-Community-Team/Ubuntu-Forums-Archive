---
title: "Airport Extreme Card Driver"
date: 2006-08-01
forum: Apple PPC Users
---

### Post by MacintoshMan on 2006-08-01
Is there a airport Extreme card driver in the newest version of ubuntu? Because when I try to configure the airport adress in etho1 it never connects. [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) I found that on digg.

---

### Post by avtolle on 2006-08-01
I have no familiarity with wireless, the Airport Extreme card, etc., but understand from reading threads on the Forum that this is a problem faced by many. [http://www.ubuntuforums.org/showthread.php?t=213661&highlight=airport+extreme](http://www.ubuntuforums.org/showthread.php?t=213661&highlight=airport+extreme) deals with this issue, the latter posts probably will be most informative to you. HTH.
The kernel referenced in your post is not used in 6.06. I recall reading somewhere that some of the "fixes" in the cited kernel have been patched to the Dapper kernel by the devs. So, it seems that to find out, you would need to install 6.06, then do the updates (including the kernel ones), and then see if your Airport Extreme card works.

---

### Post by avtolle on 2006-08-01
[http://www.ubuntuforums.org/showthread.php?t=213052](http://www.ubuntuforums.org/showthread.php?t=213052) might also provide some help.

---

### Post by rasec on 2006-08-01
There is driver support in dapper's kernel, and it goes by the name bcm43xx. It does not, however, come with a firmware. Search for forum for bcm43xx firmware and that should give you a head start. Also, once you got your firmware installed, you may be interested in a program called network manager and its frontends nm-applet and knetworkmanager depending on whether your using gnome or kde.

---

### Post by AlphaMack on 2006-08-04
The firmware you are looking for is at this location in OS X:

/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2

Copy that file over to Ubuntu and use bcm43xx-fwcutter to extract it to /lib/firmware.

---

### Post by blixel on 2006-08-09
> **alphasubzero949 said:**
> Copy that file over to Ubuntu and use bcm43xx-fwcutter to extract it to /lib/firmware.

Where does bcm43xx-fwcutter come from?  I searched Syanptic for "fwcutter" and then "cut" and didn't come up with anything.

---

### Post by icase81 on 2006-08-09
> **blixel said:**
> Where does bcm43xx-fwcutter come from?  I searched Syanptic for "fwcutter" and then "cut" and didn't come up with anything.

You need to make sure that you have the universe repository enable in Synaptic before it will show up. I was pulling my hair out cuz I couldn't find it, but once I did that it worked OK. 

I'm still having issues with my AP-E in 6.06 though. It is active and iwconfig appears right... but I get no connection via nm-applet and cant get an address or anything but iwconfig lists the proper ESSID and what not.

---

### Post by blixel on 2006-08-09
> **icase81 said:**
> You need to make sure that you have the universe repository enable in Synaptic before it will show up. I was pulling my hair out cuz I couldn't find it, but once I did that it worked OK. 

I'm still having issues with my AP-E in 6.06 though. It is active and iwconfig appears right... but I get no connection via nm-applet and cant get an address or anything but iwconfig lists the proper ESSID and what not.

Thanks, I added the repository and found the bcm43xx-fwcutter program.  When I run it against my AppleAirPort2 file, it kind of works but I get an error.  (Appears to be an error anyway.)


[INDENT]fwcutter can cut the firmware out of AppleAirPort2
  filename :  AppleAirPort2
  version  :  3.90.34.0.p16 (404.2)
  MD5      :  7200d1aef5f413ebc811046d068b40dc

WARNING! This firmware doesn't include support for 802.11a cards.
WARNING! Use this firmware only for 802.11b/g cards.

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...[/INDENT]

I copied the bcm43xx_* files over to /lib/firmware/2.6.15-23-powerpc anyway and then rebooted.

iwconfig shows the Airport Extreme card ... (but it was already doing that before without the firmware)

[INDENT]eth1      IEEE 802.11b/g  ESSID:"skizzik"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]

The main thing I notice there is the Access Point: Invalid field.

I went ahead and configured the card anyway ... doesn't work of course.  Sigh...

---

### Post by icase81 on 2006-08-09
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

Use that driver there. Thats what I'm using and for whatever reason its now working perfectly. I'm running an iBook G4 with an Airport Extreme to a WRT54G with 64bit WEP enabled. All I'm using is the System -> Administration -> Networking control panel deal to enter the WEP key and ESSID and it works great.

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Thats the How-To I used to get everything working, except network-manager didn't work for me at all with the wifi.

---

### Post by AlphaMack on 2006-08-10
If you guys have Wifi-Radar installed, get rid of it as it conflicts with the Broadcom driver.  Network Manager should then work.

Also when you guys try to connect be sure your key is 64/128 bit (as you see it in the drop down menu).

---

### Post by icase81 on 2006-08-10
> **alphasubzero949 said:**
> If you guys have Wifi-Radar installed, get rid of it as it conflicts with the Broadcom driver.  Network Manager should then work.

Really? I didn't have any issues using Wifi-Radar with mine...

---

### Post by AndrewShugg on 2006-08-13
I haven't got my iBook G4's AirPort Extreme wireless card working in Ubuntu 6.06 yet ... it's there, but I can't connect with it. ](*,) 

You may find the following helpful:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

I'm going to keep plugging away because until I get Airport working in Ubuntu, it's kinda pointless for me to leave OS X 10.4!

Cheers,

Andrew S.

---

### Post by tidris on 2006-08-13
There appears to be a bcm43xx bug that shows up in G5 machines with more than 1 GB of memory. Apparently the bcm43xx wireless chips can only address 1 GB of memory. Because of that, when the bcm43xx driver allocates DMA memory it asks the kernel to make sure the memory blocks are in the first 1 GB of physical address space. Unfortunately if the machine has more than 1 GB of RAM the PPC kernel can return memory blocks located above the first 1 GB of memory. When that happens the bcm43xx driver dies. That is all discussed in this thread:

[http://www.spinics.net/lists/netdev/msg02711.html](http://www.spinics.net/lists/netdev/msg02711.html)

---

### Post by rasec on 2006-08-13
tidris, does that problem still exist? Does it help when you force the kernel to use only 1 gig of ram when you boot it with "mem=1G" parameter? That thread that you linked to is 4 months old, so I suprised that the ubuntu devs haven't been keeping the driver up to date. By the way, my powerbook has 1.25 gigs and the bcm43xx driver works just fine, but then again it has a g4.

Andrew, are you trying to connect to a wpa encrypted network? If you are, I posted an updated libnm-util0 package that fixes network manager's problem of connecting to wpa networks in another thread a while back. Also, can you see if "iwlist eth1 scan" lists your access point, that should determine if your card is working.

---

### Post by tidris on 2006-08-13
> **rasec said:**
> tidris, does that problem still exist? Does it help when you force the kernel to use only 1 gig of ram when you boot it with "mem=1G" parameter? That thread that you linked to is 4 months old, so I suprised that the ubuntu devs haven't been keeping the driver up to date. By the way, my powerbook has 1.25 gigs and the bcm43xx driver works just fine, but then again it has a g4.


It happens on my dual G5 with 1.5 GB of memory and kernel 2.6.15-26-powerpc64-smp. When I try "sudo ifconfig eth1 up" I get this message "SIOCSIFFLAGS: Cannot allocate memory", Also the system log shows this message "bcm43xx: >>>FATAL ERROR<<<  DMA RINGMEMORY >1G (0x4e6e7000, len: 4096)".

As for the "mem=1G" parameter I will have to try that next and report what happens.

---

### Post by tidris on 2006-08-13
Ok, at the "boot:" prompt I used "Linux mem=1G" and now free reports only 1GB of total memory instead of the previous 1.5GB. Also, "sudo ifconfig eth1 up" no longer returns an error message and the system log no longer shows the bcm43xx fatal error message either.

However, when I try "sudo iwlist eth1 scan" I get the message "eth1      Interface doesn't support scanning : Bad address" and I am not sure what to make of it.

---

### Post by rasec on 2006-08-13
Did you install the firmware for the airport card? Also, what does dmesg show after you "sudo modprobe -r bcm43xx; sudo modprobe bcm43xx"? If all else fails, you might want to try the latest 2.6.17.8 kernel.

---

### Post by tidris on 2006-08-14
> **rasec said:**
> Did you install the firmware for the airport card? Also, what does dmesg show after you "sudo modprobe -r bcm43xx; sudo modprobe bcm43xx"? If all else fails, you might want to try the latest 2.6.17.8 kernel.

Yes, I had installed the firmware. I downloaded the wi_apsta.o file then used bcm43xx-fwcutter on it, then copied all the resulting bcm43xx*.fw files to /lib/firmware. 

The dmesg output after "sudo modprobe -r bcm43xx; sudo modprobe bcm43xx" was this:

[13721.872883] ieee80211_crypt: registered algorithm 'NULL'
[13721.876496] ieee80211: 802.11 data/management/control stack, git-1.1.7
[13721.876504] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[13721.888015] bcm43xx driver

---

### Post by AndrewShugg on 2006-08-14
> **rasec said:**
> Andrew, are you trying to connect to a wpa encrypted network? If you are, I posted an updated libnm-util0 package that fixes network manager's problem of connecting to wpa networks in another thread a while back. Also, can you see if "iwlist eth1 scan" lists your access point, that should determine if your card is working.

Haven't tried yet, I will probably be able to do so tomorrow.  Is your update for Network Manager in a package repository somewhere yet?

Andrew S.

---

### Post by rasec on 2006-08-14
tidris, I'm out of ideas. 

Andrew, the package is located here: [http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa)

---

### Post by AndrewShugg on 2006-08-29
> **rasec said:**
> Andrew, the package is located here: [http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa)


Thanks, I will finally try that out.  However I did look at the link to Launchpad to try to vote for your patch, and for some reason I wasn't able to actually do it ... will try again later.

Actually looking at the launchpad bug #52922 now, it seems the problem has been fixed upstream, but don't know yet if the fix will be brought back to dapper.  Any suggestions on how we can encourage this?

[INDENT][     **Re: libnm-util0 for network-manager on ppc does not work with wpa passphrases**     ]("https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/52922/comments/1")      from [sam tygier]("https://launchpad.net/people/samtygier")     at 2006-08-23 20:53:22 UTC   
[FONT=monospace]this looks like the issue mention on the NM mailing list.[/FONT]
[FONT=monospace] [http://mail.gnome.org/archives/networkmanager-list/2006-August/msg00023.html](http://mail.gnome.org/archives/networkmanager-list/2006-August/msg00023.html)[/FONT]
[FONT=monospace]  the patch in that thread was commited[/FONT]





[     **Re: libnm-util0 for network-manager on ppc does not work with wpa passphrases**     ]("https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/52922/comments/2")      from [CJP]("https://launchpad.net/people/rasecjp")     at 2006-08-24 01:14:51 UTC   
[FONT=monospace]It is, I contacted the debian maintainer and they were the ones that fixed it. Hopefully the ubuntu maintainter will backport it to dapper.[/FONT]

[/INDENT]  


Cheers

Andrew S.

---

### Post by AndrewShugg on 2006-08-29
> **rasec said:**
> Andrew, the package is located here: [http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa)

Now here's the rub ... I don't even have network-manager installed on this system!  So the fixed libnm-util0 package won't necessarily fix the problem, as I do not have any version of that package installed.

I might install network-manager-gnome anyway and give it a whirl with your fixed package.

Andrew S.

---

