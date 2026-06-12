---
title: "Ubuntu 18.10 WiFi not detecting anything"
date: 2018-12-31
forum: Apple Hardware Users
---

### Post by mwei19 on 2018-12-31
Hello All~! 
I recently dug up my old Macbook Pro (Mid-2010) from its grave and decided to load Ubuntu 18.10 on it...just for fun and for the experience. 

I managed to get everything up and running except for the WiFi. 
I was reading up a lot on other fellow Ubuntu users having the same issues with the same wireless network adapter (**BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b]**) and followed their footsteps in resolving the issue to finally get the WiFi to detect the available WiFi networks by installing **bcmwl-kernel-source. **After installing **bcmwl-kernel-source** and going to the **Software & Updates** GUI to enable the usage of the **proprietary driver **the WiFi started to detect the available wireless networks. However, the WiFi detecting the available networks was not/is not consistent. After several reboots the computer would not detect any wireless networks again. I have purged and reinstalled **bcmwl-kernel-source** multiple times and checked and unchecked the usage of the **proprietary driver** multiple times as well and now I can't get the computer to detect any wireless networks at all. 

Please advise. 

I am currently using a wired Ethernet connection with no issues. 

***$rfkill list***
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no[ATTACH=CONFIG]282061[/ATTACH]

***$sudo modprobe -r wl***
No Result


I have also attached the results of running the wireless info script. 

[ATTACH=CONFIG]282062[/ATTACH]

[ATTACH=CONFIG]282063[/ATTACH]

---

### Post by jeremy31 on 2018-12-31
Moved to Apple hardware

---

### Post by mwei19 on 2018-12-31
> **jeremy31 said:**
> Moved to Apple hardware

Thanks for pointing me to the right direction/moving the thread, I appreciate it! :smile:

---

### Post by gsahli on 2018-12-31
Install firmware-b43-installer instead.
Source code would need compiling- did you?

---

### Post by mwei19 on 2018-12-31
> **gsahli said:**
> Install firmware-b43-installer instead.
Source code would need compiling- did you?

Just installed **firmware-b43-install **and rebooted. Still not detecting any wireless networks.

---

### Post by jeremy31 on 2018-12-31
You likely need ```
sudo apt install bcmwl-kernel-source
```

---

### Post by mwei19 on 2018-12-31
> **jeremy31 said:**
> You likely need ```
sudo apt install bcmwl-kernel-source
```

yup, I ran that install command earlier already alongside the newly suggested 

***$sudo apt-get install ***[B]*firmware-b43-install*
[/B]

***$[COLOR=#000000][FONT=&quot]sudo apt install bcmwl-kernel-source[/FONT][/COLOR]***
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version (6.30.223.271+bdcom-0ubuntu4).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by mwei19 on 2018-12-31
Also, just noticed this...

[I][B]$dmesg | grep b43

[/B][/I][   26.947909] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   26.988187] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   26.988210] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   60.012235] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  332.232191] b43-phy0 ERROR: DMA RX reset timed out
[  332.508180] b43-phy0 ERROR: DMA TX reset timed out

was reading that some other people ran into this on other linux distributions and they resolved the issue by downgrading the kernel?

---

### Post by jeremy31 on 2018-12-31
Actually I would suggest using Ubuntu 18.04 as it is apparent from the wireless script result that something is wrong with bcmwl-kernel-source in 18.10

---

### Post by mwei19 on 2018-12-31
> **jeremy31 said:**
> Actually I would suggest using Ubuntu 18.04 as it is apparent from the wireless script result that something is wrong with bcmwl-kernel-source in 18.10

DOH! [insert facepalm] gah hahaha, what a pain...I guess i'll reload with Ubuntu 18.04 if this doesn't get resolved within the next couple of days then. Literally had to re-do this installation on this macbook pro 3 times already, lmao! :lolflag:
Finally got everything to where I want them now...except for this WiFi issue! :(

---

### Post by mwei19 on 2018-12-31
OK! Quick update! 

Did some more research about this issue and tried out some new things! Was eventually able to finally get the WiFi to detect the wireless networks again to some success! 
However, the successes were always short lived. The WiFI would work as expected for just two reboots...after the third reboot the WiFI would not detect any wireless networks...again! Very frustrating, haha! Below is what I did, thus far, that allowed the WiFi to pick up the networks again for two reboots:

Round 1~

Removed/purged the previously installed **bcmwl-kernel-source** and the [B]firmware-b43-install 

[/B]Changed the **Software & Updates proprietary driver **selection to NOT use the proprietary driver. 

Downloaded and installed **bcmwl-kernel-source_6.30.223.271** from this [website]("https://packages.ubuntu.com/bionic/amd64/bcmwl-kernel-source/download") and manually installed the driver. 


_********After I did this, the WiFI started to work again, for just 2 reboots********_

Round 2~

Froze the package to make sure nothing changes/gets updated for the driver in question
***$sudo apt-mark hold bcmwl-kernel-source***

Ran ***$rfkill unblock all*** just in case

Modified the ***/etc/modprobe.d/blacklist.conf ***file by adding:
[B]blacklist brcmsmac
blacklist bcma
blacklist b43[/B]

[U][B]***wasn't really sure if this is necessary but did it anyway. After the changes were set, WiFi started working again...for just 2 reboots*****

[/B][/U]This is where I am currently am right now, with the WiFi not working again. ****:frown:

---

### Post by mwei19 on 2018-12-31
The current dmesg situation:

[I][B]$dmesg | grep wl
[/B][/I]
[   26.165736] wl: loading out-of-tree module taints kernel.
[   26.165742] wl: module license 'MIXED/Proprietary' taints kernel.
[   26.172846] wl: module verification failed: signature and/or required key missing - tainting kernel
[   26.232842] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   31.870964] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   61.166248] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   63.267559] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   83.688050] ERROR @wl_notify_scan_status : 
[   83.688053] wlp2s0 Scan_results error (-22)
[  117.072222] ERROR @wl_notify_scan_status : 
[  117.072230] wlp2s0 Scan_results error (-22)
[  160.044124] ERROR @wl_notify_scan_status : 
[  160.044128] wlp2s0 Scan_results error (-22)
[  198.760051] ERROR @wl_notify_scan_status : 
[  198.760054] wlp2s0 Scan_results error (-22)
[  204.769365] bridge-wlp2s0: device is wireless, enabling SMAC
[  204.769368] bridge-wlp2s0: up
[  204.769374] bridge-wlp2s0: attached
[  204.783274] bridge-wlp2s0: disabling the bridge on dev down
[  204.783405] bridge-wlp2s0: down
[  204.783414] bridge-wlp2s0: detached
[  204.820645] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  205.863526] ERROR @wl_notify_scan_status : 
[  205.863529] wlp2s0 Scan_results error (-22)
[  221.004192] ERROR @wl_notify_scan_status : 
[  221.004196] wlp2s0 Scan_results error (-22)
[  225.176080] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  225.177064] bridge-wlp2s0: device is wireless, enabling SMAC
[  225.177067] bridge-wlp2s0: up
[  225.177071] bridge-wlp2s0: attached
[  225.702646] bridge-wlp2s0: disabling the bridge on dev down
[  225.703559] bridge-wlp2s0: down
[  225.703568] bridge-wlp2s0: detached
[  225.744326] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  226.796093] ERROR @wl_notify_scan_status : 
[  226.796097] wlp2s0 Scan_results error (-22)
[  230.028077] ERROR @wl_notify_scan_status : 
[  230.028081] wlp2s0 Scan_results error (-22)
[  243.976073] ERROR @wl_notify_scan_status : 
[  243.976077] wlp2s0 Scan_results error (-22)
[  258.984051] ERROR @wl_notify_scan_status : 
[  258.984055] wlp2s0 Scan_results error (-22)
[  274.000095] ERROR @wl_notify_scan_status : 
[  274.000098] wlp2s0 Scan_results error (-22)
[  289.000060] ERROR @wl_notify_scan_status : 
[  289.000064] wlp2s0 Scan_results error (-22)

---

### Post by mwei19 on 2018-12-31
Another update with less than 20 min to go before its the New Year, woot woot! 

Did another round of playing around and FINALLY got it! Well...I hope so at least, the WiFi has finally been holding up after four consecutive reboots and coming back from a hibernation session/test! 

What I did was install **firmware-b43-installer** again and then removed the previously installed **bcmwl-kernel-source** and somehow this did the trick this time. Not sure what the difference is from before as I did test with this set up earlier before too and the WiFi still wouldn't detect any wireless networks...but now it does. I left the blacklist.conf file relatively the same except commented out the **b43** and **bcm43xx** entries. 

***$sudo apt-get install firmware-b43-installer***

[B][I]$sudo apt remove --purge bcmwl-kernel-source
[/I][/B]
Hoping this will finally be the end of this...will do another round of testing tomorrow! Keeping my fingers crossed!

---

### Post by mwei19 on 2019-01-02
Quick update after a full day of usage yesterday...seems like the WiFi functionality has stabilized! 

Rebooted the Macbook Pro several times and the WiFi was holding steady after all the reboots and coming back from multiple hibernation sessions.
 
However, for today, now that i'm back at work...the WiFi isn't picking up anything, although I have my Verizon MiFi Jetpack with me. I checked the dmesg messages and all seems to be well. Will check again once I get home to determine if anything is actually wrong with the WiFi again or not. 

May need some guidance on getting the MiFi Jetpack to work with this Macbook Pro if there is nothing wrong with the WiFi! :cool:

---

### Post by mwei19 on 2019-01-03
No cigar from the last update I posted...

Decided to go ahead and wipe my previous 18.10 install and load with 18.04 LTS instead.
Got everything back to as they were when I was still on 18.10 but still am having a lot of issues with getting that WiFi to work properly. 

Found an old solved thread in this forum where the user has the same broadcomm card as me and followed the steps he took to resolve his issue(s) to no avail. 
[https://ubuntuforums.org/showthread.php?t=2346826&page=2](https://ubuntuforums.org/showthread.php?t=2346826&page=2)

If anyone has any suggestions or can guide me to the right path I will greatly appreciate it! Getting pretty frustrated with this WiFi haha! ](*,)

---

### Post by mwei19 on 2019-01-03
New finding...somehow the WiFi works flawlessly, even after reboots and hibernation sessions, at home. Just got home from work to find that the WiFi was working the moment I signed in from home. Did not change any settings or install anything new. Not sure why this macbook WiFi decides not to work when I am at work/not at home...is there some setting that I need to change for it to stabilize when not at home?

---

### Post by chili555 on 2019-01-04
> Not sure why this macbook WiFi decides not to work when I am at work/not at home...is there some setting that I need to change for it to stabilize when not at home?What is different between the two networks? At each place, please run and post: ```
sudo iwlist scan
```Please do not reinstall or change drivers or any other changes until we can pin this down. It is very difficult to keep up when everything changes overnight!> I left the blacklist.conf file relatively the same except commented out the b43 and bcm43xx entries. There is no driver named bcm43xx; commenting or uncommenting it will do nothing at all.  

You should, however, un-blacklist bcma.

---

### Post by mwei19 on 2019-01-04
> **chili555 said:**
> What is different between the two networks? At each place, please run and post: ```
sudo iwlist scan
```Please do not reinstall or change drivers or any other changes until we can pin this down. It is very difficult to keep up when everything changes overnight!There is no driver named bcm43xx; commenting or uncommenting it will do nothing at all.  

You should, however, un-blacklist bcma.

There shouldn't be much of a difference between the networks at work and at home as at work I'm trying to connect to my Verizon Jetpack MiFi  and at home i'm connected to my own wireless router. It's just that when I tested from home, I was able to successfully connect to my home network while also seeing and connect to the Jetpack MiFi for testing. Then the next day, once I power back up, nothing seems to be the same any more, haha! 

$sudo iwlist scan (at work)
```

 lo        Interface doesn't support scanning.

wlan0     No scan results


eth0      Interface doesn't support scanning.un-blacklist bcma

```

Will not be reinstalling or changing drivers, unless instructed, from now on. But for now, I have ***broadcom-sta-dkms*** loaded. I have also reverted the blacklist and uncommented bcma.

---

### Post by chili555 on 2019-01-04
>  But for now, I have broadcom-sta-dkms loaded.But the last word we had was:> What I did was install firmware-b43-installer again and then removed the previously installed bcmwl-kernel-source and somehow this did the trick this time. So things have already changed...again??

---

### Post by mwei19 on 2019-01-04
> **chili555 said:**
> But the last word we had was:So things have already changed...again??

haha, yup, I was reading up more and saw some more things that I could attempt to do and went ahead with playing around with the different things I found. Should I revert back to the previous update message state? My current state is that I have ***broadcom-sta-dkms*** loaded and not ***bcmwl-kernel-source*** or ***firmware-b43-installer***.

---

### Post by chili555 on 2019-01-04
Why would you search for and implement a change from this?> What I did was install firmware-b43-installer again and then removed the previously installed bcmwl-kernel-source and **somehow this did the trick this time.**

WARNING: Incoming rant

Many users assume that the answer to every problem is a different driver. In some cases, they assume an older driver is better; maybe a driver for a different device; maybe any driver!!! I even worked on several cases where the wireless was disabled by the airplane mode switch and the novice user assumed that a different driver would somehow reach out of the screen and move the switch!

It is not always the driver.

End rant.

As I said previously, don't change anything for now. 

Tell me what driver is loaded now:```
lsmod | grep -e wl -e b43
```Whatever you find, check the logs for messages about it:```
dmesg | grep b4
```Or else:```
dmesg | grep wl
```Next, tell me where this driver works and where it does not.

Do not change anything else for now.

---

### Post by mwei19 on 2019-01-04
> **chili555 said:**
> Why would you search for and implement a change from this?

WARNING: Incoming rant

Many users assume that the answer to every problem is a different driver. In some cases, they assume an older driver is better; maybe a driver for a different device; maybe any driver!!! I even worked on several cases where the wireless was disabled by the airplane mode switch and the novice user assumed that a different driver would somehow reach out of the screen and move the switch!

It is not always the driver.

End rant.

As I said previously, don't change anything for now. 

Tell me what driver is loaded now:```
lsmod | grep -e wl -e b43
```Whatever you find, check the logs for messages about it:```
dmesg | grep b4
```Or else:```
dmesg | grep wl
```Next, tell me where this driver works and where it does not.

Do not change anything else for now.

haha, I understand no worries. I was just trying all the different things that I found out there as nothing seemed to work and didn't really have much guidance. But that's different now, heh heh! Also, no worries, won't be changing anything now, unless instructed. 

$lsmod | grep -e wl -e b43
```

wl                   6447104  0cfg80211              622592  1 wl

```

$dmesg | grep wl
```

[   40.071674] wl: loading out-of-tree module taints kernel.
[   40.071679] wl: module license 'MIXED/Proprietary' taints kernel.
[   40.078140] wl: module verification failed: signature and/or required key missing - tainting kernel
[   40.145222] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   56.834492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.028051] ERROR @wl_notify_scan_status : 
[   85.028054] wlan0 Scan_results error (-22)
[  118.056226] ERROR @wl_notify_scan_status : 
[  118.056233] wlan0 Scan_results error (-22)
[  143.624054] ERROR @wl_notify_scan_status : 
[  143.624058] wlan0 Scan_results error (-22)
[  197.028059] ERROR @wl_notify_scan_status : 
[  197.028062] wlan0 Scan_results error (-22)
[  260.040066] ERROR @wl_notify_scan_status : 
[  260.040069] wlan0 Scan_results error (-22)
[  323.044077] ERROR @wl_notify_scan_status : 
[  323.044080] wlan0 Scan_results error (-22)
[  386.056148] ERROR @wl_notify_scan_status : 
[  386.056151] wlan0 Scan_results error (-22)
[  449.028094] ERROR @wl_notify_scan_status : 
[  449.028098] wlan0 Scan_results error (-22)
[  512.100153] ERROR @wl_notify_scan_status : 
[  512.100159] wlan0 Scan_results error (-22)
[  575.112162] ERROR @wl_notify_scan_status : 
[  575.112165] wlan0 Scan_results error (-22)
[  638.056210] ERROR @wl_notify_scan_status : 
[  638.056217] wlan0 Scan_results error (-22)
[  701.092040] ERROR @wl_notify_scan_status : 
[  701.092043] wlan0 Scan_results error (-22)
[  764.068046] ERROR @wl_notify_scan_status : 
[  764.068049] wlan0 Scan_results error (-22)
[  827.076047] ERROR @wl_notify_scan_status : 
[  827.076051] wlan0 Scan_results error (-22)
[  890.088063] ERROR @wl_notify_scan_status : 
[  890.088066] wlan0 Scan_results error (-22)
[  935.428146] ERROR @wl_notify_scan_status : 
[  935.428150] wlan0 Scan_results error (-22)
[  953.064113] ERROR @wl_notify_scan_status : 
[  953.064117] wlan0 Scan_results error (-22)
[ 1016.036058] ERROR @wl_notify_scan_status : 
[ 1016.036061] wlan0 Scan_results error (-22)
[ 1079.076068] ERROR @wl_notify_scan_status : 
[ 1079.076071] wlan0 Scan_results error (-22)
[ 1142.088089] ERROR @wl_notify_scan_status : 
[ 1142.088097] wlan0 Scan_results error (-22)
[ 1205.060047] ERROR @wl_notify_scan_status : 
[ 1205.060050] wlan0 Scan_results error (-22)
[ 1268.036047] ERROR @wl_notify_scan_status : 
[ 1268.036050] wlan0 Scan_results error (-22)
[ 1331.044053] ERROR @wl_notify_scan_status : 
[ 1331.044057] wlan0 Scan_results error (-22)
[ 1394.056109] ERROR @wl_notify_scan_status : 
[ 1394.056112] wlan0 Scan_results error (-22)
[ 1457.092062] ERROR @wl_notify_scan_status : 
[ 1457.092065] wlan0 Scan_results error (-22)
[ 1520.072154] ERROR @wl_notify_scan_status : 
[ 1520.072157] wlan0 Scan_results error (-22)
[ 1583.048223] ERROR @wl_notify_scan_status : 
[ 1583.048230] wlan0 Scan_results error (-22)
[ 1646.056095] ERROR @wl_notify_scan_status : 
[ 1646.056098] wlan0 Scan_results error (-22)
[ 1709.096197] ERROR @wl_notify_scan_status : 
[ 1709.096204] wlan0 Scan_results error (-22)
[ 1772.104211] ERROR @wl_notify_scan_status : 
[ 1772.104218] wlan0 Scan_results error (-22)
[ 1835.108043] ERROR @wl_notify_scan_status : 
[ 1835.108046] wlan0 Scan_results error (-22)
[ 1898.084085] ERROR @wl_notify_scan_status : 
[ 1898.084088] wlan0 Scan_results error (-22)
[ 1961.064064] ERROR @wl_notify_scan_status : 
[ 1961.064067] wlan0 Scan_results error (-22)
[ 2024.104194] ERROR @wl_notify_scan_status : 
[ 2024.104201] wlan0 Scan_results error (-22)
[ 2087.076087] ERROR @wl_notify_scan_status : 
[ 2087.076091] wlan0 Scan_results error (-22)
[ 2150.084044] ERROR @wl_notify_scan_status : 
[ 2150.084047] wlan0 Scan_results error (-22)
[ 2213.096203] ERROR @wl_notify_scan_status : 
[ 2213.096209] wlan0 Scan_results error (-22)
[ 2276.072207] ERROR @wl_notify_scan_status : 
[ 2276.072214] wlan0 Scan_results error (-22)
[ 2339.108050] ERROR @wl_notify_scan_status : 
[ 2339.108054] wlan0 Scan_results error (-22)
[ 2402.048081] ERROR @wl_notify_scan_status : 
[ 2402.048081] wlan0 Scan_results error (-22)
[ 2465.064176] ERROR @wl_notify_scan_status : 
[ 2465.064182] wlan0 Scan_results error (-22)
[ 2528.036113] ERROR @wl_notify_scan_status : 
[ 2528.036116] wlan0 Scan_results error (-22)
[ 2591.048139] ERROR @wl_notify_scan_status : 
[ 2591.048142] wlan0 Scan_results error (-22)
[ 2654.088174] ERROR @wl_notify_scan_status : 
[ 2654.088181] wlan0 Scan_results error (-22)
[ 2662.952168] ERROR @wl_notify_scan_status : 
[ 2662.952176] wlan0 Scan_results error (-22)
[ 2717.092039] ERROR @wl_notify_scan_status : 
[ 2717.092042] wlan0 Scan_results error (-22)
[ 2748.175226] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2748.509543] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2749.540071] ERROR @wl_notify_scan_status : 
[ 2749.540074] wlan0 Scan_results error (-22)
[ 2752.612101] ERROR @wl_notify_scan_status : 
[ 2752.612108] wlan0 Scan_results error (-22)
[ 2761.832090] ERROR @wl_notify_scan_status : 
[ 2761.832093] wlan0 Scan_results error (-22)
[ 2776.040163] ERROR @wl_notify_scan_status : 
[ 2776.040170] wlan0 Scan_results error (-22)
[ 2809.064059] ERROR @wl_notify_scan_status : 
[ 2809.064063] wlan0 Scan_results error (-22)
[ 2852.072097] ERROR @wl_notify_scan_status : 
[ 2852.072101] wlan0 Scan_results error (-22)
[ 2905.064148] ERROR @wl_notify_scan_status : 
[ 2905.064151] wlan0 Scan_results error (-22)
[ 2968.040075] ERROR @wl_notify_scan_status : 
[ 2968.040079] wlan0 Scan_results error (-22)
[ 3031.080041] ERROR @wl_notify_scan_status : 
[ 3031.080044] wlan0 Scan_results error (-22)

```

For right now, with the currently loaded driver, was never able to get it to work or see any networks. Has not been that long since I attempted to go with this driver.

---

### Post by chili555 on 2019-01-04
> For right now, with the currently loaded driver, was never able to get it to work or see any networks. And I doubt that you ever will:```

[   85.028054] wlan0 Scan_results error (-22)
[  118.056226] ERROR @wl_notify_scan_status : 
[  118.056233] wlan0 Scan_results error (-22)
[  143.624054] ERROR @wl_notify_scan_status : 
[  143.624058] wlan0 Scan_results error (-22)
[  197.028059] ERROR @wl_notify_scan_status : 
[  197.028062] wlan0 Scan_results error (-22)
[  260.040066] ERROR @wl_notify_scan_status : 
[  260.040069] wlan0 Scan_results error (-22)
```I suggest that you purge it and test b43 and firmware again.

---

### Post by mwei19 on 2019-01-04
> **chili555 said:**
> And I doubt that you ever will:```

[   85.028054] wlan0 Scan_results error (-22)
[  118.056226] ERROR @wl_notify_scan_status : 
[  118.056233] wlan0 Scan_results error (-22)
[  143.624054] ERROR @wl_notify_scan_status : 
[  143.624058] wlan0 Scan_results error (-22)
[  197.028059] ERROR @wl_notify_scan_status : 
[  197.028062] wlan0 Scan_results error (-22)
[  260.040066] ERROR @wl_notify_scan_status : 
[  260.040069] wlan0 Scan_results error (-22)
```I suggest that you purge it and test b43 and firmware again.


ok, will purge it and reinstall the b43 firmware now.

---

### Post by mwei19 on 2019-01-04
Ok, purge and the install of the firmware-b43-installer was completed, will be rebooting now but have to head home now. Will post results of the change once I am home!

---

### Post by mwei19 on 2019-01-04
Hello from home!
Guess what? The moment I booted up from home, WiFi is working as it should...makes me feel like I'm going crazy haha! 
Here's the information with the firmware-b43-installer:

$[COLOR=#000000][FONT=&amp]lsmod | grep -e wl -e b43
[/FONT][/COLOR]```
b43                   413696  0bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43

```[COLOR=#000000][FONT=&amp]

$dmesg | grep b43
[/FONT][/COLOR]```

[   17.394225] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   17.440203] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   17.443772] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   51.540236] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

```

[COLOR=#000000][FONT=&amp]
$dmesg | grep wl
[/FONT][/COLOR]```
[   51.337711] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[   51.997200] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.256865] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.654440] wlan0: authenticate with 2c:b0:5d:ab:07:e9
[   62.692407] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 1/3)
[   62.896075] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 2/3)
[   62.897711] wlan0: authenticated
[   62.900169] wlan0: associate with 2c:b0:5d:ab:07:e9 (try 1/3)
[   62.902796] wlan0: RX AssocResp from 2c:b0:5d:ab:07:e9 (capab=0x431 status=0 aid=5)
[   62.903259] wlan0: associated
[   63.009433] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by mwei19 on 2019-01-04
Reproduced the issue! Just rebooted a couple of times and now the WiFI won't detect anything again...
Following is the info that I pulled:

$lsmod | grep -e wl -e b43
```

b43                   413696  0
bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43

```

$dmesg | grep b43
```

[   32.834973] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   32.880574] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   32.882661] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   50.788219] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

```


$dmesg | grep wl
```

[   50.577022] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.276346] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.827581] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```


ran the following and then the WiFi networks showed back up but could not connect to anything:
```

$sudo modprobe -r b43
$sudo modprobe b43
$sudo service network-manager restart

```


$lsmod | grep -e wl -e b43 ***(after running above 3 commands)***
```

b43                   413696  0
bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43

```


$dmesg | grep b43 ***(after running above 3 commands)***
```

[   32.834973] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   32.880574] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   32.882661] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   50.788219] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  390.288062] b43-phy0 ERROR: DMA RX reset timed out
[  390.568276] b43-phy0 ERROR: DMA TX reset timed out
[  395.280048] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[  395.324752] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[  395.324781] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[  395.624236] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  414.480249] b43-phy0 ERROR: DMA RX reset timed out
[  414.756283] b43-phy0 ERROR: DMA TX reset timed out
[  415.396130] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  447.668152] b43-phy0 ERROR: DMA RX reset timed out
[  447.948040] b43-phy0 ERROR: DMA TX reset timed out
[  451.006856] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[  451.048130] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[  451.048158] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[  451.364179] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  451.705123] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  451.705136] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[  451.705143] b43-phy0: Controller RESET (DMA error) ...
[  452.036160] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  452.348203] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.
[  452.484437] b43-phy0: Controller restarted
[  459.196132] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  459.512367] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.

```


$dmesg | grep wl ***(after running above 3 commands)***
```

[   50.577022] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.276346] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.827581] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  395.423633] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  396.100672] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  396.164688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  415.191574] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  415.844570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  416.153018] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  451.155818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  452.484921] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  452.552954] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  458.994186] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  459.644425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  459.956584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  470.389526] wlan0: authenticate with 2c:b0:5d:ab:07:e9
[  470.428323] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 1/3)
[  470.632046] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 2/3)
[  470.633511] wlan0: authenticated
[  470.636310] wlan0: associate with 2c:b0:5d:ab:07:e9 (try 1/3)
[  470.639242] wlan0: RX AssocResp from 2c:b0:5d:ab:07:e9 (capab=0x431 status=0 aid=5)
[  470.639467] wlan0: associated
[  484.861369] wlan0: authenticate with 2c:b0:5d:ab:07:e9
[  484.904454] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 1/3)
[  485.108063] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 2/3)
[  485.312193] wlan0: send auth to 2c:b0:5d:ab:07:e9 (try 3/3)
[  485.516036] wlan0: authentication with 2c:b0:5d:ab:07:e9 timed out
[  521.004205] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by chili555 on 2019-01-04
> 
[  451.705123] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  451.705136] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[  451.705143] b43-phy0: Controller RESET (DMA error) ...


This seems like a hardware/BIOS problem. Is the BIOS fully updated? Is the BIOS set to defaults?

May we see the scan?```
sudo iwlist scan
```Please just show us your network and redact the MAC address like this:```
Cell 01 - Address: [COLOR="#FF0000"]xxxxxx[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b522d11e15
                    Extra: Last beacon: 680ms ago
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

---

### Post by mwei19 on 2019-01-04
> **chili555 said:**
> This seems like a hardware/BIOS problem. Is the BIOS fully updated? Is the BIOS set to defaults?

May we see the scan?```
sudo iwlist scan
```Please just show us your network and redact the MAC address like this:```
Cell 01 - Address: [COLOR=#FF0000]xxxxxx[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b522d11e15
                    Extra: Last beacon: 680ms ago
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

Gotcha, the BIOS should be set to default as I'm actually not sure on how to modify/update the BIOS on a Macbook. 

As for the scan, nothing is showing up for now and am currently connected via ethernet. 

$sudo iwlist scan
```

wlan0     No scan results


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

```

---

### Post by gsahli on 2019-01-06
It's not a happy thought, but I think you may have a hardware problem (intermittent).
I don't remember, does wifi work OK in Mac OS?
And, have you tried 18.04?

PS-Macs don't have a BIOS - they must have something like that, but there aren't any user settings.

---

### Post by chili555 on 2019-01-06
> t's not a happy thought, but I think you may have a hardware problem (intermittent).That's on my suspicion list, as well.

Please try:

```
sudo -i
echo "options b43 pio=1"  >  /etc/modprobe.d/b43.conf
exit
```Reboot and tell us if there is any improvement.

---

### Post by mwei19 on 2019-01-07
> **gsahli said:**
> It's not a happy thought, but I think you may have a hardware problem (intermittent).
I don't remember, does wifi work OK in Mac OS?
And, have you tried 18.04?

PS-Macs don't have a BIOS - they must have something like that, but there aren't any user settings.

Oh man...that doesn't sound good, I hope not...but it does seem that way though. I never had any issues with the WiFi when the macbook pro was still using MacOSX. 
The macbook pro is actually currently running on 18.04 right now. 

Gotcha, Apple wants to be special eh? lmao :(

---

### Post by mwei19 on 2019-01-07
> **chili555 said:**
> That's on my suspicion list, as well.

Please try:

```
sudo -i
echo "options b43 pio=1"  >  /etc/modprobe.d/b43.conf
exit
```Reboot and tell us if there is any improvement.

Just tried the code you provided, no difference thus far, no wireless networks are showing up. Ran the code once from home (yesterday) and at work (just now). The WiFi did work a couple of times, randomly, this past weekend though.

---

