---
title: "Wireless card detection"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by oli888 on 2007-11-08
I have used Damn Small Linux and have found the hardware detection to be perfect.

Unfortunately, on Ubuntu, my Belkin F5D6020 (original version, not 2 or 3) is detected.

I tried downloading the driver from the Belkin website, but there isn't an .inf file. There is a .in_ file, but renaming that and installing with Ndiswrapper doesn't work.

Surely since it works on DSL, it should work under Ubuntu. Could you tell me how I should go about getting this working.

Thankyou,

Oli

---

### Post by startherepodcast on 2007-11-08
From the Ndsiwrapper Website:

#
Card: Belkin F5D6020

    *
      Chipset: RealTek? 8180
    *
      pciid: 1799:6020 (rev 20)
    *
      Driver: Belkin [http://web.belkin.com/support/download/downloaddetails.asp?file_id=1431](http://web.belkin.com/support/download/downloaddetails.asp?file_id=1431) RealTek? [ftp://202.65.194.18/cn/wlan/rtl8180l/ndis5x-8180(173).zip](ftp://202.65.194.18/cn/wlan/rtl8180l/ndis5x-8180(173).zip)
    *
      *Toshiba Satellite 4015CDT, Debian Sarge, kernel 2.6.8 / ndiswrapper 0.10. The Belkin driver did not work for me, it loaded but failed to do anything useful whatsoever. An ndiswrapper -l using the realtek driver reported the hardware not present. By copying the Bel6020.inf file from the Belkin driver and the rtl8180.sys file from the realtek driver into the same directory, and replacing every instance of the string “Bel6020.sys” with “rtl8180.sys” I was able to get the card work satisfactorily. ‘(Best Solution)’
    *
      * Acer TravelMate 240 series. Follow the same procedure as in Toshiba Satellite above. Tested on debian unstable, 2.6.16-2-686 kernel with headers. I have compiled the ndiswrapper(1.6) module for the kernel from source, since apt-get did/does not install it.
    *
      *Dell Latitude CPi, Debian Sarge, kernel 2.6.7 / Ndiswrapper 0.10-1. After first trying with the Belkin driver, fiddeling the mode back and forward between Ad-Hoc and Managed mode without much success I switched driver to the one from RealTek?. Which works without any trouble what so ever.
    *
      *Other: Dell Latitude C840, Mandrake 10, kernel 2.6.3-15mdk / Ndiswrapper 0.9. WEP works with non-broadcasting essid. Managed mode requires several attempts to get activated. I have to toggle between the 2 modes (Ad-Hoc and Managed) to get the link LED on the PCMCIA card to lit up.
    *
      *IBM Thinkpad T23, Debian testing, kernel 2.6.10, ndiswrapper 1.1rc1@050217 (nightly). Using the Debian packages did not work, so first get rid of packages ndiswrapper-source/utils/modules, then install the nightly build (both utils and driver of course). Then download the ndis-driver from realtek, and install with ndiswrapper -i. By some reason, the .conf-files in /etc/ndiswrapper/net8180/ will be called 10EC:8180.5.conf. Until I changed that into 1799:6020.5.conf (the PCIID you get from lspci -n), the hardware was not detected with ndiswrapper -l. As I don’t have an AP, I cannot really verify that it works from here, but it looks promising.
      *IBM ThinkPad A22P. Tested on RHEL AS4 update 4 with ndiswrapper v. 1.9. Download the driver [ftp://210.51.181.211/cn/wlan/ndis5x-8180(173).zip](ftp://210.51.181.211/cn/wlan/ndis5x-8180(173).zip) and install according to the basic ndiswrapper instructions. After installing, rename the files in /etc/ndiswrapper/net8180, substituting `10EC’ with `1799’ and `8180’ with `6020’, respectively, to match the PCIID you get from `lspci -n’.


I cant test any of those since I do not have the card but you might wanna try these methods

Leon

---

### Post by oli888 on 2007-11-09
Thankyou for your reply. I will try these later. :D

---

