---
title: "Wireless Encryption"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by jideuu on 2007-10-03
I've been having problem getting Ubuntu to connect to the internet and I've narrowed it down to the encryption I use on my wireless card. (I turned the WEP off via Windows, and was able to connect on Ubuntu. However, I can't keep my WEP key turned off forever, for obvious reasons.)

I use a 64-bit WEP key. My router generates four 10 character long keys. It uses the first as default.
I have entered all four, several times, in both the 'hexadecimal' and 'ascii' format. And none of the times it has worked. I have also tried switching to WPA encryption, but Ubuntu doesn't seem to support it.

---

### Post by Pumalite on 2007-10-03
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

---

### Post by jideuu on 2007-10-03
That's pretty much told me what I already knew. 
WEP is supported 'out-of-the-box'. So if it doesn't work, I've misspelt the key.

Despite being very sure I haven't typed it wrong, I went and checked all the keys, went onto Ubuntu and tried them all again. No luck.

---

### Post by benerivo on 2007-10-03
These are long shots, but have you tried manually entering a single WEP key of something like '123' or rebooting the router? I know i had problems getting my apple mac mini to connect. In the end i used a manually entered WPA key.

---

### Post by jideuu on 2007-10-04
Oh yeah, checked all those things, I've tried copy and pasting the keys as well as manually entering them. And have rebooted the router several times before posting this thread.

---

### Post by multifaceted on 2007-10-04
Do another manual config.Change it to **ESSID** and then enter you Hex key... that worked for me but, every few hours or so, I lose connection. But you can fix it it by un-checking and re-checking the wireless connection field from the Manual configuration menu.

Mine is a desktop though with a USB adapter receiver... don't know if it will solve it for a laptop's card. 

hope this helps!

---

### Post by brigux on 2007-10-04
Wep or no encryption is about the same...
It takes most people about 30mn to crack a WEP password. Some people created a new code a couple of month ago and they can crack the WEP password in about 1 mn.
So I'd say, either you dont bother with encryption or if it's important for you (and it should be unless you use a VPN directly upon connection) then you need at least WPA.

no really.

---

### Post by jideuu on 2007-10-04
Well, where I live, I'll be damned if anyone even understands what 'Operating System' means. So, I'm fine with WEP for the moment, I didn't ask for security tips, thanks.

Anyway, I've tried the manual configuration multifaceted, but it doesn't seem to work. I'm going to try changing some more settings on my router.

Thanks for all your help so far.

---

### Post by brigux on 2007-10-04
> **jideuu said:**
> [...] I'll be damned if anyone even understands what 'Operating System' means. So, I'm fine with WEP for the moment, 

And if no one except you can understand the words OS, you need weak encryption because...?^^

> **jideuu said:**
> I didn't ask for security tips.

Thanks! I take that as a compliment!

---

### Post by jideuu on 2007-10-04
...because I simply want it to stop people from connecting to my wi-fi instantly. Again as they aren't exactly clued into the whole tech job, they tend to use roaming connections which connect to anything and everything.

I'm willing to try out WPA if it will allow me to connect.

---

### Post by Austin_KW on 2007-10-04
What is your wireless adapter, some adapters need to be configured manually for security settings.

if you don't know the adapter type, post the output of the following commands from a terminal
```
lspci
lsusb
```

---

### Post by jideuu on 2007-10-04
This is the adapter:

**00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)**

---

### Post by benerivo on 2007-10-04
Have you got any setting known as 'Wireless Station Access List'. Mine has and here is what my router help says about it. It would explain why you can't connect even with the right key.


Wireless Station Access List Help

By default, any wireless PC that is configured with the correct SSID will be allowed access to your wireless network. For increased security, you can restrict access to the wireless network to only allow specific PCs based on their MAC addresses.

The Wireless Station Access List page displays a list of wireless PC's that will be allowed to connect to the Router based on their MAC addresses. These wireless PCs must also have the correct SSID and WEP settings (as configured on the Wireless Settings page) to access the wireless network.

Turn Access Control On

   1. Click the check box to Turn Access Control On to enable the restricting of wireless PCs by their MAC addresses.
   2. Click the Apply button to save changes and return to the Wireless Settings page. 

Note: If the Turn Access Control On is enabled and the Trusted Wireless Stations list is blank; then all wireless PCs will be unable to connect to your wireless network.

---

### Post by jideuu on 2007-10-04
I suppose my alternative would be 'MAC Address Filtering' but it's turned off.

---

### Post by benerivo on 2007-10-04
I don't think this combination is possible, but could you leave the signal unencrypted and turn the MAC Address Filtering on, and just include the MAC address of the Ubuntu system in the access list?

---

### Post by jideuu on 2007-10-04
It's not an ideal situation, because I have an unholy amount of other devices I'd like to connect also but don't necessarily know how to find their MAC Addresses, e.g. PSP.

---

### Post by benerivo on 2007-10-04
If you do use that method, then to find the MAC address of your PSP (from a google search)...

   1. Navigate to "System Settings";
   2. Then navigate to "System Information," which is where the MAC address is listed.

---

### Post by benerivo on 2007-10-04
Do you get any useful info from this command ```
sudo iwlist scan
```

---

### Post by jideuu on 2007-10-04
Standard Stuff, like ESSID, Frequencies, Encryption Key: On.

---

### Post by benerivo on 2007-10-04
Also have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=559154&highlight=RTL-8185+IEEE+802.11a%2Fb%2Fg+Wireless+LAN+Controller"). It is the same problem.

---

### Post by jideuu on 2007-10-04
I don't think the MAC Address is the problem because I am able to connect when I have encryption(WEP) off, but when it's on the connection doesn't work.

---

### Post by Lambert on 2007-10-04
This is a realtek card. do you know what driver is being used?

If not run this code

```

sudo lshw -C network

```The reason I ask is the driver r818x has this information with it.

> hwwep: Try to use hardware WEP support. **Still broken and not available on all cards** (uint)There might be more information out there, need to dig some more.

One more thought, run this command and post output.

```

sudo lsmod | grep ieee80211

```

---

### Post by jideuu on 2007-10-04
sudo lshw -C network:
 ```
 *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: wlan0
       version: 20
       serial: 00:12:0e:47:83:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.48+Realtek,10/20/2005,5.103.10 latency=32 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: ioport:f800-f8ff iomemory:dfffd000-dfffd1ff irq:23
```

For "sudo lsmod | grep ieee80211" absolutely nothing cam up.

And it uses the r818x drivers.

---

### Post by Lambert on 2007-10-04
Try running this command and see if you can connect.

```

sudo modprobe ieee80211_crypt_wep

```run this command to make sure it loaded

```

sudo lsmod | grep ieee

```

should deisplay in output along with one that says just ieee80211_crypt

And if so try to connect using wep.

---

### Post by jideuu on 2007-10-05
It doesn't seem to have done much, still no connection. There is bound to be some way of getting this to work, it's just finding that something which proves hard. ](*,)

---

