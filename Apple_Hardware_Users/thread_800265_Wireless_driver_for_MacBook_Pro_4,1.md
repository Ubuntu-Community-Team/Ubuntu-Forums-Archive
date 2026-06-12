---
title: "Wireless driver for MacBook Pro 4,1?"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by hajk on 2008-05-19
The chipset is Broadcom 4328 802.11a/b/g/n (rev 5) and I expect that the right Windows driver for use in Ndiswrapper is somewhere inside the "broadcominstaller64.exe" or "broadcomxpinstaller.exe" files that I've lifted off the BootCamp CD. I already tried wine on these files, but no luck. How can I liberate a 64-bit driver from these files without having access to Windows?

---

### Post by seaward on 2008-05-19
Hey, I believe you can treat it as a file archive and just unzip the sucker.

[This old thread]("http://ubuntuforums.org/showthread.php?t=735846") suggests using Unrar on the file.

---

### Post by cyberdork33 on 2008-05-19
> **seaward said:**
> Hey, I believe you can treat it as a file archive and just unzip the sucker.
yep
you want the xp driver btw.

---

### Post by hajk on 2008-05-20
OK, found it, the same pair of bcmwl5.{inf,sys} files that are listed in other threads. Installed into ndiswrapper, shows up as only driver with "ndiswrapper -l" command,```

bcmwl5 : driver installed
        device (14E4:4328) present
```
Now the differences from previous threads: lsmod doesn't show ohci_hcd and ssb modules, so there won't be any problems with order of loading the ndiswrapper module, I take it. After modprobing ndiswrapper, the "iwconfig" command shows the wlan0 interface present, the "iwlist scan" command shows a whole bunch of wireless interfaces among which my own -- an Airport Extreme Base Station set to WPA/WPA2 Personal security. So far, so good.

After I select my network in network-manager a window pops up and asks for the WPA or WPA2 passphrase, which I provide, then keeps spinning and periodically asking for my passphrase again. It never connects! OK, network-manager has never worked well for me, so out with it and manually edit /etc/network/interfaces```

auto wlan0
iface wlan0 inet dhcp
   wpa-ssid HAJKNET
   wpa-psk "xxxxxxxxxx"
   wpa-driver wext
```
then "sudo ifup wlan0" also spins forever, never getting a DHCP offer.

Strange..., just the other day I installed Hardy on my old original MacBook  and it had no problems connecting (with madwifi) to the same network with network-manager. What am I overlooking, I wonder... the old MacBook had 32-bit Hardy, the new MBP has 64-bit Hardy, is that it? Has anyone got the Broadcom 4328 rev 05 to work on 64-bit Hardy?

---

### Post by hajk on 2008-05-20
A bit of progress, if you can call it that. I've reconfigured my wireless AP (an Airport Extreme Base Station) to 802.11n (2.4GHz) only, instead of the 802.11n (b/g compatible). The security is now WPA2 Personal (AES-CCMP). I've also re-enabled nm-applet and cleaned out /etc/network/interfaces.

The nm-applet sees my network, the icon starts spinning and a window pops up asking for WPA2 Personal passphrase, and now the nm-applet shows connected, except it alternates between full-colour (100%) and no colour (0%), and sometimes in between. Yet, it keeps on asking for my passphrase, time and again, and ifconfig shows no connection....

I've now wasted half a day on this, back to running Ubuntu in VMware Fusion for now...:confused::mad:

---

### Post by seaward on 2008-05-20
Not got much to add except to say have you tried it without the WPA authentication switched on, just for the sake of testing?

I've read a few reports of WPA being a bit screwed up on 64-bit Ubuntu.

Might be worth checking, but doesn't really represent a valid solution.

---

### Post by hajk on 2008-05-20
I've tried it without any WPA or WEP (but I did put a MAC address filter in place), and now I get a connection, after trying a few times. Yeah!

But, unfortunately, the connection speed is very low, unusable really. The iwconfig command shows 11 Mbps, that's 802.11b territory, while this Airport chip is draft-n (and so is the router). 

Something must have happened in Broadcom 4328 rev 05 that means a regression from all those good reports from people with rev 03 chips. Oh well, I have VMware Fusion to fall back on, but I'll keep an eye out for a fix since a VM doesn't allow those fancy Compiz effects that the Nvidia 8600GT hardware does.

---

### Post by cyberdork33 on 2008-05-20
have you tried wicd?

---

### Post by hajk on 2008-05-20
> **cyberdork33 said:**
> have you tried wicd?
No, but I have a feeling that rev 05 is the problem. Another problem that has cropped up is that pommed doesn't work on the MBP 4,1. I've had enough for now, at least I have the VMware session. I may also try to see how Debian testing behaves...

Thanks for now, I'll be back some time soon (I hope).

---

### Post by cyberdork33 on 2008-05-20
> **hajk said:**
> No, but I have a feeling that rev 05 is the problem. Another problem that has cropped up is that pommed doesn't work on the MBP 4,1. I've had enough for now, at least I have the VMware session. I may also try to see how Debian testing behaves...

Thanks for now, I'll be back some time soon (I hope).

A lot of people have been using rev05...

Looks like pommed supports your Macbook Pro as well unless there is a bug:
[http://svn.debian.org/wsvn/pommed/trunk/README?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/pommed/trunk/README?op=file&rev=0&sc=0)

---

### Post by hajk on 2008-05-23
Well, the saga continues... I've gotten pommed to work, but only after installing the next version from ppa.launchpad. The applesmc module gives an unending stream of```

applesmc: wait status failed: c != 8
```
messages in dmesg, so I rmmod-ded it and I'll have to do without keyboard backlighting.

I have also installed wicd (the stable version 1.4.2) and gotten rid of network-manager in the process. Wireless still doesn't connect to my WPA-secured AP, although it will connect to my neighbour's unsecured AP. It makes no difference whether I use WPA, WPA2, with TKIP or AES. At the same time, my old MacBook (also with Hardy) will connect happily to the same AP (an Apple Airport Extreme Base Station).

Is there anyone around with an MBP 4,1 (with the Broadcomm 4328 rev 05 chip), running 64-bit generic Hardy, who can connect to a WPA-secured network? If so, I would like to hear details on the setup, please.

---

### Post by cyberdork33 on 2008-05-23
> **hajk said:**
> Well, the saga continues... I've gotten pommed to work, but only after installing the next version from ppa.launchpad. The applesmc module gives an unending stream of```

applesmc: wait status failed: c != 8
```messages in dmesg, so I rmmod-ded it and I'll have to do without keyboard backlighting.
From what I understood, those messages are OK. It was a debug message (or something like that) and didn't get commented out in the code or something, but doesn't effect operation.

> I have also installed wicd (the stable version 1.4.2) and gotten rid of network-manager in the process. Wireless still doesn't connect to my WPA-secured AP, although it will connect to my neighbour's unsecured AP. It makes no difference whether I use WPA, WPA2, with TKIP or AES. At the same time, my old MacBook (also with Hardy) will connect happily to the same AP (an Apple Airport Extreme Base Station).

Is there anyone around with an MBP 4,1 (with the Broadcomm 4328 rev 05 chip), running 64-bit generic Hardy, who can connect to a WPA-secured network? If so, I would like to hear details on the setup, please.

What do you have the wifi settings set to? Some people have trouble if it is set to b+g compatible instead of just g compatbile or something like that. I have a Linksys router, so I don't know the exact options in the AEB

---

### Post by hajk on 2008-05-23
@applesmc: not sure whether those messages are harmless; even with it loaded the keyboard backlighting doesn't work. BTW, those messages start once /etc/init.d/pommed is restarted, not when applesmc is modprobed with pommed already running.

@wireless: I've tried both 802.11n (2.4GHz only) and 802.11n (b/g compatible 2.4GHz), it makes no difference. Obviously I'm using the b/g compatible right now, as I'm typing this on my MacBook 1,1.

---

### Post by cyberdork33 on 2008-05-23
> **hajk said:**
> @applesmc: not sure whether those messages are harmless; even with it loaded the keyboard backlighting doesn't work. BTW, those messages start once /etc/init.d/pommed is restarted, not when applesmc is modprobed with pommed already running.Well, you can go check the mactel-linux mailing list archives, but I am pretty sure they are harmless. 

> **hajk said:**
>  @wireless: I've tried both 802.11n (2.4GHz only) and 802.11n (b/g compatible 2.4GHz), it makes no difference. Obviously I'm using the b/g compatible right now, as I'm typing this on my MacBook 1,1.There was a thread recently where someone discussed changing something like that, and it fixed it. Maybe not for you though. Sry.

---

### Post by vanakush on 2008-05-23
[http://ubuntuforums.org/showthread.php?t=800618]("http://ubuntuforums.org/showthread.php?t=800618")

i use wpa2 and whenever i go to System--->Administration--->Network and type my Network password it gets double and Password type automatically shifts to WPA Personal from WPA2 Personal, i don't know what is the problem .Is there any way to enter WPA2 psk using command line.

---

### Post by hajk on 2008-05-23
> **vanakush said:**
> [http://ubuntuforums.org/showthread.php?t=800618]("http://ubuntuforums.org/showthread.php?t=800618")

i use wpa2 and whenever i go to System--->Administration--->Network and type my Network password it gets double and Password type automatically shifts to WPA Personal from WPA2 Personal, i don't know what is the problem .Is there any way to enter WPA2 psk using command line.Yes, check out the wpa_supplicant man-pages and documentation (examples). I've tried that too, but couldn't make things work. :(

---

### Post by hajk on 2008-05-28
> **cyberdork33 said:**
> A lot of people have been using rev05...This I find puzzling, as I have trolled the various forums and wikis for days without finding a single instance of an MBP 4,1 user succeeding in getting a connection to a WPA/WPA2 wireless AP. Yes, it will connect to an open AP, so the problem lies in the current version of wpasupplicant, not ndiswrapper or any of the network-managers. 

This is confirmed by using wpasupplicant directly, with config file /etc/wpa_supplicant/wpa_supplicant.conf```

ctrl_interface=/var/run/wpa_supplicant
network={
          ssid="HAJKNET"
          key_mgmt=WPA-PSK
          psk="MyPassPhrase"
}
```(No need for a more elaborate config file, as wpa_supplicant correctly picks up all necessary settings of the wireless AP. That directory in /var/run must be made first.) Then do```

$ sudo ifconfig wlan0 up
$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -d > tmp
```
and stop it with Ctrl-C after some time. Then study the output in tmp: it appears that everything associates fine until the 4-way handshaking phase, when it somehow proceeds to reassociate, etc, until things time out.

I've also tried Debian unstable with the 2.6.25 kernel... same problem.

P.S. The 2.6.25 kernel has solved the problem with usbhid, so the special fn-key works without the quirks work-around. The applesmc module still gives those never-ending error messages.

PP.SS. I'm abandoning my attempts at installing GNU/Linux directly to the hardware of the MBP 4,1 until I see reports of wpasupplicant having been fixed. I'll try and see whether a bug report (in Ubuntu Launchpad or Debian BTS) is indicated.

---

### Post by jc71229 on 2008-05-28
I have exactly the same problems. On a brand new MBP wlan0 is detected but I don't get an IP from my dhcp server.

Interessting is that I avahi feels responsable to assign an IP:

wlan0     Link encap:Ethernet  Hardware Adresse 00:1e:c2:c4:68:46
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Speicher:97300000-97304000

wlan0:avahi Link encap:Ethernet  Hardware Adresse 00:1e:c2:c4:68:46
          inet Adresse:169.254.6.237  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          Interrupt:16 Speicher:97300000-97304000

Any ideas how to solve this?
Thanks

---

### Post by cyberdork33 on 2008-05-28
> **hajk said:**
> I have trolled the various forums and wikis for days without finding a single instance of an MBP 4,1 user succeeding in getting a connection to a WPA/WPA2 wireless AP. Yes, it will connect to an open AP, so the problem lies in the current version of wpasupplicant, not ndiswrapper or any of the network-managers.I didn't think that n-m used wpa-supplicant!

What encryption type are you using though? AES? TKIP? That may also the issue. I can see problems with WPA2... I have always had issues with that, but WPA has worked without much issue for me for years. (I don't have one of the rev5 cards though...)

---

### Post by hajk on 2008-05-28
We've been through this before... I've tried just about any combination I could think of: WPA with TKIP, WPA2 with TKIP and CCMP, WPA/WPA2 with TKIP and CCMP, etc. The output of the "wpa_supplicant" command shows that everything is properly detected, except at the 4-way handshake stage things time out. I should say, there is a 10 second time-out limit, and I have not been able to ascertain where that is set (in wpa_supplicant? in the router?). 

That same 10-second time-out is also active in network-manager, seeing that it asks for the passphrase every 10 seconds or so; wicd just sits there spinning its wheels. Would the Apple Extreme Base Station router be the problem?

BTW, has anyone seen a report of WPA/WPA2 working on the MBP 4,1 with the ndiswrapper(broadcom 4328 rev 05) setup?

---

### Post by cyberdork33 on 2008-05-28
> **hajk said:**
> Would the Apple Extreme Base Station router be the problem?I notice that many a problem with WiFi are trying to connect to an AEB. That very well may be the issue.

---

### Post by hajk on 2008-05-28
Yes, that's what I've been thinking too. So, I borrowed a Linksys WAG160N asdls-modem/router and configured it both for WPA and WPA2 (separately) and tried to connect to it. Unfortunately, same result: network-manager asks for WPA PassPhrase every 10 seconds or so, but never connects. Well, I'm glad I had the foresight to install VMware Fusion on the MBP; it runs both Hardy and Lenny flawlessly, and fast too (what with 4GB RAM installed). I'll be back trying an install of Ubuntu and/or Debian on the hardware sometime, but not too soon I guess...

---

### Post by theghostbelow on 2008-05-29
I have this same problem in 32bit although I did get wireless to work briefly and then it stopped again.

---

### Post by theghostbelow on 2008-05-29
Make sure that you have gone to the software sources and checked the third party boxes and the two boxes under update. I tried that and if finally worked :) using Wpa/wpa2.

---

### Post by jc71229 on 2008-05-30
Maybe the new ndiswrapper 1.53 is the solution?

Form the Change-Log the last point might solve the problem?

* Implemented va_list conversion for x86_64, which fixes oops in  
  vsprintf() and vsnprintf().
* Fixed oops on unload if using our workqueue implementation with SMP enabled.
* Don't change the actual thread priority, just pretend it was changed.
* Implemented format string conversion for x86_64, so that Windows long  
  is mapped to Linux int.
* Fixed most sparse warnings.
* Simplified code and build system to remove already broken support for  
  Linux versions prior to 2.6.16.
* Added .size and .type for all functions in win2lin_stubs.S to improve  
  backtrace on x86_64.
* Fixed rx key authentication sequence number conversion from Windows to
  Linux so WPA authentication doesn't sometimes go into re-key auth loop.

Anyone tried that?
Best regards
Jens

---

### Post by hajk on 2008-05-30
Yes, that may well be solution to the problem that I described earlier. Good show to notice that!

I won't try this out myself anytime soon, though, since I've now switched my wireless setup (for other reasons) exclusively to the 5GHz band. Unfortunately, the current Ndiswrapper/Broadcom 4328 (rev 05) combination does not scan that band...

---

### Post by hajk on 2008-06-03
Well, I've now also tried Ndiswrapper 1.53, downloaded from SourceForge and compiled/installed as per the instructions. I'm sad to inform that there was no difference: it did not solve the problem with WPA/WPA2 security discussed earlier in this thread.

---

### Post by jc71229 on 2008-06-03
Yes, I can confirm this. I have compiled the new ndiswrapper too, but the problem persists.
This is a pity. Such a nice machine and no wireless LAN (with WPA). I have to use OS X after all :-).

**hajk**: Does ifconfig shows a wlan0:avahi entry like mine?

wlan0:avahi Link encap:Ethernet Hardware Adresse 00:1e:c2:c4:68:46
inet Adresse:169.254.6.237 Bcast:169.254.255.255 Maske:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metrik:1
Interrupt:16 Speicher:97300000-97304000

I was not able to inhibit the responsability of avahi (zeroconf) for my wlan interface.

Thanks

---

### Post by hajk on 2008-06-03
Yes, it did. I have switched to Debian testing (Lenny) in the meantime, with a 2.6.25 kernel, and now it does not show  that extra avahi interface. 

I have configured my AP now for 5GHz 802.11n, but it is not visible in network-manager or with "iwlist scan", as these look in the 2.4GHz band only. 

I'm afraid that resolution of the WPA/WPA2 and 5GHz band problems must await further development of Ndiswrapper. You should look into using VMware Fusion (the beta 2.0 version) in order to use Ubuntu Hardy on your new MBP -- it runs very well on mine (money well spent).

---

### Post by cyberdork33 on 2008-06-03
> **hajk said:**
> Yes, it did. I have switched to Debian testing (Lenny) in the meantime, with a 2.6.25 kernel, and now it does not show  that extra avahi interface. 

I have configured my AP now for 5GHz 802.11n, but it is not visible in network-manager or with "iwlist scan", as these look in the 2.4GHz band only. 

I'm afraid that resolution of the WPA/WPA2 and 5GHz band problems must await further development of Ndiswrapper. You should look into using VMware Fusion (the beta 2.0 version) in order to use Ubuntu Hardy on your new MBP -- it runs very well on mine (money well spent).Yea, ndiswrapper and the other broadcom drivers do not support 802.11n yet.

---

### Post by hajk on 2008-06-03
> **cyberdork33 said:**
> Yea, ndiswrapper and the other broadcom drivers do not support 802.11n yet.
Not quite, since 802.11n is just dual 802.11g. So, there's no problem with the 2.4GHz band: iwconfig will report 802.11n as 802.11g; and, as discussed earlier, ndiswrapper + the XP bcmwl5(64) driver works fine without WPA/WPA2 in that case, even with the rev 05 version of 4328. But 802.11n also has the added 5GHz band, which (clearly) is supported by bcmwl5(64) but not yet by ndiswrapper.

---

### Post by cyberdork33 on 2008-06-03
> **hajk said:**
> Not quite, since 802.11n is just dual 802.11g. So, there's no problem with the 2.4GHz band: iwconfig will report 802.11n as 802.11g; and, as discussed earlier, ndiswrapper + the XP bcmwl5(64) driver works fine without WPA/WPA2 in that case, even with the rev 05 version of 4328. But 802.11n also has the added 5GHz band, which (clearly) is supported by bcmwl5(64) but not yet by ndiswrapper.
n is backwards compatible with g, so it is recognized as g because full n is not supported.

---

### Post by a1234 on 2008-06-03
Just want to let you folks know that penryn mbp can have wifi access. Please look at this post.

[http://ubuntuforums.org/showthread.php?t=816161](http://ubuntuforums.org/showthread.php?t=816161)

---

### Post by hajk on 2008-06-04
Yes, I had seen that post of yours. The fact that the Broadcom 4328 rev 05 wireless chip on the MBP 4,1 can be made to work without security isn't new, it has already been mentioned in several threads including this one. The problem is to get it working with WPA or WPA2 security, without which it is of no use to many users like myself. This may take a while for the ndiswrapper devs to sort out, but patience is a virtue, or so they say...

---

### Post by a1234 on 2008-06-04
> **hajk said:**
> Yes, I had seen that post of yours. The fact that the Broadcom 4328 rev 05 wireless chip on the MBP 4,1 can be made to work without security isn't new, it has already been mentioned in several threads including this one. The problem is to get it working with WPA or WPA2 security, without which it is of no use to many users like myself. This may take a while for the ndiswrapper devs to sort out, but patience is a virtue, or so they say...
 
Well I am sorry for bothering you with OLD NEWS. If any consolation I used a "closed network setting" for some ? measure of of security.

---

### Post by a1234 on 2008-06-04
Just reconfig my airport base station specifically with WAP2 AES/cCm. And then signed selecting the AES-- instead of AUTO (default) option. Now I have encrypted wifi.

---

### Post by Andreas T on 2008-06-06
> **a1234 said:**
> Just reconfig my airport base station specifically with WAP2 AES/cCm. And then signed selecting the AES-- instead of AUTO (default) option. Now I have encrypted wifi.


Confirmed -
I have WPA2/WPA on my airport extreme and chose WPA with tkip instead of automatic when connecting. Works!

---

### Post by hajk on 2008-06-07
Well great, but alas no solution to my problem... User a1234 refers in his OP to a driver obtained from vanakush as a bcmwl5.zip file (cyberdork questioned the source of that file), which contained a 32-bit version of the driver. My problem is with a 64-bit implementation. Besides, I have indicated earlier in this thread that I have already checked the various strategies that now turn out to be successful for a1234 and Andreas T; they were not successful in my 64-bit case. I state this merely as a fact, no negative reflection on a1234 and Andreas T intended.

So, I would still be interested in hearing about a successful application of bcmwl5.inf/bcmwl564.sys together with WPA/WPA2 Personal security on a 64-bit installation of Hardy on the 4,1 MBP.

---

### Post by Salohcin on 2008-06-08
I'm running a macbook pro 4,1 (Feb 2008 ) release.  I installed ndiswrapper and the broadcom drivers per the wiki instructions onto a 64bit version of Heron (8.04) and am able to connect to the 802.11g network at uni using WPA.
Haven't successfully connected with WPA2, but intend to give it a try over the break.

---

### Post by hajk on 2008-06-08
Thanks for sharing your experience. May I ask whether you did anything special to configure wireless? Did you use network-manager? Did it ask for your WPA passphrase more than once?

---

### Post by Salohcin on 2008-06-09
Yes, i used the network manager applet that sits on the top panel in your default installation of ubuntu.  With reference to how many times i have to enter the pass phrase, its random.  Sometimes it connects right off, other times it will ask me for it several times before it connects.

I've found that picking up a signal at longer ranges isn't as good as when i'm booted into the macosx side of things, and the signal strength varies a lot unless i'm within a room range of the ap.

---

### Post by lloeki on 2008-07-08
I recently changed router:

- I was previously connecting happily in wpa on a wrt54g v5 loaded with ddwrt 24 micro.
- I am now failing to connect past the wpa supplicant '4 way handshake' on a netgear wnr834b v2 with ddwrt v24 std. wpa diagnosis is easy, just start 'sudo wpa_cli' and watch the messages, and/or type 'status' command.

workaround: since the routers os is exactly the same, and I could connect successfully to the wrt54g, I degraded settings on the wnr834b to match the wrt54g (namely disabling BGN-mixed mode and forcing BG-mixed mode). also I forced wpasup to use wpa-psk only, and success! okay I don't get the N's 320Mb/s but at least I have the G's 54Mb/s with WPA encryption.

btw that's with archlinux 64bit but I thought this might be useful to some here.

---

### Post by cyberdork33 on 2008-07-08
That sounds about right. I have the same problem with several machines on my home network. Have to force it down to BG.

---

### Post by kosumi68 on 2008-07-08
I recently brought an apple extreme basestation home to my ubuntu macbook air, and experienced the same problem; I could not make it work. I went back to the store and had it replaced by a netgear WPN824v2, with which I have had no problems.

---

### Post by hajk on 2008-07-09
Well, I've tried a few other 802.11b/g modem/routers too (SpeedTouch 585, SpeedTouch 780) but still no dice. Eventually the WPA/WPA2 problem will be sorted out, I'm sure. In the meantime I've switched to a solution of sorts that doesn't require any Linux wireless drivers or ndiswrapper: a Linksys WET54G wireless bridge. It's a bit bulky, but it does fit in the outside pockets of the Incase sleeve for my 15" 4,1 MBP. For those interested, refer to my setup Howto in [http://forums.debian.net/viewtopic.php?t=28456](http://forums.debian.net/viewtopic.php?t=28456).

---

### Post by lloeki on 2008-07-10
I now have it working in N mode, although the router must be set to accept B mode:
- 'BG Mixed' mode works, G-only fails
- 'BGN Mixed' mode works, N-only fails

```
wlan0     IEEE 802.11g  ESSID:"Day5"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:2A:61:F2:90   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:127  Invalid misc:194143   Missed beacon:0

```

what's more, it seems that some auth combinations will fail. here's my wpa_supplicant.conf, forcing some settings so I can have the widest ones (WPA/WPA2 Personal+TKIP/AES) on the router. refer to wpa_supplicant documentation/sample config for what things mean.

```
## global configuration (shared by all network blocks)
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
#fast_reauth=1

## network configs

network={
    ssid="Day5"
    proto=RSN # WPA works too
    key_mgmt=WPA-PSK # what else?
    pairwise=CCMP # TKIP auths but then MAC-level link is crap
    group=TKIP # CCMP fails to auth, WEP104/WEP40 untested
    psk="MYSECRETPASSPHRASE"
    priority=5
}

```

for the record, I'm using following ArchLinux packages versions:
```
$ pacman -Q ndiswrapper wpa_supplicant wireless_tools dhcpcd
ndiswrapper 1.53-1
wpa_supplicant 0.5.10-1
wireless_tools 29-2
dhcpcd 3.2.1-1

```

---

### Post by lloeki on 2008-07-10
some people are encountering similar issue on ddwrt forums: [http://www.dd-wrt.com/phpBB2/viewtopic.php?p=191268#191268](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=191268#191268)

---

