---
title: "WPA compatability"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by witham on 2007-07-01
I am completely new to Ubuntu and I have downloaded and used the live CD, I really want to migrate away from windows on both moral and security grounds. My problem is that whilst 7.04 says it supports WPA encrytion I cannot make the live cd connect?
I have searched the documentation and network manager is installed and working but when I go in it only shows WEP encrytion. I really don't want to lower the security on my wireless network do you have to install onto the hard drve o configure this?

---

### Post by abn91c on 2007-07-01
not to point out the obvious but did you look for a drop menu under WEP, WPA personal should be there as well

---

### Post by witham on 2007-07-01
yes I did it isn't there the only ones listed are WEP

---

### Post by ugm6hr on 2007-07-01
From memory, Network Manager doesn't give you an option for encryption - it auto-detects the router's encryption, and only offers potentially correct options (e.g. for WEP - 64-bit, 128-bit etc.)

Are you using the Network-manager applet (top right corner) to bring up a list of available networks (i.e. on roaming mode enabled)?

If you don't know what I'm talking about - post a screenshot of the wireless configuration options, and someone will explain.

Also - to see if your wifi will work easily, enter the following in Terminal:
```
lspci
ifconfig
iwconfig
```

And post the results here too (you are looking for Ethernet/Network controller details).

---

### Post by witham on 2007-07-01
Thanks very much for your reply

Here goes, I hope this means more to you than me???


ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off 
          Link Quality=48/100  Signal level=27/100  Noise level=0/100 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:00:39:AE:DE:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

eth0:avah Link encap:Ethernet  HWaddr 00:00:39:AE:DE:95  
          inet addr:169.254.8.222  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2764 (2.6 KiB)  TX bytes:2764 (2.6 KiB) 

wlan0     Link encap:Ethernet  HWaddr 00:0D:0B:0C:17:1E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:11 

wlan0:ava Link encap:Ethernet  HWaddr 00:0D:0B:0C:17:1E  
          inet addr:169.254.1.58  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:11 

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83) 
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33) 
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface 
ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off 
          Link Quality=51/100  Signal level=32/100  Noise level=0/100 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ugm6hr on 2007-07-01
The important bits:
Chipset: 02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface 
Interface: wlan0

From memory, the ACX Linux driver was a bit hit and miss (about a year ago) - not sure if that's still the case.  It certainly never did WPA.

I think ndiswrapper may allow WPA, but I'm not 100% sure.  Unfortunately, you have to install to HD to try.

Best to search for ACX1 in these forums to see whether anyone has a solution.  The ndiswrapper wiki is useful too.

---

### Post by witham on 2007-07-01
Thanks very much I will

---

### Post by sheck on 2007-07-03
look in Synaptic and make sure wpa_supplicant is installed, otherwise you cannot use WPA/WPA2

---

### Post by Paul_world10 on 2007-07-03
Is this bad to consider the driver not being installed for chipset. Also WPA not good in Feisty in GUI. Gui will never work on Feisty in WPA but a programmer could make.

---

### Post by Paul_world10 on 2007-07-03
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated

---

### Post by Paul_world10 on 2007-07-03
Your NIC isnt showing up on lspci only the built in lan card is.

---

### Post by Paul_world10 on 2007-07-03
OH it is darn 

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)

---

### Post by houms on 2007-07-04
From what I understand you just need to configure wpa_supplicant to handle the encryption... And in Networkmanager, go to Connect to other wireless networks, under this option you can choose wpa/wpa2, but it will not work unless you have configured your wpa_supplicant FIRST. This was from my experience with a inspiron 8600 with internal intel 2100 b card, and fiesty.

---

### Post by witham on 2007-07-05
Thank you all very much I will try all the suggestions

---

### Post by witham on 2007-07-06
Could anyone please tell me how I configure the WPA Supplicant?

---

### Post by houms on 2007-07-06
sure here is how mine looks..... feel free to copy....couple of things, RSN=wpa2 and CCMP=AES encryption.... if anything else doesn't make sense let me know. Insert your ssid and hex key below... to get your hexkey just
sudo wpa_passphrase 'yournetworkname' 'yourpassphrase' (leave the single quotes in...
the output will have a line like psk=
this is yourhexkey. just copy and paste. Let me know how it goes. good luck  

# WPA 2
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
ssid="yournetworkname"(leave the quotes)
scan_ssid=1
proto=RSN     
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk=yourhexkey
}

---

### Post by ugm6hr on 2007-07-06
> **witham said:**
> Could anyone please tell me how I configure the WPA Supplicant?
Before you go too far...  I just searched again, and these suggest ACX111 Linux driver doesn't do WPA:
[http://acx100.sourceforge.net/wiki/ACX](http://acx100.sourceforge.net/wiki/ACX)
[http://ubuntuforums.org/showthread.php?t=385979](http://ubuntuforums.org/showthread.php?t=385979)

If you want WPA, I think ndiswrapper is your only choice for ACX chipsets.

---

### Post by houms on 2007-07-06
yeah but if I'm not mistaken, thats why you must configure /etc/wpa_supplicant.conf, cause just like my ipw2100 driver, it doesn't support wpa natively so it needs the supplicant as a back-end to handle encryption....

---

### Post by witham on 2007-07-07
Thanks for all your help, I have got my psk hexkey which worked great but when I copy and paste the code you detailed putting in my hexkey and ssid nothing happens?
Am I doing something wrong?

# WPA 2
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
ssid="belkin54g"
scan_ssid=1
proto=RSN 
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk=I put the key in here and nothing happened
}

---

### Post by houms on 2007-07-07
now go network manager and look at the list of wireless networks listed... is yours there? if so try and connect to it.... You'll know if its working when Keyring Manager pops up and asks for a default password for the Keyring, the funny thing is sometimes key manager will not pop up if fother windows are open, so MINMIZE all your open windows,....If it fails to connect the first time try it 3 more times.. and let me know what happened..
If you don't see your network listed there, go to 'connect to other wireless networks' option and fill in the appropriate fields that apply to your network... again same as above once you put this info in, make sure to minimize any window and wait for keyring manager to pop up.....Let me know how it goes....

oh and make sure your /etc/network/interfaces file has not been modified, make sure its the default setup....
I'm here if ya need help...Holla

---

### Post by witham on 2007-07-08
Thanks very much for your patience I have done that and tried to connect but WPA is still not there. Ubuntu knows that the wireless connection is there because it s listed and the keyring manager comes up but only lists WEP encrytion?

---

### Post by nijinsky on 2007-07-25
Okay I'm not trolling here.

After finishing my recent contract I don't need my laptop for crucial stuff so I'm going to play with Ubuntu and probably write an app to configure WPA.

I see you are desperate to move from windows. Well try [www.xandros.com](www.xandros.com) it is a linux that will give you WPA out of the box. Indeed it works with my PCMCIA card when windows doesn't.

I tried ubuntu in the past but was put off by lack of WPA (I never got it to work). Although I'm advocating another linux it is simply so you can see how well linux can work.

Then check back here for a free linux (xandros costs money, I think it is worth it but I'm leaving because of the MS agreement).

I intend to install Ubuntu and Puppy as a dualboot.

Dont loose heart, you will ge there in the end. Since using linux, I have to go to windows at work and constantly swear at the desktop when on app brings down the system.
Cheers
Bob

---

