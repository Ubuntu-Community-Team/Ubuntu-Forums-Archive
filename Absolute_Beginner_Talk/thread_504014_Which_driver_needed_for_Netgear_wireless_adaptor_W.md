---
title: "Which driver needed for Netgear wireless adaptor WG111v2 with Ubuntu 7.04?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-07-18
I have the Netgear Wireless adaptor WG111v2, and need to configure it to work with Ubuntu 7.04.  I went to the NDISWrapper site and found that there were quite around 8 or 10 different driver entries on the site that matched my adaptor model number, WG111v2. So I used the command "lsusb" to find out the USB ID of the adaptor and this is what I got: Bus 001 Device 016: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2). So on this basis I understood that it is USB ID 0846:6a00. I checked this against the entries on the NDISWrapper website and found that there are five different entries that have that very USB ID. I am listing them below.  Could someone take a look at them and let me know which one I should use. I did not want to install the wrong driver just by arbitrarily experimenting and ending up with something that did not work.  I do not know how to differentiate among these below five drivers. And none seem to state directly that they are for Ubuntu 7.04. Thanks!!

Here below are the five options I found:

#1 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter (made in Taiwan)

*
Chipset: Realtek RTL8187
*
usbid: 0846:6a00
*
Distro: Ubuntu 6.06 LTS, kernel 2.6.15-25
*
Driver: (BAD) Realtek RTL8187L Win98SE/WinME driver v 1.221 from [http://www.realtek.com.tw/downloads/...eyword=RTL8187](http://www.realtek.com.tw/downloads/...eyword=RTL8187) - DriverVer 5.1221.0412.2006. Uses name netrtuw.inf. This works for a while, but after ~5 minutes of ssh/file copy traffic, the machine hung and had to be rebooted (reproducibly).
*
Driver: (BAD) Netgear wg111v2 1.40 (?) from [http://kbserver.netgear.com/release_notes/D102948.asp](http://kbserver.netgear.com/release_notes/D102948.asp) (labeled as 2.00 on [http://kbserver.netgear.com/products/wg111v2.asp](http://kbserver.netgear.com/products/wg111v2.asp)) - DriverVer 5.1213.06.0327. Ndiswrapper will load this driver successfully and find the device, but iwlist scans will fail and the device won’t associate.
*
Other: MUST rmmod, or blacklist kernel driver r8187 (in /etc/modprobe.d/blacklist) - it will claim the device before ndiswrapper gets a chance. The r8187 driver will associate with an AP and appear to work, but won’t actually transmit any data.

#2 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
Chipset: Realtek Semiconductor Corp. RTL8187L
*
usbid: 0846:6a00 Distro-specific: Debian “sid”
*
Driver: realtek-driver for Windows 98SE/ME from [http://www.realtek.com.tw/](http://www.realtek.com.tw/) look for RTL8187L or take Win-ME-driver from 1.4.0 driver from Netgear
*
Other: Distro: Kanotix, kernel Linux version 2.6.17.6, ndiswrapper utils version: 1.8 ndiswrapper driver version: 1.21. Some XP/2K drivers could see ESSID but didn’t transfer bytes, others did not even scan ESSID of AP. With ME-driver it seems to work quite well.

#3 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
usbid: 0846:6a00 Distro-specific: Debian “sid”
*
Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD
*
Other: tested debian-kernel 2.6.8 with ndiswrapper 1.1 and vanilla-kernel 2.6.12.3 with ndiswrapper 1.2 - everything works fine as far as i can tell.

#4 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
usbid: 0846:6a00
*
Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD
*
Distro-specific: SuSE 10.0
*
Other: tested SuSE Kernel 2.6.13-15.11 with ndiswrapper 1.21 - 128bit WEP and data transfer work fine. Ndiswapper 1.17 and previous kernel did not work (flaky operation + kernel oops).

#5 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
Chipset: Realtek Semiconductor Corp. RTL8187L
*
usbid: 0846:6a00
*
Driver: Realtek Windows XP drivers Version: Realtek Semiconductor Corp.,05/04/2005,5.112.05.0504 from [http://www.realtek.com.tw/downloads/...eyword=RTL8187](http://www.realtek.com.tw/downloads/...eyword=RTL8187) (2.00 2005/05/31)
*
Other: Extract ZIP file and install driver in WINXP directory. Kernel 2.6.12.6 with WE 18 and ndiswrapper 1.2/1.4 &#8658; 128 bit WEP works perfectly, but WPA-PSK TKIP seems not to work with current wpa_supplicant version

---

### Post by testube_babies on 2007-07-18
This guide recommends the Win98 driver:
[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

---

### Post by swarup on 2007-07-18
> **testube_babies said:**
> This guide recommends the Win98 driver:
[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

Hey, thanks for the reference. I've been reading through it. But my question for you is: that discussion is about loading the WG111v2 on Edgy--not on Feisty (Ubuntu 7.04). Do you think the directions for Edgy and for Feisty would be the same?

---

### Post by testube_babies on 2007-07-18
It looks like it should, but you might need some tricks:
[http://ubuntuforums.org/showpost.php?p=2570897&postcount=86](http://ubuntuforums.org/showpost.php?p=2570897&postcount=86)

---

### Post by swarup on 2007-07-18
> **testube_babies said:**
> It looks like it should, but you might need some tricks:
[http://ubuntuforums.org/showpost.php?p=2570897&postcount=86](http://ubuntuforums.org/showpost.php?p=2570897&postcount=86)

It looks like you've read through that entire 10-page thread! I just finished doing the same. The last post in that thread gives reference to another thread in which a further approach is given, in another tutorial: [http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187)

By they way, do you have a WG111? It seems like you do, given your familiarity with the subject.

---

### Post by Azoix on 2007-07-18
> **swarup said:**
> I have the Netgear Wireless adaptor WG111v2, and need to configure it to work with Ubuntu 7.04.  I went to the NDISWrapper site and found that there were quite around 8 or 10 different driver entries on the site that matched my adaptor model number, WG111v2. So I used the command "lsusb" to find out the USB ID of the adaptor and this is what I got: Bus 001 Device 016: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2). So on this basis I understood that it is USB ID 0846:6a00. I checked this against the entries on the NDISWrapper website and found that there are five different entries that have that very USB ID. I am listing them below.  Could someone take a look at them and let me know which one I should use. I did not want to install the wrong driver just by arbitrarily experimenting and ending up with something that did not work.  I do not know how to differentiate among these below five drivers. And none seem to state directly that they are for Ubuntu 7.04. Thanks!!

Here below are the five options I found:

#1 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter (made in Taiwan)

*
Chipset: Realtek RTL8187
*
usbid: 0846:6a00
*
Distro: Ubuntu 6.06 LTS, kernel 2.6.15-25
*
Driver: (BAD) Realtek RTL8187L Win98SE/WinME driver v 1.221 from [http://www.realtek.com.tw/downloads/...eyword=RTL8187](http://www.realtek.com.tw/downloads/...eyword=RTL8187) - DriverVer 5.1221.0412.2006. Uses name netrtuw.inf. This works for a while, but after ~5 minutes of ssh/file copy traffic, the machine hung and had to be rebooted (reproducibly).
*
Driver: (BAD) Netgear wg111v2 1.40 (?) from [http://kbserver.netgear.com/release_notes/D102948.asp](http://kbserver.netgear.com/release_notes/D102948.asp) (labeled as 2.00 on [http://kbserver.netgear.com/products/wg111v2.asp](http://kbserver.netgear.com/products/wg111v2.asp)) - DriverVer 5.1213.06.0327. Ndiswrapper will load this driver successfully and find the device, but iwlist scans will fail and the device won&#8217;t associate.
*
Other: MUST rmmod, or blacklist kernel driver r8187 (in /etc/modprobe.d/blacklist) - it will claim the device before ndiswrapper gets a chance. The r8187 driver will associate with an AP and appear to work, but won&#8217;t actually transmit any data.

#2 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
Chipset: Realtek Semiconductor Corp. RTL8187L
*
usbid: 0846:6a00 Distro-specific: Debian &#8220;sid&#8221;
*
Driver: realtek-driver for Windows 98SE/ME from [http://www.realtek.com.tw/](http://www.realtek.com.tw/) look for RTL8187L or take Win-ME-driver from 1.4.0 driver from Netgear
*
Other: Distro: Kanotix, kernel Linux version 2.6.17.6, ndiswrapper utils version: 1.8 ndiswrapper driver version: 1.21. Some XP/2K drivers could see ESSID but didn&#8217;t transfer bytes, others did not even scan ESSID of AP. With ME-driver it seems to work quite well.

#3 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
usbid: 0846:6a00 Distro-specific: Debian &#8220;sid&#8221;
*
Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD
*
Other: tested debian-kernel 2.6.8 with ndiswrapper 1.1 and vanilla-kernel 2.6.12.3 with ndiswrapper 1.2 - everything works fine as far as i can tell.

#4 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
usbid: 0846:6a00
*
Driver: Netgear windows driver Version: NETGEAR Inc.,04/21/2005,5.112.05.0421 from directory Driver/WINXP/ on the setup CD
*
Distro-specific: SuSE 10.0
*
Other: tested SuSE Kernel 2.6.13-15.11 with ndiswrapper 1.21 - 128bit WEP and data transfer work fine. Ndiswapper 1.17 and previous kernel did not work (flaky operation + kernel oops).

#5 Card: NETGEAR WG111v2 802.11g Wireless USB2.0 Adapter

*
Chipset: Realtek Semiconductor Corp. RTL8187L
*
usbid: 0846:6a00
*
Driver: Realtek Windows XP drivers Version: Realtek Semiconductor Corp.,05/04/2005,5.112.05.0504 from [http://www.realtek.com.tw/downloads/...eyword=RTL8187](http://www.realtek.com.tw/downloads/...eyword=RTL8187) (2.00 2005/05/31)
*
Other: Extract ZIP file and install driver in WINXP directory. Kernel 2.6.12.6 with WE 18 and ndiswrapper 1.2/1.4 &#8658; 128 bit WEP works perfectly, but WPA-PSK TKIP seems not to work with current wpa_supplicant version

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I'm currently typing this on my Ubuntu laptop, on wireless, with WEP encryption, on a WG111v2 USB dongle, the driver i use, without error and without any troubles is v.1_3_0

azoix@tualatin:~$ ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)

I have uploaded it as a gzip here :

[http://www.sendspace.com/file/ld326j](http://www.sendspace.com/file/ld326j)

It is the full windows package, containing the utility and drivers, so it has the files for both an Ubuntu or Windows install.
For Ubuntu, create a folder somewhere, and open the driver folder in the zip, and use the .inf and .sys files in the WINDOWS 2000 folder, the ME and 98 version fail, and the XP reports as bad when probed,All work fine with windows, but use ONLY the Win2K for nix.
Copy the 2 files to the new folder and direct ndiswrapper -i command to it, then you should be online in minutes.
Hope this gets things working for you.

One note, my wg111v2 IS WORKING 100%, but the NDISGTK shows no hardware present, the power functions of the usb dongle are not available on Ubuntu, and the LED doesn't work on Ubuntu either, but does on Windows.
This just means, you need to find another means of telling if the wireless is working or not, easiest method i found is use the add applet tool on the desktop, right click the taskbar, top of screen, then select add applet, then choose the network monitor from the System and Hardware group, then just position it where you wish.
This shows the wireless and ethernet (if connected) and has a bar showing incoming and outgoing packets.Simple, but effective way of seeing if the wireless is down, if the packets stop coming in, the wireless is not connected.[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-18
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I'm currently typing this on my Ubuntu laptop, on wireless, with WEP encryption, on a WG111v2 USB dongle, the driver i use, without error and without any troubles is v.1_3_0

azoix@tualatin:~$ ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)

I have uploaded it as a gzip here :

[http://www.sendspace.com/file/ld326j](http://www.sendspace.com/file/ld326j)

It is the full windows package, containing the utility and drivers, so it has the files for both an Ubuntu or Windows install.
For Ubuntu, create a folder somewhere, and open the driver folder in the zip, and use the .inf and .sys files in the WINDOWS 2000 folder, the ME and 98 version fail, and the XP reports as bad when probed,All work fine with windows, but use ONLY the Win2K for nix.
Copy the 2 files to the new folder and direct ndiswrapper -i command to it, then you should be online in minutes.
Hope this gets things working for you.

One note, my wg111v2 IS WORKING 100%, but the NDISGTK shows no hardware present, the power functions of the usb dongle are not available on Ubuntu, and the LED doesn't work on Ubuntu either, but does on Windows.
This just means, you need to find another means of telling if the wireless is working or not, easiest method i found is use the add applet tool on the desktop, right click the taskbar, top of screen, then select add applet, then choose the network monitor from the System and Hardware group, then just position it where you wish.
This shows the wireless and ethernet (if connected) and has a bar showing incoming and outgoing packets.Simple, but effective way of seeing if the wireless is down, if the packets stop coming in, the wireless is not connected.[/COLOR][/SIZE][/FONT][/B]

Thanks very much for your very helpful post. That is really great news. I guess I have a couple of further questions:
1. Are you using Feisty Fawn, or are you using a different version of Ubuntu?
2. Could you spell out the instructions a little more for me, as I am not so familiar with the linux terminology and style of function. Particular the following part:

"For Ubuntu, create a folder somewhere, and open the driver folder in the zip, and use the .inf and .sys files in the WINDOWS 2000 folder. Copy the 2 files to the new folder and direct ndiswrapper -i command to it, then you should be online in minutes."

Say I create a folder in my home directory. Will that be ok? Then I'll open the folder which you directed me to download, and open the Windows 2000 folder. I will copy the .inf and .sys files from that Windows 2000 folder, and paste these two files (Windows 2000 .inf and .sys)  into the folder I made in my home directory. Then, what does it mean to "direct ndiswrapper -i command" to the folder? 

Thanks!

---

### Post by Azoix on 2007-07-19
> **swarup said:**
> Thanks very much for your very helpful post. That is really great news. I guess I have a couple of further questions:
1. Are you using Feisty Fawn, or are you using a different version of Ubuntu?
2. Could you spell out the instructions a little more for me, as I am not so familiar with the linux terminology and style of function. Particular the following part:

"For Ubuntu, create a folder somewhere, and open the driver folder in the zip, and use the .inf and .sys files in the WINDOWS 2000 folder. Copy the 2 files to the new folder and direct ndiswrapper -i command to it, then you should be online in minutes."

Say I create a folder in my home directory. Will that be ok? Then I'll open the folder which you directed me to download, and open the Windows 2000 folder. I will copy the .inf and .sys files from that Windows 2000 folder, and paste these two files (Windows 2000 .inf and .sys)  into the folder I made in my home directory. Then, what does it mean to "direct ndiswrapper -i command" to the folder? 

Thanks!

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Currently i'm in a Feisty kinda mood...but i can be a kubuntu kid anytime i want, and xubuntu is a bad mofo too !! 
Say nothing of a sleek and clean ubuntu gnome server.....running gnome-core xorg and gdm  and nothing more.LIGHT FAST AND STABLE.

Your Answer :
Save me typing it all again, have a look here, [http://ubuntuforums.org/showthread.php?t=499084](http://ubuntuforums.org/showthread.php?t=499084)  You can PM me if you need more help.Other's on the forum site who know than i do more will also be glad to help if they can i'm sure.[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-19
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Currently i'm in a Feisty kinda mood...but i can be a kubuntu kid anytime i want, and xubuntu is a bad mofo too !! 
Say nothing of a sleek and clean ubuntu gnome server.....running gnome-core xorg and gdm  and nothing more.LIGHT FAST AND STABLE.

Your Answer :
Save me typing it all again, have a look here, [http://ubuntuforums.org/showthread.php?t=499084](http://ubuntuforums.org/showthread.php?t=499084)  You can PM me if you need more help.Other's on the forum site who know than i do more will also be glad to help if they can i'm sure.[/COLOR][/SIZE][/FONT][/B]

You write here that you are online in Feisty, but in your tutorial you referred me to above, you have clearly stated that in Feisty (Ubuntu 7.04), the WG111v2 did not work for you. So please clarify for me one time here: have you gotten the WG111v2 to work with Ubuntu 7.04 Feisty Fawn, or not? Thanks so much!

---

### Post by Azoix on 2007-07-19
> **swarup said:**
> You write here that you are online in Feisty, but in your tutorial you referred me to above, you have clearly stated that in Feisty (Ubuntu 7.04), the WG111v2 did not work for you. So please clarify for me one time here: have you gotten the WG111v2 to work with Ubuntu 7.04 Feisty Fawn, or not? Thanks so much!
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Hi,
If you re-read the post i linked to, you will see it pertains to 2 seperate wireless dongles, the first USB dongle mentioned is a wg111v2, same as your's, this one [COLOR="Red"]DOES[/COLOR] work on Ubuntu, and many more distro's, but the second type mentioned, the wg111v1 type [COLOR="Red"]DOES NOT[/COLOR] work on Ubuntu for me.[COLOR="Green"]**[/COLOR] 
It may work fine on other hardware.Both types worked on KDE distro's i tested.( knoppix HDD install , kanotix liveCD and HDD)

[COLOR="Green"]**
I say for me, as i am using an IBM Thinkpad laptop, and know from experience, in the past IBM and linux didn't like each other much, a bit like the young niece and the drunken, lecherous uncle at christmas time...........i guess things have not changed much in some area's.
Nice to find an effort is being made for us one make/brand users....the thinkpad-utils adds all the functions i want, my OSD, OSKB and such.NICE WORK.[/COLOR][/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-19
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Hi,
If you re-read the post i linked to, you will see it pertains to 2 seperate wireless dongles, the first USB dongle mentioned is a wg111v2, same as your's, this one [COLOR="Red"]DOES[/COLOR] work on Ubuntu, and many more distro's, but the second type mentioned, the wg111v1 type [COLOR="Red"]DOES NOT[/COLOR] work on Ubuntu for me.[COLOR="Green"]**[/COLOR] 
It may work fine on other hardware.Both types worked on KDE distro's i tested.( knoppix HDD install , kanotix liveCD and HDD)

[/COLOR][/SIZE][/FONT][/B]

I see-- yes, I re-read it and now I understand. So that is great. My device is also ID 0846:6A00 as is yours, so on the basis of this it should work fine. In several places in the tutorial you mentioned that you were working on "ubuntu"-- wherever you mentioned ubuntu does it mean you were using Feisty 7.04, and not Edgy or Dapper? Please don't mind my asking, I just want to be sure as far as possible I'm not going to run into problems. 

I think everything else you wrote was quite clear. Although my own ignorance about Linux may be the cause of some silly questions which others wouldn't need to ask. For example, does it matter when I download the driver you uploaded? Do I have to wait until I'm ready to go ahead, or could I download it now for example and then just hold it in my computer until I'm ready to move ahead. I have ordered a wireless router (the Kyocera KR1 EVDO Mobile Router) which is made to work with my aircard, the Novatel Wireless Ovation U720 USB modem. It should be arriving in around 3-4 days, and I thought I would wait till then so I would be able to tell whether the Netgear adaptor is working or not to get me on line. Thanks for all your help!

---

### Post by Azoix on 2007-07-20
> **swarup said:**
> I see-- yes, I re-read it and now I understand. So that is great. My device is also ID 0846:6A00 as is yours, so on the basis of this it should work fine. In several places in the tutorial you mentioned that you were working on "ubuntu"-- wherever you mentioned ubuntu does it mean you were using Feisty 7.04, and not Edgy or Dapper? Please don't mind my asking, I just want to be sure as far as possible I'm not going to run into problems. 

I think everything else you wrote was quite clear. Although my own ignorance about Linux may be the cause of some silly questions which others wouldn't need to ask. For example, does it matter when I download the driver you uploaded? Do I have to wait until I'm ready to go ahead, or could I download it now for example and then just hold it in my computer until I'm ready to move ahead. I have ordered a wireless router (the Kyocera KR1 EVDO Mobile Router) which is made to work with my aircard, the Novatel Wireless Ovation U720 USB modem. It should be arriving in around 3-4 days, and I thought I would wait till then so I would be able to tell whether the Netgear adaptor is working or not to get me on line. Thanks for all your help!

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]No worries at all, how can you learn what you don't know if you don't ask , eh ? I'm just the same as you, learning as i go.Only been nix-ing for a month myself.........
All Ubuntu testing was done using 7.04 Feisty Fawn, but as long as you use the apt-get commands as shown, it should install the latest version compatable to your distro, i assume, be it Feisty Edgy Dapper or the latest one from the drug smokin' developers......GUTSY GIBBON !!! come on guy's, what are you smokin' over there ? and where's my share ??? 
As for the driver, just download it and put it somewhere until you need it, it's a gzip, just download from sendspace, and then when you need it, right click on it and select extract.Then you have all the files you will need.:)[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-20
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]No worries at all, how can you learn what you don't know if you don't ask , eh ? I'm just the same as you, learning as i go.Only been nix-ing for a month myself.........
All Ubuntu testing was done using 7.04 Feisty Fawn, but as long as you use the apt-get commands as shown, it should install the latest version compatable to your distro, i assume, be it Feisty Edgy Dapper or the latest one from the drug smokin' developers......GUTSY GIBBON !!! come on guy's, what are you smokin' over there ? and where's my share ??? 
As for the driver, just download it and put it somewhere until you need it, it's a gzip, just download from sendspace, and then when you need it, right click on it and select extract.Then you have all the files you will need.:)[/COLOR][/SIZE][/FONT][/B]

Thanks for much for all your helpful replies. I'll go ahead and download the file then, and when the router arrives, I'll do the install and configuration. I have no doubt that I shall need to write you again, when I get stuck on something or other along the way. But that'll probably be around four-five days from now.

...I went to the site your gave for downloading the file. When I click on the file to download, then the download window opens and asks me whether I want to "open" the file using file-roller, or save to disc. Which should I choose? If I select "open", then does that mean it is going to unzip it and try to run it? It sounds like, if I don't want to run it now then I should select "save to disc", right? What does it mean to select "open" the file, anyway? Does "open" mean to just "open it and look at it on the screen"? Or does "open" mean to "unzip and run" the file?

---

### Post by Azoix on 2007-07-20
> **swarup said:**
> Thanks for much for all your helpful replies. I'll go ahead and download the file then, and when the router arrives, I'll do the install and configuration. I have no doubt that I shall need to write you again, when I get stuck on something or other along the way. But that'll probably be around four-five days from now.

...I went to the site your gave for downloading the file. When I click on the file to download, then the download window opens and asks me whether I want to "open" the file using file-roller, or save to disc. Which should I choose? If I select "open", then does that mean it is going to unzip it and try to run it? It sounds like, if I don't want to run it now then I should select "save to disc", right? What does it mean to select "open" the file, anyway? Does "open" mean to just "open it and look at it on the screen"? Or does "open" mean to "unzip and run" the file?

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I honestly don't know if opening in file roller opens the zip contents in a window similar  winzip/winrar  in windows, but YES just choose save to disk and you can use the file when needed.
I would imagine if you select open , it would bring up a window, with an extract button somewhere to open the zip and extract the files from it.That would be it's job.
There&#347; an easy answer to your questions though......save a copy , reopen the sendspace page AFTER you save the file, click on the link AGAIN and try open.See what happens.......it will either open and ask if you want to extract, or nothing at all may happen.
Try it yourself and see.There's nothing you can do to harm your PC, all it will do is ask for more details i would imagine(where to extract? do u want to run? etc.)  but i really don't know, as i don't use it myself.[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-20
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I honestly don't know if opening in file roller opens the zip contents in a window similar  winzip/winrar  in windows, but YES just choose save to disk and you can use the file when needed.
I would imagine if you select open , it would bring up a window, with an extract button somewhere to open the zip and extract the files from it.That would be it's job.
There&#347; an easy answer to your questions though......save a copy , reopen the sendspace page AFTER you save the file, click on the link AGAIN and try open.See what happens.......it will either open and ask if you want to extract, or nothing at all may happen.
Try it yourself and see.There's nothing you can do to harm your PC, all it will do is ask for more details i would imagine(where to extract? do u want to run? etc.)  but i really don't know, as i don't use it myself.[/COLOR][/SIZE][/FONT][/B]

Thanks very much. That is very sound advice, and I'll certainly try and see.

---

### Post by dcstar on 2007-07-21
My RTL8187 based WG111v2 seemed to work "out of the box" with Feisty (once I plugged it into a USB port with sufficient power capability), and it came up in the nm-applet.

Just make sure that you have both the **network-manager-gnome** & **network-manager** packages installed, and then the Network Monitor added to your top panel.

In this "basic" setup, I could only get it to work by broadcasting SSID and only with WEP, there are instructions for getting WPA going here (but I couldn't be bothered):

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by swarup on 2007-07-21
> **dcstar said:**
> My RTL8187 based WG111v2 seemed to work "out of the box" with Feisty (once I plugged it into a USB port with sufficient power capability), and it came up in the nm-applet.

Just make sure that you have both the **network-manager-gnome** & **network-manager** packages installed, and then the Network Monitor added to your top panel.

In this "basic" setup, I could only get it to work by broadcasting SSID and only with WEP, there are instructions for getting WPA going here (but I couldn't be bothered):

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Many thanks for your report, which is fascinating to me. --That is, that the WG111v2 will work "out of the box". That is marvelous to hear. Yet at the same time, it is almost too bizarre. Because if you search on 
"WG111v2" in this forum, you will find pages and pages of discussions on how to get it working in Feisty and other Ubuntu distros. There are lots of sob stories of people who could not get it to work, and there are complex instructions on "work-arounds" for the difficulties. --Then amidst all this, to hear a report that it "works out of the box", is quite strange. Although wonderful. 

The way you worded your description, I was unsure whether all WG111v2's are RTL8187 based, or only some?

But I will certainly try what you suggest. If it works, then that is really great. I'll get the network-manager-gnome & network-manager, as you instruct. 

One important question: when you say a "USB port with sufficient power capability", does it mean that some USB ports have sufficient power capability and others not? How can one tell if one's USB port has sufficient power capability? I only have USB type 1 on my laptop, but I do have a double USB cable which can shuttle the power from the two USB ports on the machine into the WG111v2. Should that do it?

As soon as my aircard router arrives in 3 days or so, I'll give your suggestion a try first. If it works, that is just fantastic! 

Many thanks.

---

### Post by Azoix on 2007-07-21
> **swarup said:**
> Many thanks for your report, which is fascinating to me. --That is, that the WG111v2 will work "out of the box". That is marvelous to hear. Yet at the same time, it is almost too bizarre. Because if you search on 
"WG111v2" in this forum, you will find pages and pages of discussions on how to get it working in Feisty and other Ubuntu distros. There are lots of sob stories of people who could not get it to work, and there are complex instructions on "work-arounds" for the difficulties. --Then amidst all this, to hear a report that it "works out of the box", is quite strange. Although wonderful. 

The way you worded your description, I was unsure whether all WG111v2's are RTL8187 based, or only some?

But I will certainly try what you suggest. If it works, then that is really great. I'll get the network-manager-gnome & network-manager, as you instruct. 

One important question: when you say a "USB port with sufficient power capability", does it mean that some USB ports have sufficient power capability and others not? How can one tell if one's USB port has sufficient power capability? I only have USB type 1 on my laptop, but I do have a double USB cable which can shuttle the power from the two USB ports on the machine into the WG111v2. Should that do it?

As soon as my aircard router arrives in 3 days or so, I'll give your suggestion a try first. If it works, that is just fantastic! 

Many thanks.

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I have personal knowledge of at least 2 types of w111v2 and i own 3 variants of the version 1 type, and 2 different wg511v2 pcmcia cards.
Only one of all these works at all on Ubuntu, the wg111v2 i'm using now, all of them work on windows, and all work on debian4 and fedora7 in KDE.
If someone out there has the definitive answer as to why this is so, your one up on me.........:)
USB ports are +5 volt, and double the power to the port is useful if you have a cantankerous external drive like i do, but apart from the fact you can't run two inward connection to the one USB wireless device, it only has 1 port, your in eminent danger of frying it and your mainboard.
Laptop mainboards are EXTREMELY sensitive to excess voltages, i've fried one or two myself over the years......  [/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-21
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I have personal knowledge of at least 2 types of w111v2 and i own 3 variants of the version 1 type, and 2 different wg511v2 pcmcia cards.
Only one of all these works at all on Ubuntu, the wg111v2 i'm using now, all of them work on windows, and all work on debian4 and fedora7 in KDE.
If someone out there has the definitive answer as to why this is so, your one up on me.........:)
USB ports are +5 volt, and double the power to the port is useful if you have a cantankerous external drive like i do, but apart from the fact you can't run two inward connection to the one USB wireless device, it only has 1 port, your in eminent danger of frying it and your mainboard.
Laptop mainboards are EXTREMELY sensitive to excess voltages, i've fried one or two myself over the years......  [/COLOR][/SIZE][/FONT][/B]

Perhaps DCStar can tell us if he is using the WG111v2 which is of the variety having ID 0846:6A00? That would be a great help. Please kindly let us know the ID of your device, DC Star.

As for the double USB cable, it is a cable that came with my Novatel Aircard. It is a special cable--a single cable having two USB connectors on one end that plug into the two USB ports of my laptop, and on the other end a single USB connector that plugs into my Novatel aircard. That way the aircard gets all the power it needs. But as far as I understand, all the power is flowing from the laptop TO the aircard-- that is, I do not think power is flowing INTO the laptop as would put the mainboard at risk. So I was just saying that this cable I could use with the Netgear adaptor if needed. I guess according to what you've state, that would supply the Netgear device with power from two +5 volt USB ports-- perhaps that means if it is an additive relation, then the Netgear device would be supplied with +10 volts should it be needed.

---

### Post by Azoix on 2007-07-21
> **swarup said:**
> Perhaps DCStar can tell us if he is using the WG111v2 which is of the variety having ID 0846:6A00? That would be a great help. Please kindly let us know the ID of your device, DC Star.

As for the double USB cable, it is a cable that came with my Novatel Aircard. It is a special cable--a single cable having two USB connectors on one end that plug into the two USB ports of my laptop, and on the other end a single USB connector that plugs into my Novatel aircard. That way the aircard gets all the power it needs. .........edited (to shorten length only)....would be supplied with +10 volts should it be needed.
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]It would seem clear to me, you have a clear understanding of the power issue's you could face, the surge on the mainboard i mention, can occur if too much load is asked of the port (i.e:stubborn device, such as my usb disc, the hdd in it is old and covered in bad sectors) , this most times, when plugged into my Windows laptop, pops up an error box with the warning of a "power surge on hub port" and the device simply doesn't read.
I ***can*** use a double powered cable, and sometimes this helps, but often the surge overrides all safety's in the machine and the good 'ole Blue Screen of DEATH pops it's head up and says says "Howdy".
After rebooting, the disc is still absent, and device manager shows unknown usb device, or simply reports the port as bad.
As with the previous question you asked about file roller, i give the same advice on the USB issue, try it and see if it works, but be prepared for the ( possible ) after effects.[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-21
\> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]It would seem clear to me, you have a clear understanding of the power issue's you could face, the surge on the mainboard i mention, can occur if too much load is asked of the port (i.e:stubborn device, such as my usb disc, the hdd in it is old and covered in bad sectors) , this most times, when plugged into my Windows laptop, pops up an error box with the warning of a "power surge on hub port" and the device simply doesn't read.
I ***can*** use a double powered cable, and sometimes this helps, but often the surge overrides all safety's in the machine and the good 'ole Blue Screen of DEATH pops it's head up and says says "Howdy".
After rebooting, the disc is still absent, and device manager shows unknown usb device, or simply reports the port as bad.
As with the previous question you asked about file roller, i give the same advice on the USB issue, try it and see if it works, but be prepared for the ( possible ) after effects.[/COLOR][/SIZE][/FONT][/B]

Thanks for the prudent advice. I'll surely keep it in mind.

---

### Post by dcstar on 2007-07-22
> **swarup said:**
> Perhaps DCStar can tell us if he is using the WG111v2 which is of the variety having ID 0846:6A00? That would be a great help. Please kindly let us know the ID of your device, DC Star.
.........

That ID is what is reported in my system:

This is the relevant lshw data:
```
                   description: Generic USB device
                   product: NETGEAR WG111v2
                   vendor: NETGEAR WG111v2
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   serial: 00184DBA2D32
                   capabilities: usb-2.00
                   configuration: driver=rtl8187 maxpower=500mA speed=480.0MB/s
```
 and lsusb:
```

Bus 004 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
```

When I plugged it into a 4 port USB hub with a stick drive also on it, dmesg reported a current overload warning and I wasted a lot of time trying to get the thing to work - when I just plugged it into a USB port on its own there was no warning and it actually worked with my wireless setup.

Here is my dmesg output once I put in my WG111v2:

```
[ 3415.876424] usb 4-2: new high speed USB device using ehci_hcd and address 5
[ 3415.996409] usb 4-2: configuration #1 chosen from 1 choice
[ 3416.180486] wmaster0: Selected rate control algorithm 'simple'
[ 3416.180732] wiphy1: hwaddr 00:18:4d:ba:2d:32, rtl8187 V1 + rtl8225z2
[ 3419.878931] wmaster0: Does not support passive scan, disabled
[ 3419.899176] wlan0: starting scan
[ 3421.203505] wlan0: scan completed
[ 3426.166348] NET: Registered protocol family 17
[ 3431.224776] wlan0: Initial auth_alg=1
[ 3431.224785] wlan0: authenticate with AP 00:18:4d:6c:4d:68
[ 3431.235272] wlan0: RX authentication from 00:18:4d:6c:4d:68 (alg=1 transaction=2 status=0)
[ 3431.235277] wlan0: replying to auth challenge
[ 3431.238133] wlan0: RX authentication from 00:18:4d:6c:4d:68 (alg=1 transaction=4 status=0)
[ 3431.238137] wlan0: authenticated
[ 3431.238141] wlan0: associate with AP 00:18:4d:6c:4d:68
[ 3431.240505] wlan0: RX AssocResp from 00:18:4d:6c:4d:68 (capab=0x471 status=0 aid=1)
[ 3431.240509] wlan0: associated
```

---

### Post by swarup on 2007-07-23
> **dcstar said:**
> My RTL8187 based WG111v2 seemed to work "out of the box" with Feisty (once I plugged it into a USB port with sufficient power capability), and it came up in the nm-applet.

Just make sure that you have both the **network-manager-gnome** & **network-manager** packages installed, and then the Network Monitor added to your top panel.

In this "basic" setup, I could only get it to work by broadcasting SSID and only with WEP, there are instructions for getting WPA going here (but I couldn't be bothered):

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

You mention above to be sure both the network-manager-gnome and network-manager packages are installed. I went to add-remove programs, and there is a network-manager package there-- and it is already installed. And its Network Monitor is also added already to the top panel. But I could not find anything called network-manager-gnome in add-remove programs. Is there indeed something separate by that name which   I need to install?

When I plug in my Netgear WG111v2 here is the output data that I get--

Here is the relevant lshw output:


                   description: Generic USB device
                   product: NETGEAR WG111v2
                   vendor: NETGEAR WG111v2
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   serial: 00146CB02782
                   capabilities: usb-1.10
                   configuration: driver=rtl8187 maxpower=500mA speed=12.0MB/s

Here is the lsusb output:

Bus 001 Device 012: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

And here is the dmesg output once I put in my WG111v2:

[202297.896000] usb 1-2: new full speed USB device using uhci_hcd and address 12
[202298.064000] usb 1-2: configuration #1 chosen from 1 choice
[202299.144000] wmaster0: Selected rate control algorithm 'simple'
[202299.148000] wiphy1: hwaddr 00:14:6c:b0:27:82, rtl8187 V1 + rtl8225
[202306.332000] wmaster0: Does not support passive scan, disabled
[202306.636000] wlan0: starting scan
[202308.660000] wlan0: scan completed
[202328.756000] wlan0: starting scan
[202330.780000] wlan0: scan completed
[202350.804000] wlan0: starting scan
[202352.828000] wlan0: scan completed
[202372.880000] wlan0: starting scan
[202374.904000] wlan0: scan completed
[202394.984000] wlan0: starting scan
[202397.008000] wlan0: scan completed
[202417.060000] wlan0: starting scan
[202419.084000] wlan0: scan completed
[202439.096000] wlan0: starting scan
[202441.120000] wlan0: scan completed
[202561.196000] wlan0: starting scan
[202563.228000] wlan0: scan completed
[202683.248000] wlan0: starting scan
[202685.276000] wlan0: scan completed

Perhaps indeed I have everything I need? It seems to give similar output to what David at dcstar reported. Of course, I do not yet have my router. So perhaps that is why the end of the dmesg output is different. Because the WG111v2 is not actually on line. But in 1-2 days when the router comes, I'll try it. Maybe it will work!! On the basis of what data I have provided above, does it seem that I have everything needed? Or is there indeed something separate called network-manager-gnome which I need to install?

Thanks.

---

### Post by Azoix on 2007-07-23
> **dcstar said:**
> That ID is what is reported in my system:

This is the relevant lshw data:
```
                   description: Gen[SIZE="1"]eric USB device
                   product: NETGEAR WG111v2
                   vendor: NETGEAR WG111v2
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   serial: 00184DBA2D32
                   capabilities: usb-2.00
                   configuration: driver=rtl8187 maxpower=500mA speed=480.0MB/s
```
 and lsusb:
```

Bus 004 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
```

When I plugged it into a 4 port USB hub with a stick drive also on it, dmesg reported a current overload warning and I wasted a lot of time trying to get the thing to work - when I just plugged it into a USB port on its own there was no warning and it actually worked with my wireless setup.

Here is my dmesg output once I put in my WG111v2:

```
[ 3415.876424] usb 4-2: new high speed USB device using ehci_hcd and address 5
[ 3415.996409] usb 4-2: configuration #1 chosen from 1 choice
[ 3416.180486] wmaster0: Selected rate control algorithm 'simple'
[ 3416.180732] wiphy1: hwaddr 00:18:4d:ba:2d:32, rtl8187 V1 + rtl8225z2
[ 3419.878931] wmaster0: Does not support passive scan, disabled
[ 3419.899176] wlan0: starting scan
[ 3421.203505] wlan0: scan completed
[ 3426.166348] NET: Registered protocol family 17
[ 3431.224776] wlan0: Initial auth_alg=1
[ 3431.224785] wlan0: authenticate with AP 00:18:4d:6c:4d:68
[ 3431.235272] wlan0: RX authentication from 00:18:4d:6c:4d:68 (alg=1 transaction=2 status=0)
[ 3431.235277] wlan0: replying to auth challenge
[ 3431.238133] wlan0: RX authentication from 00:18:4d:6c:4d:68 (alg=1 transaction=4 status=0)
[ 3431.238137] wlan0: authenticated
[ 3431.238141] wlan0: associate with AP 00:18:4d:6c:4d:68
[ 3431.240505] wlan0: RX AssocResp from 00:18:4d:6c:4d:68 (capab=0x471 status=0 aid=1)
[ 3431.240509] wlan0: associated[/SIZE]
```

**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Does it support WEP and WAP/PSK natively aswell ?[/COLOR][/SIZE][/FONT]**

---

### Post by dcstar on 2007-07-23
> **Azoix said:**
> **[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Does it support WEP and WAP/PSK natively aswell ?[/COLOR][/SIZE][/FONT]**

The Ubuntu nm-applet software supports WEP, WPA apparently can be supported with manual configuration.

---

### Post by swarup on 2007-07-23
My Kyocera K1 aircard router arrived! 

I hooked my evdo aircard into the router, and plugged the WG111v2 into the laptop, and tried the native connection as dcstar suggested. But it hasn't connected. I have a feeling the WG111v2 is still not properly configured-- although it may be close. Ubuntu recognizes that a WiFi connection is there on my USB port.

I ran dmesg to see what sort of output it gives. Please take a look and see if you can tell me where the connection is failing. I really can't fully comprehend what all the below means. But I see references to Wiphy3, with attempts to connect. And then after that, Wiphy4. And then an attempt to connect. And then Wiphy 5. Please kindly see below and let me know what you think:

[260015.392000] usb 1-1: new full speed USB device using uhci_hcd and address 15
[260015.560000] usb 1-1: configuration #1 chosen from 1 choice
[260016.644000] wmaster0: Selected rate control algorithm 'simple'
[260016.644000] wiphy3: hwaddr 00:0f:b5:d4:59:90, rtl8187 V1 + rtl8225
[260023.688000] wmaster0: Does not support passive scan, disabled
[260023.728000] wlan0: starting scan
[260025.752000] wlan0: scan completed
[260045.808000] wlan0: starting scan
[260047.832000] wlan0: scan completed
[260067.884000] wlan0: starting scan
[260069.908000] wlan0: scan completed
[260089.964000] wlan0: starting scan
[260091.988000] wlan0: scan completed
[260212.040000] wlan0: starting scan
[260214.064000] wlan0: scan completed
[260334.084000] wlan0: starting scan
[260336.108000] wlan0: scan completed
[260413.064000] usb 1-1: USB disconnect, address 15
[260420.316000] usb 1-1: new full speed USB device using uhci_hcd and address 16
[260420.480000] usb 1-1: configuration #1 chosen from 1 choice
[260420.480000] airprime 1-1:1.0: airprime converter detected
[260420.480000] usb 1-1: airprime converter now attached to ttyUSB0
[260420.480000] usb 1-1: airprime converter now attached to ttyUSB1
[260420.484000] usb 1-1: airprime converter now attached to ttyUSB2
[260420.484000] airprime 1-1:1.1: airprime converter detected
[260420.488000] usb 1-1: airprime converter now attached to ttyUSB3
[260420.488000] usb 1-1: airprime converter now attached to ttyUSB4
[260420.488000] usb 1-1: airprime converter now attached to ttyUSB5
[260420.492000] airprime 1-1:1.2: airprime converter detected
[260420.492000] usb 1-1: airprime converter now attached to ttyUSB6
[260420.492000] usb 1-1: airprime converter now attached to ttyUSB7
[260420.492000] usb 1-1: airprime converter now attached to ttyUSB8
[260420.496000] airprime 1-1:1.3: airprime converter detected
[260420.496000] usb 1-1: airprime converter now attached to ttyUSB9
[260420.496000] usb 1-1: airprime converter now attached to ttyUSB10
[260420.500000] usb 1-1: airprime converter now attached to ttyUSB11
[260689.720000] usb 1-1: USB disconnect, address 16
[260689.720000] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[260689.720000] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[260689.720000] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[260689.720000] airprime 1-1:1.0: device disconnected
[260689.720000] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
[260689.720000] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
[260689.720000] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
[260689.720000] airprime 1-1:1.1: device disconnected
[260689.720000] airprime ttyUSB6: airprime converter now disconnected from ttyUSB6
[260689.720000] airprime ttyUSB7: airprime converter now disconnected from ttyUSB7
[260689.720000] airprime ttyUSB8: airprime converter now disconnected from ttyUSB8
[260689.724000] airprime 1-1:1.2: device disconnected
[260689.724000] airprime ttyUSB9: airprime converter now disconnected from ttyUSB9
[260689.724000] airprime ttyUSB10: airprime converter now disconnected from ttyUSB10
[260689.724000] airprime ttyUSB11: airprime converter now disconnected from ttyUSB11
[260689.724000] airprime 1-1:1.3: device disconnected
[260754.552000] usb 1-1: new full speed USB device using uhci_hcd and address 17
[260754.720000] usb 1-1: configuration #1 chosen from 1 choice
[260755.804000] wmaster0: Selected rate control algorithm 'simple'
[260755.804000] wiphy4: hwaddr 00:0f:b5:d4:59:90, rtl8187 V1 + rtl8225
[260762.836000] wmaster0: Does not support passive scan, disabled
[260762.872000] wlan0: starting scan
[260764.896000] wlan0: scan completed
[260784.952000] wlan0: starting scan
[260786.980000] wlan0: scan completed
[260807.036000] wlan0: starting scan
[260809.064000] wlan0: scan completed
[260829.088000] wlan0: starting scan
[260831.112000] wlan0: scan completed
[260847.304000] usb 1-1: USB disconnect, address 17
[261288.920000] usb 1-1: new full speed USB device using uhci_hcd and address 18
[261289.088000] usb 1-1: configuration #1 chosen from 1 choice
[261290.172000] wmaster0: Selected rate control algorithm 'simple'
[261290.172000] wiphy5: hwaddr 00:0f:b5:d4:59:90, rtl8187 V1 + rtl8225
[261298.676000] wmaster0: Does not support passive scan, disabled
[261298.716000] wlan0: starting scan
[261300.740000] wlan0: scan completed
swarup@swarup-laptop:~$

---

### Post by Azoix on 2007-07-24
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I found NEITHER of the downloadable packages show as having a wireless connection on my laptop, if they don't show your connection either.......all is not lost......right click on the taskbar on the top of your screen, it opens a drop down list.
Click on +add to panel tab, then scroll down to System and Hardware tab.
In here you will find Network Manager, add this to the panel, when you close the applet manager, IT MAY Show the wireless, but most likely wont.
Reboot your PC, this should then show the wireless connection like this  : 

[IMG]http://i58.photobucket.com/albums/g261/PostHost/Screenshots/Screenshot.png[/IMG]

If you look above the letters `ufo` in the address bar of the screenshot, you will see the wireless applet on the taskbar.The background your seeing is THIS POST AS I TYPE IT, thus proving i'm using this wireless dongle as my connection.
The packet indicator will tell you immediately if your connected or not. [/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-24
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I found NEITHER of the downloadable packages show as having a wireless connection on my laptop, if they don't show your connection either.......all is not lost......right click on the taskbar on the top of your screen, it opens a drop down list.
Click on +add to panel tab, then scroll down to System and Hardware tab.
In here you will find Network Manager, add this to the panel, when you close the applet manager, IT MAY Show the wireless, but most likely wont.
Reboot your PC, this should then show the wireless connection like this  : 

[IMG]http://i58.photobucket.com/albums/g261/PostHost/Screenshots/Screenshot.png[/IMG]

If you look above the letters `ufo` in the address bar of the screenshot, you will see the wireless applet on the taskbar.The background your seeing is THIS POST AS I TYPE IT, thus proving i'm using this wireless dongle as my connection.
The packet indicator will tell you immediately if your connected or not. [/COLOR][/SIZE][/FONT][/B]

You are great!

I tried what you said to do, and it worked. I can't believe it. I didn't even do anything, didn't even have to do any of these fancy driver installations everyone is talking about, and I'm on-line. What you said, that is exactly what happened. I added the Network Manager to the panel (which is something I thought I already HAD on the panel because further to the right on the panel there is already an icon having two monitors on it just like you also have. I thought that WAS the Network Manager. But sure enough, when i clicked on "add", another such icon appeared to the left-- just as you said it would). And as you said, nothing happened. Actually, even when I rebooted nothing happened. But then, I was playing with the icon on the right, changing some settings...and all of a sudden an option appeared for the "kyocera". I clicked on that option, and the icon changed into a sort of a whirly form, and was spinning-- like it was thinking. I think it was doing some sort of configuration. 15-20 seconds later it stopped spinning, and changed form again, into a bar diagram showing signal strength. And when I move my curser over it, a message comes: "Wireless network connection to 'KR1' (73%)'.  And when I click on the left icon (the one you showed me to add), a window opens like the one you've posted here, showing signal strength. And that signal strength shows "86%". 

And it seems to be moving around the web quickly enough. Actually, I am not really noticing any difference in speed so far with simple web browsing, compared with when I had the evdo card hooked directly up to my laptop. Although I haven't tried any bigger downloads or anything.

But three questions:

1. When I went to the [www.speedtest.net](www.speedtest.net) website and checked the speed, it is showing A LOT slower upload and download speed then when I had the evdo card hooked up directly to my laptop. It used to show 1.2 mb/sec download speed (with evdo card hooked up directly to laptop). Now, with WG111v2 and the evdo plugged into the kyocera router, it gives download speeds of 300-400 kb/s. I don't know what accounts for the difference in speed. Now, my laptop is somewhat old and only has USB type 1 ports in it. But still, the USB 1 port is far faster than the online download speed. I forget exactly what a USB 1 port will carry, but it is something like 15 mb/sec. And the evdo card when it was plugged directly into my laptop, that was also plugged into the same USB type 1 port. And the WG111v2 should be able to manage 58 mb/sec. So why the speedtest is so much slower, I do not know.

2. If I were to re-set up this connection using for example the driver you suggested, or one of the others that others have suggested on other ubuntu discussion threads, then is it likely that the speedtest download speed would increase?

3. Do I need to set up a security protocol? What is it called, I think WEP, right? That is the lesser of two grades of security. I haven't set up any sort of security or encryption on this connection.

Now, we live in a rural area and there aren't really any houses quite close by to jump on our connection. Nor are there any passersby who would want to do so. So maybe we don't need anything. But please let me know what you think about this, and if we should choose to set something up, how it would be done.

Thanks so much!

---

### Post by Azoix on 2007-07-25
> **swarup said:**
> You are great!

I tried what you said to do, and it worked. I can't believe it. I didn't even do anything, didn't even have to do any of these fancy driver installations everyone is talking about....edited slightly for shortening... whirly form, and was spinning-- like it was thinking. I think it was doing some sort of configuration. 15-20 seconds later it stopped spinning.....when I move my curser over it, a message comes: "Wireless network connection to 'KR1' (73%)'.  And when I click on the left icon (the one you showed me to add), a window opens like the one you've posted here, showing signal strength. And that signal strength shows "86%"....
**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]Congratulations !!! Well Done[/COLOR][/SIZE][/FONT]**

And it seems to be moving around the web quickly enough. Actually, I am not really noticing any difference in speed so far with simple web browsing, compared with when I had the evdo card hooked directly up to my laptop. Although I haven't tried any bigger downloads or anything.....
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]Online speed is not connection related, it is governed by the supplier, ISP, file-source, web-load, etc.
All the wireless is for , is so you can sit outside and play on the 'net, without needing a LONG ethernet cable.It WILL NOT increase your speed in ANYWAY[/COLOR][/SIZE][/FONT][/B]

But three questions:

1. When I went to the [www.speedtest.net](www.speedtest.net) website and checked the speed, it is showing A LOT slower upload and download speed then when I had the evdo card hooked up directly to my laptop. It used to show 1.2 mb/sec download speed (with evdo card hooked up directly to laptop). Now, with WG111v2 and the evdo plugged into the kyocera router, it gives download speeds of 300-400 kb/s. I don't know what accounts for the difference in speed. ...[COLOR="Lime"]irrelevent[/COLOR].... WG111v2 should be able to manage 58 mb/sec.[COLOR="Lime"] ** 54Mbps MAX **[/COLOR]. So why the speedtest is so much slower, I do not know.[COLOR="Lime"][B][FONT="Comic Sans MS"][SIZE="3"]Mine is the same, this laptop does 2358/365 or something similar from a 5088Kbps connection, Windows box does 4799Kbps but only 298Kbps upload from a max of 384Kbps. Linux seems slower on down but MUCH faster on upload.
[/SIZE][/FONT][/B].[/COLOR]

2. If I were to re-set up this connection using for example the driver you suggested, or one of the others that others have suggested on other ubuntu discussion threads, then is it likely that the speedtest download speed would increase?[COLOR="Lime"]**[FONT="Comic Sans MS"][SIZE="3"]UNKNOWN, but i doubt it.I think it's to do with the kernel connection to the internet, window's can be tweaked in TCP/IP settings and other area's to speed it up, but i don't know enough about linux yet to know how to tweak it[/SIZE][/FONT]**.[/COLOR]

3. Do I need to set up a security protocol? What is it called, I think WEP, right? That is the lesser of two grades of security. I haven't set up any sort of security or encryption on this connection.

Now, we live in a rural area and there aren't really any houses quite close by to jump on our connection. Nor are there any passersby who would want to do so. So maybe we don't need anything. But please let me know what you think about this, and if we should choose to set something up, how it would be done.[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]I would doubt it, if you have limited passers-by, and neighbours are more than 80 metres** away, i wouldn't worry.I would set it up and make sure it works, for travelling purposes, if you wish a secure connection away from home, then turn it off.Then it's one less fail point in your connection to worry about, if things break-down.
** please don't anybody feel they have to tell me you can boost the range of your wireless, iv'e had the pringles antenna on the roof for 5 years......., i know you can do it, but it's irrelevent in this discussion.[/COLOR][/SIZE][/FONT][/B]

Thanks so much!

**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I answered and edited as i went, i did it this way just because it's been a LONG day, and i'm knackered, couldn't be arsed writing it all out for you......PM me if you need any explanation,or if my descriptions are un-intelligable.[/COLOR][/SIZE][/FONT]**

---

### Post by swarup on 2007-07-25
Everything you wrote was quite clear.

Just a few specific follow-up questions:

You wrote,

"Online speed is not connection related, it is governed by the supplier, ISP, file-source, web-load, etc.
All the wireless is for , is so you can sit outside and play on the 'net, without needing a LONG ethernet cable.It WILL NOT increase your speed in ANYWAY"

Isn't online speed governed by both one's connection speed and the speed at which the incoming info is sent from the supplier? From what I've understood, once one's connection speed exceeds the speed at which the incoming info is sent from the supplier, then the supplier's speed becomes the rate-limiting step. But if one's connection speed is less than the speed at which the incoming info is sent from the supplier, then the connection speed is the rate-limiting step. Isn't this true?

For example, before getting this evdo, I had a dial-up modem. There, the dial-up modem's snail-like speeds were what dictated the browsing and download speeds. In contrast, if one has a fiberoptic connection, then the supplier's speed will dictate the speed of browsing and download. Correct me if I am wrong.

You wrote,

"So why the speedtest is so much slower [with the evdo router compared with having the evdo directly connected to the computer], I do not know. Mine is the same, this laptop does 2358/365 or something similar from a 5088Kbps connection, Windows box does 4799Kbps but only 298Kbps upload from a max of 384Kbps. Linux seems slower on down but MUCH faster on upload."

I did a firmware update of the router yesterday, and now it is working faster. It gets 700-800 kbps download on the [www.speedtest.net](www.speedtest.net). But still, that is only about 60% what I get with the evdo directly connected i.e. 1.2 mb/sec. My point was that, when none of the individual components (USB type 1 port, WG111v2, router, evdo) are rate-limiting, then why would introducing the router into the connection make it slower? There must be somewhere we could find some sort of info on this.

I wrote,

"If I were to re-set up this connection using for example the driver you suggested, or one of the others that others have suggested on other ubuntu discussion threads, then is it likely that the speedtest download speed would increase?"

You replied,

"UNKNOWN, but i doubt it.I think it's to do with the kernel connection to the internet, window's can be tweaked in TCP/IP settings and other area's to speed it up, but i don't know enough about linux yet to know how to tweak it."

My point here is that, with evdo card directly connected to the computer I get 1.2 mb/second download speed. So by this it is clear that Linux, the USB type 1 port, and the evdo card are all quite capable of 1.2 mb/sec speed. In other words, none of these components are responsible for the slowing when I introduce the router. It has to be the fault of something which was newly introduced. That is, either the router, or the WG111v2, or the driver which Linux is using for the WG111v2. And since we know the router and the WG111v2 are both capable of speeds well beyond 800 kbps, then the only thing left is the driver Linux uses to manage the WG111v2. And that is why I asked you whether any of the other drivers -- either the one you suggested or one of the others on the ubuntu forums -- might allow the information to travel more quickly than then native driver currently being used in Linux.

And if in fact there would not be any difference, then my questions are:

1. Why is the router connection slower than the direct evdo connection?

2. Why is everyone struggling to set up these complex alternate driver solutions using NDISwrapper etc etc, when the native Linux driver works fine with WG111v2 out of the box???

---

### Post by pickarooney on 2007-07-25
Hope you don't mind if I jump in here. I have a new Netgear WG111V2 USB dongle which is recognised
as such when I connect it an in KDE's wireless manager I can see my (unencrypted) router but cannot for the life of me connect to it. I've tried all the configurations of IP, DHCP, Gateway, net mask and DNS that I could think of but with no succes. I managed two days ago to connect another laptop with a Netgear PCMCIA card so the router works. That was with Ubuntu Dapper, I'm using Kubuntu Feisty.

I'm lost as to where I'm going wrong.

---

### Post by Azoix on 2007-07-26
> **swarup said:**
> Everything you wrote was quite clear.

Just a few specific follow-up questions:

You wrote,

"Online speed is not connection related, it is governed by the supplier, ISP, file-source, web-load, etc.
All the wireless is for , is so you can sit outside and play on the 'net, without needing a LONG ethernet cable.It WILL NOT increase your speed in ANYWAY"

Isn't online speed governed by both one's connection speed and the speed at which the incoming info is sent from the supplier? From what I've understood, once one's connection speed exceeds the speed at which the incoming info is sent from the supplier, then the supplier's speed becomes the rate-limiting step. But if one's connection speed is less than the speed at which the incoming info is sent from the supplier, then the connection speed is the rate-limiting step. Isn't this true?[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]I think i understand what you mean here, but not sure,The irrelevence i mentioned, was solely from the POV that you will NOT EXCEED the available speed of a USB 1.1 port, i think they do 11-12Mbps, so unless you exceed that on an ADSL2+ connection, i wouldn't think it will come into the equation.
I am using a USB 1.1 port, and have never suffered from a lack of speed, even flat out at 11Mbps the flow into your PC would need to exceed 11.5 MEGABYTES per second to be held up by port speed, i am yet to see that sort of downspeed short of a 100Mb 'net access.
I don't think anyone in a private residence will get that, but i would love to hear if anyone does.
And how much they pay for the priviledge.[/COLOR][/SIZE][/FONT][/B]

For example, before getting this evdo, I had a dial-up modem. There, the dial-up modem's snail-like speeds were what dictated the browsing and download speeds. In contrast, if one has a fiberoptic connection, then the supplier's speed will dictate the speed of browsing and download. Correct me if I am wrong.**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]Even with a fibre node in your basement, and a million dollar server in the loungeroom, your still at the mercy of the file-hoster as to the download speed, Example : My FTP site here, was being abused something horrid, i had unlimited upload speed set, so anyone connected got all my speed for transfer, this slowed my browsing to a crawl, so i swiched it off, then i set it with a limited speed for outgoing files and all's fine for me now, just takes longer for leeches to get my shared files.[/COLOR][/SIZE][/FONT]**

You wrote,

"So why the speedtest is so much slower [with the evdo router compared with having the evdo directly connected to the computer], I do not know. Mine is the same, this laptop does 2358/365 or something similar from a 5088Kbps connection, Windows box does 4799Kbps but only 298Kbps upload from a max of 384Kbps. Linux seems slower on down but MUCH faster on upload."

I did a firmware update of the router yesterday, and now it is working faster. It gets 700-800 kbps download on the [www.speedtest.net](www.speedtest.net). But still, that is only about 60% what I get with the evdo directly connected i.e. 1.2 mb/sec. My point was that, when none of the individual components (USB type 1 port, WG111v2, router, evdo) are rate-limiting, then why would introducing the router into the connection make it slower? There must be somewhere we could find some sort of info on this.[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]Sorry , i think i misunderstand this, your saying that on Ubuntu, the same computer is faster connected to an ethernet cable ? If this is correct, i would suggest a driver issue as you summise, but in which area, i don't know, it would only be a guess by me, not being able to see how you set things up.It sounds odd that the wireless shows less than the ethernet on the same O/S, they use the same connection outbound, same modem.On that note, try adding the wireless to the router, it may not be turned on automatically.Also check the adaptor is set in the allowed devices for your Wireless Access Point.And set the WAP to Infrastructure, not Ad-Hoc or Roam or Auto.
Why you felt the need to upgrade the firmware,i don't know.This is done most commonly to repair any bugs or clashes, if the router worked on the old f/w, you should have left it alone.(Just My Opinion, not an authority on component level driver's.)[/COLOR][/SIZE][/FONT][/B]

I wrote,

"If I were to re-set up this connection using for example the driver you suggested, or one of the others that others have suggested on other ubuntu discussion threads, then is it likely that the speedtest download speed would increase?"

You replied,

"UNKNOWN, but i doubt it.I think it's to do with the kernel connection to the internet, window's can be tweaked in TCP/IP settings and other area's to speed it up, but i don't know enough about linux yet to know how to tweak it."

My point here is that, with evdo card directly connected to the computer I get 1.2 mb/second download speed. So by this it is clear that Linux, the USB type 1 port, and the evdo card are all quite capable of 1.2 mb/sec speed. In other words, none of these components are responsible for the slowing when I introduce the router. It has to be the fault of something which was newly introduced. That is, either the router, or the WG111v2, or the driver which Linux is using for the WG111v2. And since we know the router and the WG111v2 are both capable of speeds well beyond 800 kbps, then the only thing left is the driver Linux uses to manage the WG111v2. And that is why I asked you whether any of the other drivers -- either the one you suggested or one of the others on the ubuntu forums -- might allow the information to travel more quickly than then native driver currently being used in Linux.**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]See above reply[/COLOR][/SIZE][/FONT]**

And if in fact there would not be any difference, then my questions are:

1. Why is the router connection slower than the direct evdo connection?**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]See above reply[/COLOR][/SIZE][/FONT]**


2. Why is everyone struggling to set up these complex alternate driver solutions using NDISwrapper etc etc, when the native Linux driver works fine with WG111v2 out of the box???**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Lime"]Very good question, to which i have no answer.....[/COLOR][/SIZE][/FONT]**

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]You ask some very complex questions here, i think i understood most of it, but can't give you the answer's you wish, as i am yet to find them myself....
I have an idea to try though, delete the driver your using for the wg111v2 now, i think you went with the ME one ?, try using one of the other's now you know that one at least works, the driver for XP or Win2000 may work for you OK, when they don't for me.Different PC may read it OK. open terminal and type sudo ndiswrapper wlan0 -r wg111v2
 if wlan0 is the wireless adaptor on your PC.
Find this by using iwconfig  command first.
You may need to use a small e instead of the small r after the dash, the command ndiswrapper -h will open all relevent commands and you can use the correct letter associated with your version to remove the driver.Then replace it with a new one, in the folder your using now, then re-do the /??/??/wg111v2.inf command in terminal to get ndiswrapper to use the new driver instead. See if this makes a difference at all and let us know.
[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-27
Hi there, and sorry for the delayed reply. I've had to be out all day today.
Now it's very late and I'm just exhausted, so I'll give the nutshell reply which is all I can manage right now.

It was difficult for me to tell by reading your replies, whether you were following what I was trying to express. One thing you wrote made me think you may not have understood at least part-- and that is that I am not talking about using an ethernet cable connection. I don't even have an ethernet port on my laptop. What I was comparing was the following:

I have an evdo card. That is, it is like a cellular phone only you can't talk into it. The evdo card aka "aircard" connects to the internet using the same technology as a cellular phone. And the evdo card is a usb device-- it connects to my laptop by directly plugging into the usb type 1 port. And when I connect like that, I get download speeds of 1 mb/sec. 

Now, when I connect as I described above, then I am the only person who can go online using that aircard. Only one user can use it at a time. 

So in order that others in the house should also be able to go online using the aircard I have, I purchased a special router which is made only for aircards. It will not work with a cable modem or DSL or anything else. The way this router connects to the internet is via an "aircard". That aircard connects to the internet using Sprint's cellular phone towers. So, my aircard plugs into the router via usb port. And then the router in turn conects to my computer wirelessly using the WSG111v2. If my laptop had an ethernet port, I would also have the option of connecting the laptop and the router using ethernet cable. But not having an ethernet port, I have to use the wireless connection using WG111v2. 

So my two options are:

1) Plug the cellular phone modem (the "aircard") directly into the usb1 port of my laptop;

or

2) Plug the cellular phone modem (the "aircard") into the aircard router (Kyocera K1) and connect to the router using my WG111v2.

These two above options should yield the same download speeds. --But they don't. Option #1 gives me download speeds of 1.2 mb/sec, whereas option #2 gives download speeds of 700 kbps. 

It is this difference in speed that I am seeking to understand and remove. And it is about this difference, that I was commenting that it should not be since all the components of the router pathway have the capability to handle a 1.2 mb/sec download speed without any problem. That is to say the router itself, and the WG111v2 both have the capability to go far faster than 1mb/sec. So if the speed using them is only 700 kbps, then something else must be limiting the speed. Which is where I started thinking that it may be the driver.

In reply to your last suggestion, about using different Windows drivers with NDISwrapper.  My answer is that I am not using NDISwrapper right now at all. Not with ME, and not with any Windows driver. I am just using the native Linux driver which you yourself showed my how to successfully establish. And not having even tried yet to establish a connection using NDISwrappter, and having a connection which is working now albeit slightly slower than it might, nevertheless I feel somewha shy ort hesitant to delete the native Linux driver and start experimenting with the Windows drivers, when I have a connection that is basically working fine. In order to experiment with NDISwrapper, would I have to delete the Linux native driver I am using? If so, then I think I'll  a little while-- until I'm a little more savy about handling the pathways of software management in Linux. I'll surely try when I'm a litle braver and well schooled in how this stuff works in Linux. Because right now your description of how this could be tried in NDISwrapper, is looking a little complex and daunting, even scary. The last thing I would want is to end up in a spot where nothing is working and I can't get out of it. It would be one thing if I didn't have any system working with the router. But now I do have one system working, and it is basically working well. ....So I feel shy to tamper with it and risk losing the connection. 

Looking forward to your highly useful and educational reply as always,
Many thanks,
Swarup

---

### Post by Azoix on 2007-07-27
> **swarup said:**
> Hi there, ...removed...
Many thanks,
Swarup
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I understand now, i don't think this is part of this thread, but we can always start another .This is mostly on the wg111v2 issue's so we will keep it on that. 
But to start off...
I ***_[COLOR="Red"]think[/COLOR]_*** your having a driver issue.
Not a bad driver, but perhap's a mismatched one.
Start a thread titled EVDO and the Kyocera model number or  something similar, so other's with the same configuration, can also benefit from any help you may find or other's can offer, you may also find someone already found the answer to the question.........
I know nothing of the EVDO card you mention, i don't think it's available in Australia, but *we* do have wireless broadband if you wish to use it, it would be similar in design i expect.
The Kyocera stuff i know nothing of, i have never seen more than photo's, i have never had an order for one at work, and couldn't even tell you who supplies them in Aust, if you can even get them.So i'm not going to be much help with it i'm afraid.
If it were me, i would look at trying to revert back to your old firmware driver's on the router and anything else you updated, and see if the same results occur.
I would then proceed to look at the added items that make the change occur.
You state it's fine connected modem/pc but bad when modem/router/pc via wireless.
I would concentrate my efforts on the router, it seems the likely point of delay to me.
Did you try another of the driver's for the wg111v2  yet ? 
I would try that too, it may help, may also do bugger all !!
As an aside, i was suffering tremendous line speed degradation through to loss of signal completely , on this Ubuntu laptop, where using my Windoze laptop in the same location, i got full tilt boogie all the way.
I put the wireless dongle on a 1 metre USB extension, tossed that over an arm chair nearby, but pointing in a direction AWAY from the PC and bingo -- full speed on Ubuntu too !!! 

Go Figure .....[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-07-28
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I understand now, i don't think this is part of this thread, but we can always start another .This is mostly on the wg111v2 issue's so we will keep it on that.   .............................

Go Figure .....[/COLOR][/SIZE][/FONT][/B]

Somehow I've been thinking my problem is more related with the WG111v2 and its driver, than with the router. But I appreciate your suggestions, and will think on how I can integrate them. I would certainly start experimenting with different Netgear drivers, but I'm afraid to lose what I've got now. At least it is working. Is it easy to delete the driver I've got working with the WG111v2 now, and then if the one I experiment with doesn't work or doesn't work well, to go back to the original driver which I deleted?

As for the router's firmware, the download speed was only 400 dbps with the original firmware and once I updated it (which was what Kyocera's technical support person told me to do), then the speed jumped up to 700 kbps.

---

### Post by Azoix on 2007-07-28
Somehow I've been thinking my problem is more related with the WG111v2 and its driver, than with the router. But I appreciate your suggestions, and will think on how I can integrate them. I would certainly start experimenting with different Netgear drivers, but I'm afraid to lose what I've got now. At least it is working. Is it easy to delete the driver I've got working with the WG111v2 now, and then if the one I experiment with doesn't work or doesn't work well, to go back to the original driver which I deleted?
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]The removal is very simple, just type ndiswrapper --help in a terminal window, this will list the commands you can use, just find the one for driver removal, use it and re-install one of the other's, and see if things improve.
All you need to do is type ndiswrapper -?? wg111v2 and hit enter, ?? being the letter required in the help section, it will then remove the driver from the NDISWRAPPER section of usage, NOT FROM THE PC, or the folder.So you can re-use it later.Just re-install the working one again if a different one makes it worse or anything.[/COLOR][/SIZE][/FONT][/B]

As for the router's firmware, the download speed was only 400 dbps with the original firmware and once I updated it (which was what Kyocera's technical support person told me to do), then the speed jumped up to 700 kbps.
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]If it was Tech. Support that advised the firmware upgrade, i would leave it alone, but can you revert if you wanted ? just as a test, if all else fails?
I have a suspicion that the slow down is between Netgear and Kyocera, they may be incompatable, and thus limited in connectivity.
I can't say for sure, just guessing, not being able to see things for myself, i do know that wireless can be a right pain in the klacker when it wants to be.[/COLOR][/SIZE][/FONT][/B]

---

### Post by swarup on 2007-08-21
> **Azoix said:**
> [B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I found NEITHER of the downloadable packages show as having a wireless connection on my laptop, if they don't show your connection either.......all is not lost......right click on the taskbar on the top of your screen, it opens a drop down list.
Click on +add to panel tab, then scroll down to System and Hardware tab.
In here you will find Network Manager, add this to the panel, when you close the applet manager, IT MAY Show the wireless, but most likely wont.
Reboot your PC, this should then show the wireless connection like this  : 

[IMG]http://i58.photobucket.com/albums/g261/PostHost/Screenshots/Screenshot.png[/IMG]

If you look above the letters `ufo` in the address bar of the screenshot, you will see the wireless applet on the taskbar.The background your seeing is THIS POST AS I TYPE IT, thus proving i'm using this wireless dongle as my connection.
The packet indicator will tell you immediately if your connected or not. [/COLOR][/SIZE][/FONT][/B]

I followed these instructions a month ago to set up the configuration for the WG111v2 Netgear adapter using the native driver in Feisty, and it worked beautifully. Now I want to set the same Netgear adapter up on another computer, and I followed the above instructions but it did not work. Means, the applet got set up as described, but the network was not established.

I think it is because a month ago when I did it, just prior to that I had gone into the config file to put the listing of the Netgear adaptor there. That way the computer was recognizing the adapter, and the whole network configuration worked. But now I forget the terminal command to open that config file. I need it so I can insert the same listing for the Netgear adapter, into another computer.

Can someone tell me the terminal command to open this config file? (Please don't ask the name of the specific config file, because I do not remember. Hopefully by reading the above description, you will know which config file it is.)

---

