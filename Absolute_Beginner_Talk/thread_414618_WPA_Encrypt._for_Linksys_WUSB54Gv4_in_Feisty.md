---
title: "WPA Encrypt. for Linksys WUSB54Gv4 in Feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Supercross on 2007-04-20
I just booted up into the LiveCD of Feisty and was delighted to see that my wireless card, a Linksys WUSB54Gv4 appeared to be working out of the box, as it detected my wireless network.  So I thought, no need to use ndiswrapper here, but for some reason whenever I click on my SSID using network manager and it asks for the key it will not let me select WPA encryption, it only allows WEP or none.  So I searched a bit on here and found some info saying that RT2xxx driver wifi cards do not support WPA through network manager.  The WUSB54Gv4 is a ralink driver card correct?  Is my only resort here to use wpa_supplicant?  Last, I had to use ndiswrapper in Edgy but in Feisty I don't do I, as it appears it IS working, just without WPA support.

---

### Post by qrprat77 on 2007-04-20
Well, mine don't work at all right now, set everything up exactly as it is set up in Edgy, and nope, he don't work at all. I cant even get a green light to come on on the device!

---

### Post by DapperMe17 on 2007-04-20
In order to use WPA encryption, you'll have to simply blacklist the built-in driver RT2570. Then, you'll have to ue the Windows driver, along with NDISwrapper, in order to get your WPA setup.

If you look in the "How To's", you'll find an easy, step-by-step guide from Wieman01. 

The WUSB54G v4 works flawlessly with WPA after folloing the guide!

---

### Post by Supercross on 2007-04-20
> **DapperMe17 said:**
> In order to use WPA encryption, you'll have to simply blacklist the built-in driver RT2570. Then, you'll have to ue the Windows driver, along with NDISwrapper, in order to get your WPA setup.

If you look in the "How To's", you'll find an easy, step-by-step guide from Wieman01. 

The WUSB54G v4 works flawlessly with WPA after folloing the guide!
Yeah, I was able to get it working fine in Edgy, but in Feisty just follow the same steps?

It states that using ndiswrapper and wpa_supplicant will break network manager or something to that extent...is that true?

---

### Post by wieman01 on 2007-04-20
> **Supercross said:**
> Yeah, I was able to get it working fine in Edgy, but in Feisty just follow the same steps?

It states that using ndiswrapper and wpa_supplicant will break network manager or something to that extent...is that true?
My WUSB54G V4 worked fine with the beta version of Feisty. Don't use the standard networking tool, but Network-Manager. I think there are two apps available, at least that's the case in Kubuntu.

You don't have to install any extra packages at all, nor do you have to blacklist the RT2570 driver as far as I can tell. All included.

---

### Post by qrprat77 on 2007-04-20
> **wieman01 said:**
> My WUSB54G V4 worked fine with the beta version of Feisty. Don't use the standard networking tool, but Network-Manager. I think there are two apps available, at least that's the case in Kubuntu.

You don't have to install any extra packages at all, nor do you have to blacklist the RT2570 driver as far as I can tell. All included.

What about the network interfaces file?
When I upgraded to Feisty, it modified my blacklist, and as far as I could tell, that was the only difference between the way Feisty and Edgy set up my wireless.  When I don't blacklist the driver, it gives me the network-manager applet in the upper right hand corner, and it reads my network only to have no WPA option for security.  When I disable the WPA security, the router sees the device, and the device sees and attempts to connect to the network, but it does not succeed.

When I attempt to use the same setup as in Edgy (Blacklisted driver being the main difference), the little green light on the WUSB54Gv4 doesn't come on.  when I type ndiswrapper -l it tells me that it detects the hardware and has the driver installed.

---

### Post by qrprat77 on 2007-04-29
Anyone having any luck getting WPA to work on the WUSB54Gv4 in Feisty yet??

---

### Post by wieman01 on 2007-04-30
> **qrprat77 said:**
> Anyone having any luck getting WPA to work on the WUSB54Gv4 in Feisty yet??
Using "ndiswrapper" or the Linux driver for Ralink?

---

### Post by qrprat77 on 2007-04-30
> **wieman01 said:**
> Using "ndiswrapper" or the Linux driver for Ralink?

I havent' been able to get either to work.  If I use the native driver, it sees my network, but does not allow to connect using WPA.  If I try ndiswrapper, I can't seem to get it to work using the same interface files as I did under Edgy...
originally I was an upgraded install.  now I m a clean install.  This has been a learning experience, but I would like to do a little more using than learning right now when it comes to wireless dongles.  :lolflag:

---

### Post by wieman01 on 2007-04-30
> **qrprat77 said:**
> I havent' been able to get either to work.  If I use the native driver, it sees my network, but does not allow to connect using WPA.  If I try ndiswrapper, I can't seem to get it to work using the same interface files as I did under Edgy...
originally I was an upgraded install.  now I m a clean install.  This has been a learning experience, but I would like to do a little more using than learning right now when it comes to wireless dongles.  :lolflag:
It is just that Ralink does not support WPA the way other drivers do. I have a WUSB54G V4 as well, and I could WPA working only by making use of "ndiswrapper". Plus Serialmonkey's RT2570 only supports WPA-TKIP and not WPA-AES (= WPA2). So my recommendation is that you use "ndiswrapper" and blacklist the RT2570 driver, unless you want to bother with command line. WPA support by the means of NetworkManager is out of the question under the circumstances... :-(

---

### Post by Supercross on 2007-05-01
I actually got my WUSB54G working by removing Network Manager, blacklist the RT2570 driver, install ndiswrapper and use the rt2500usb driver from the Linksys cd, and use wpa_supplicant to connect via WPA.  After setting the ndis modules to load upon boot, and editing my network interfaces config file, the connection is ready to go everytime I boot up, never had a problem.

---

### Post by qrprat77 on 2007-05-01
Ok, my last question b4 pulling the trigger on uninstalling network manager.
If this doensn't work, will I still be able to connect to the internet via my ethernet connection?

---

### Post by wieman01 on 2007-05-01
> **qrprat77 said:**
> Ok, my last question b4 pulling the trigger on uninstalling network manager.
If this doensn't work, will I still be able to connect to the internet via my ethernet connection?
Sure as sugar. :-)

---

### Post by Supercross on 2007-05-01
> **qrprat77 said:**
> Ok, my last question b4 pulling the trigger on uninstalling network manager.
If this doensn't work, will I still be able to connect to the internet via my ethernet connection?
By the way, uninstalling network manager doesn't mean it is gone forever, it can be easily reinstalled via package manager, although you may need a working internet connection, which is ironic.

---

### Post by wieman01 on 2007-05-01
> **Supercross said:**
> By the way, uninstalling network manager doesn't mean it is gone forever, it can be easily reinstalled via package manager, although you may need a working internet connection, which is ironic.
Yeah, kind of reminds me of Joseph Heller's Catch-22. ;-)

---

### Post by qrprat77 on 2007-05-03
Ok,
So what the heck is wrong with my wireless?
I installed ndiswrapper 1.9, I installed wpa_supplicant, I deinstalled network-manager, I installed drivers from the hardware site (cd drivers didn't work under Edgy, so I figger same would be true under Fiesty) edited my interface file, installed all the modprobe crap, and basically followed the instructions from <a href="http://moonintheroom.blogspot.com/search/label/WUSB54G">Moon in The Room</a> except I use WPA-TKIP and not AES.  I even wrote the "networking restart" script.
He still don't work...
:mad: :confused:

---

### Post by qrprat77 on 2007-06-07
Ok,
I am having fun right now....
Kinda at least....
I am currently using my wireless dongle on Feisty Fawn, even with WPA  -TKIP!
YEah!
Here is what I did. 
0.  I made sure my system was up to date using a lame duck internet connection via my hardwired DSL modem.
1.  I checked out my hardware settings by using the dropdown menu, System>Preferences>Hardware Information.
2.  There I noticed that my device was listed under "rausb0" and not "wlan0"  Hmmmm, I said to myself.  I don't have a rausb0 in my interface configuration file, all my jazz is under wlan0.  I was under the general impression that wlan0 is where ndiswrapper likes its devices to live.
3.  I cut the configuration settings under wlan0 and pasted them under a newly created rausb0 setting.
4.  I commented out a line that reads" wpa-conf managed " because I kept getting something that said "wpa_supplicant cannot read contents of managed" when I would try to connect to the network.  
5.  I now connect, kinda...

My interface file says the following under the rausb0 entry:

auto rausb0
iface rausb0 inet dhcp
wpa-driver wext
#wpa-conf managed
wpa-ap-scan 2
wpa-scan-ssid 1
wpa-ssid (*mysitename*)
wpa-passphrase ********
wpa-key-mgmt WPA-PSK
wpa-pairwise TKIP
wpa-group TKIP
wpa-proto WPA

NOW,
sometimes, seems to be when I let the computer idle long enough to start a screensaver (I am unable to confirm this) the internet connection drops all of a sudden.  the" /*/networking restart" command isn't enough to get things right.  instead I must reboot the entire computer, anyone have any ideas???

---

### Post by bilbothebaggins on 2007-08-21
Hi all.

Let me add that after upgrading from Edgy 6.10 to Feisty 7.04 my WLAN/WUSB54Gv4 access was also broken all of a sudden. (Network was found but DHCP couldn't be resolved which means in my experience that wpa just doesn't behave)

After fiddling round and stumbling over this thread (via wired) I managed to get it working again.
I also had the error:
"wpa_supplicant: cannot read contents of managed"
when the interface was starting up.
after removing # wpa-conf managed it seems to work now ... let's just wait for the next reboot :-)

I'm using the ndiswrapper (v 1.9 with feisty) method and run on TKIP:

/etc/network/interfaces:
```
auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 essid Z...e
pre-up iwconfig wlan0 mode Managed
wpa-driver wext
# wpa-conf managed
wpa-ssid Z...e
wpa-ap-scan 1
wpa-prot WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 4...d

```

---

### Post by wieman01 on 2007-08-22
Can confirm that removing...
> wpa-conf managed
... will resolve the issue.

---

