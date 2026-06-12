---
title: "Why would my wireless stop working when I restarted my computer?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by TopHatCat on 2007-03-18
I posted a topic some time back looking for help to get my wireless up and running on my new Ubuntu install.

To make a long story short, I got the wireless up and running and was able to connect to my MAC-filtered, WEP encrypted wireless network. Nothing has changed with my wireless network between then and now but now that I've restarted my laptop I can no longer pull an IP from my wireless network.

I know that my NIC is working because I can see my ESSID on Wifi-Radar.

Anyone know what might cause this little problem?

---

### Post by roachk71 on 2007-03-18
This is a known bug, and has an easy solution:

First, open a terminal window, and type:
```
 sudo nano /etc/init.d/wireless-network.sh
```Then, type this line into it:
```
/etc/init.d/networking restart
```and use Ctrl-X to save the file and exit Nano.

Now, you need to make this new file executable:
```
sudo chmod +x /etc/init.d/wireless-network.sh
```Finally, create a symlink:
```
sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S42wireless-network
```Now, all you should have to do is reboot.

If that didn't quite do the trick (and if you're using ndiswrapper), adding ndiswrapper to /etc/modules should finally have it up and running after a reboot. The reason for the multiple reboots is that modprobe sometimes goes awry when it's used manually.
:guitar:

---

### Post by TopHatCat on 2007-03-18
Hey, hey. You're at Kenai and I'm on Elmendorf. What are the odds? ;)

Hasn't seemed to work yet and I have no idea what ndiswrapper is or if I'm using it.

How would I go about adding it to /etc/modules?

---

### Post by roachk71 on 2007-03-18
Edit /etc/modules using nano, like the wireless-network file, and add ndiswrapper to the bottom of it (though it sounds as if you're not using the latest build.)

I'd almost forgotten to ask: What card are you using (Make, model and version)?

Some cards need the latest ndiswrapper built from source and the wireless driver from the installation CD, which I'd be happy to guide you through.

---

### Post by TopHatCat on 2007-03-18
Okay... (I'm really new at all of this but I did figure out what nano is with a little work, heh...)

So I typed nano /etc/modules and I arrow keyed down to the bottom of whatever the modules file is. I suppose I just add the text "ndiswrapper" to the bottom of it and save & exit?

I'm using an Atheros wireless NIC. Can't recall exactly which model off the top of my head, honestly. Built into my Toshiba Satellite P-30 laptop.

---

### Post by roachk71 on 2007-03-18
Hmm.

Ubuntu does have an included Atheros driver (madwifi), but how well that works depends on the exact wireless chipset. I used to own an AR5211-based card that worked well with the included driver (albeit somewhat unreliably; that's why I built ndiswrapper from source.)

If the wireless chipset is built-in, it can be a tad more difficult to find out what you're using in terms of wireless chipset, and you probably don't have the right installation CD to install the wireless driver from...

First off, try typing these into the terminal window, so we can try to find out what chipset's in use:
```
 dmesg > dmesg-out.txt
```and
```
 sudo lspci -vv > lspci-out.txt
```then change the permissions on the latter file:
```
 sudo chown *username* lspci-out.txt
sudo chmod 755 lspci-out.txt
```and post these two files (dmesg-out and lspci-out) in the next reply. I'll try to figure out what chipset's used from these files.

---

### Post by TopHatCat on 2007-03-19
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev$
        Subsystem: Askey Computer Corp. Unknown device 7065
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Steppin$
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <$
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at e8200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-$
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-




Atheros AR5212, according to lsoci-out.txt

How can I actually highlight all the lines of text from dmesg-out.txt? Seems to only allow me to highlight one page of text at a time so I can copy and paste.

---

### Post by roachk71 on 2007-03-19
No need; Apparently you're using a supported chipset (AR5212).

You might want to edit /etc/network/interfaces, looking for the ath0 device, and change it as follows (only change the lines indicated here):

```
iface ath0 inet static
address 192.168.1.24 (change the first two or three numbers to match your network)
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers (get this info from your ISP, addresses separated by a space; this should be placed at the bottom of the device's block)

```

Be sure to change the numbers in the addresses to match your router's network address scheme.

On some routers, DHCP takes an impossible amount of time to resolve. This is especially the case with madwifi, which is why a static IP is preferred.

---

### Post by TopHatCat on 2007-03-19
I have to assign myself a static IP? That kinda sucks. :)

*goes to try this*

---

### Post by roachk71 on 2007-03-19
Oh, and make sure this line:

```
auto ath0
```is at the beginning of the block, instead of the end.

---

### Post by TopHatCat on 2007-03-19
Actually - another question:   Does Fiesty correct this wireless bug? Maybe I should just ditch Edgy for Fiesty. Its not like I'm terribly attached to Edgy, I've only been using it for a few weeks.

---

### Post by TopHatCat on 2007-03-19
<Message Deleted>

---

### Post by roachk71 on 2007-03-19
I'll be testing wireless with my new card later tonight, but I'm sure its Marvell chipset needs ndiswrapper.

And I'm not sure, but I've read rumors that support is supposed to be much better. Of course, Feisty is still an alpha (Herd 5 right now), and using it as your primary OS isn't yet recommended.

All we're doing right now is trying to get real show-stopping critical bugs worked out. Once that's taken care of, there are still other bugs (a few of which I've already discovered) which should be taken care of before release.

Honestly, I don't like 6.10 myself; it proved too unstable for my computer. So I moved back to 6.06, and later decided to test Feisty. So far, so good, though. :)

_**UPDATE**_

It would appear that only WEP will work for now in wireless in Feisty. If you plan on using the more secure WPA or WPA2, you'll have to wait a month or so... :(

---

### Post by TopHatCat on 2007-03-19
When I rebooted using ndiswrapper in my modules file it wouldn't allow me to use either my wireless OR my wired connections...

Seems to me like modifying the interfaces file might get a little bit complicated considering I've had a hard enough time getting my wireless to work with something as simple as DHCP.  :)

---

### Post by roachk71 on 2007-03-19
I wonder what's in that file, anyway...

Does /etc/interfaces have an "ath0" or "wlan0" block?

It might be a good idea at this time for me to check with the Ubuntu HCL, and find out whether your hardware is really supported or not; this is beginning to stump me a little.

I'll be back...

Uh-Oh... It looks like your P30 isn't listed in the Hardware Compatibility Guide yet. :confused:

But neither is my Pavilion xt125, and it works great (except for having to use ndiswrapper, and the built-in modem isn't supported either.)

Quick question: do you have any installation CDs lying around?

_**UPDATE**_

SSID broadcast should be turned on for either Wifi-Radar or Network-manager to work correctly. Is this enabled on your router? (I realize this isn't a very secure option, but there's no way around it unless you want to keep updating your interfaces file.)

---

### Post by TopHatCat on 2007-03-19
/etc/interfaces doesn't have any block lines in it.

I do have the Edgy CD from last month's "Linux User & Developer" magazine laying around.

Exactly what does ndiswrapper do? All it did when I added it to my one file through nano was disable my communications entirely.

**EDIT**: SSID broadcast? I'll have to take a look.

**DOUBLE EDIT**: SSID broadcast is enabled on my router but I don't see any options for it in WiFi Radar.

---

### Post by roachk71 on 2007-03-20
The kind of installation CD I'm talking about here is for the card itself, which would contain the drivers for your wireless chipset. But considering this is an integrated component, this seems unlikely.

On the flip-side of the coin, though: You just told me quite a bit; if you have a relatively blank /etc/interfaces file without the "auto ath0" block, this means the interface configuration has to be entered by hand.

It could be something like this (the configuration here is for DHCP):
```
auto ath0
iface ath0 inet dhcp
wireless-ssid {your router's ESSID}
wireless-key {the router's WEP key}

```Note that if you're using WPA/WPA2 instead, the configuration is a bit more complicated.

Here's another example, for a static IP address:
```
auto ath0
iface ath0 inet static
address {any IP address not used by your network for DHCP}
netmask 255.255.255.0 {your netmask may differ}
network x.y.z.0 {works for a Linksys router, some are different}
broadcast x.y.z.255 {some use 254 instead}
wireless-ssid {again, your router's SSID}
wireless-key {...and, your WEP key.}
dns-nameservers {your DNS nameservers, each separated by a space}

```An interesting note: if you have a Linksys WRT54G with DD-WRT installed, the router can be set to your DNS servers, and you can simply supply your router's network IP address for each computer you use; DHCP, however, doesn't need this info.

Another note:

If you want the wireless interface to work right away, the wired connection has to be disabled and disconnected. So do that before editing the file. Once everything's ready, issue this command from the terminal window:
```
sudo /etc/init.d/networking restart
```

---

### Post by TopHatCat on 2007-03-21
Using DHCP on my router. Wouldn't I need to alter the interface file again if I ever want to change wireless networks if this is the fix action?

**EDIT**: Sadly this didn't fix it! lol  :)   Woe is me...

---

