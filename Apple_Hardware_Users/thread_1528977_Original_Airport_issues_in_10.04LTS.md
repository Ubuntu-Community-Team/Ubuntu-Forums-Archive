---
title: "Original Airport issues in 10.04LTS"
date: 2010-07-11
forum: Apple Hardware Users
---

### Post by Legal Beagle on 2010-07-11
To make it short, I have a 667MHz (Tibook) Powerbook G4 and a 500MHz Dual USB iBook G3 that I have successfully installed Lucid (10.04LTS) on. 

Everything works aside from the Airport cards. Lucid will recognize them on both machines and allow me to browse for wireless networks before showing me the proper SSIDs. Performance as expected up to this point.
 
I'm trying to connect to an Apple Airport Extreme (2003-ish) broadcasting on 802.11B and 802.11G (not G-only) without any  kind of authentication (WEP/WPA, etc.) Once I try to connect, I get a constant flurry of "Disconnected" or the spinning "connecting circles".

My Macbook Pro (10.6) can connect without issue as can my Acer Aspire One (XP).

I'm hoping somebody has some ideas.

I'm going to try to get it working on the 667MHz Powerbook G4 and all the information below is for that machine.

nm-tool gives me this (with hw addresses x-ed out, they come back correct):

```

NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airport
  State:             disconnected
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    SR-2:     Infra, xx:xx:xx:xx:xx:xx, Freq 2462 MHz, Rate 54 Mb/s, Strength 91 WEP

```Iwconfig gives me this:

```

eth1    IEEE 802.11b  ESSID:"SR-2"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Lspci gives me this:

```

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW322/323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

```And lsmod gives me this:

```

Module                  Size  Used by
binfmt_misc             8530  1 
radeon                802403  0 
ttm                    62566  1 radeon
drm_kms_helper         31219  1 radeon
drm                   192389  3 radeon,ttm,drm_kms_helper
ppdev                   7877  0 
lp                      9304  0 
parport                39110  2 ppdev,lp
ipv6                  299918  12 
sg                     32495  0 
sr_mod                 16052  0 
apm_emu                 1468  0 
apm_emulation           7311  2 apm_emu
snd_aoa_i2sbus         20791  0 
snd_pcm_oss            47872  0 
snd_powermac           68187  1 
snd_mixer_oss          19382  1 snd_pcm_oss
snd_pcm                87095  3 snd_aoa_i2sbus,snd_pcm_oss,snd_powermac
snd_seq_dummy           1766  0 
michael_mic             2384  4 
snd_seq_oss            36232  0 
snd_seq_midi            6161  0 
snd_rawmidi            24746  1 snd_seq_midi
snd_seq_midi_event      7367  2 snd_seq_oss,snd_seq_midi
snd_seq                61897  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24515  2 snd_pcm,snd_seq
snd_seq_device          7524  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 37678  0 
airport                 3786  0 
snd                    70628  12 snd_aoa_i2sbus,snd_pcm_oss,snd_powermac,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           25736  1 
orinoco                71822  1 airport
cfg80211              152734  1 orinoco
rsrc_nonstatic         11098  1 yenta_socket
pmac_zilog             18110  0 
soundcore               7534  1 snd
uninorth_agp            8437  1 
usb_storage            46294  0 
rfkill                 20725  2 cfg80211
serial_core            23813  1 pmac_zilog
evdev                  10257  17 
snd_aoa_soundbus        4916  1 snd_aoa_i2sbus
rtc_generic             1391  0 
pcmcia_core            40156  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                39895  3 ttm,drm,uninorth_agp
snd_page_alloc          7660  1 snd_pcm
usbhid                 44238  0 
hid                    78460  1 usbhid
ohci1394               35584  0 
sungem                 32704  0 
ieee1394               97330  1 ohci1394
sungem_phy             12365  1 sungem
windfarm_core          10420  0 

```Hopefully that's enough information for somebody to help me out with some ideas..

Thanks!

---

### Post by Legal Beagle on 2010-07-11
I've been keeping after it, and here's what I've tried so far:

First, I tried "iwconfig" and it comes back with an entry for eth1 and the ESSID of my Apple Airport.  So far, so good.

Next, I tried "iwlist scan" to get the address. It pops right up and I dutifully copy it.

Finally, I try "iwconfig eth0 ap xx:xx:xx:xx:xx:xx" where xx is the address from "iwlist scan".

I get back:

```

Error for wireless request "Set AP Address" (8B14) : SET failed on device eth0 ; Operation not supported.

```So then I try to edit /etc/network/interfaces:

[code]
iface wlan1 inet dhcp
name Wireless LAN card
wireless_mode managed
wireless_essid [I put my essid here]

wireless_channel 1
auto wlan1
[code]

Restarted.. Still won't connect, either through the Network Manager or when I try it in the command line. 

>_<

Help.

---

### Post by Legal Beagle on 2010-07-13
Still fighting with it.. Anybody have better google-fu to point me in the right direction..?

---

### Post by linuxopjemac on 2010-07-13
first, your wireless lan is eth1, not wlan0 and also not eth0. So you first want to change that in /etc/network/interfaces.

Apart from that, I would empty that file and let networkmanager or wicd do the job.

If you insist on /etc/network/interfaces:

```
sudo ifdown eth1
sudo ifup eth1
```

would make your connection come up, provided everything is put right in that file.

---

### Post by Legal Beagle on 2010-07-13
Glad to have somebody else to bounce ideas off of! Thank you for replying.

I cleared out the /etc/network/interfaces as you suggested.

I tried the "ifdown" code you suggested and returned:

```

ifdown: interface eth1 not configured

```Then ifup gets this:

```

Ignoring unknown interface eth1=eth1

```I don't understand why I can see all the networks but can't connect to them.

What other information would be helpful for me to give you?

---

### Post by linuxopjemac on 2010-07-14
If you cleared out the interfaces file, you can't manually ifup and ifdown anymore, as that interface is gone from the configuration file.

You need network-manager or wicd to make connections with an open /etc/network/interfaces file.
```

sudo apt-get install wicd
```

Then you will see an network applet somewhere. Click on it and try to make a connection.

---

### Post by stmiller on 2010-07-14
Yeah don't mess with if up / down unless you really want to. Use network manager or wicd.

That original airport card just works(TM) without modification. It can't do any WPA encryption, only WEP max due to the hardware limitation.

Can you connect with it at a coffee shop, or home wifi? 

I don't have my old Tibook anymore, unfortunately.

---

### Post by Legal Beagle on 2010-07-15
I double-checked network manager and get this back:

```

network-manager is already the newest version.

```I gave it a shot with installing wicd and get this back:

```

Setting up wicd-daemon (1.7.0+ds1-2) ...
 * Starting Network connection manager wicd                              [fail]

```I've tried it in four different places on four different unsecured wireless networks -- each of them has been a different type (eg. Apple Airport Base Station, Belkin, Netgear). The Tibook and iBooks still see the networks and the ssids, but still refuse to connect.

On identical hardware that has Mac OSX, it connects without issue.

I don't know if it's a driver issue.. If I were to liken it to a two-way radio, it's almost like it can receive but not transmit.

---

### Post by Legal Beagle on 2010-07-18
FINALLY got it all working -- thank you everyone for all your help!

I followed the suggestion to use wicd but still had connection errors and ran down the list of steps in the wireless troubleshooting guide. I had forgotten to remove network-manager after installing wicd, and it was conflicting somehow.

```

sudo apt-get install wicd
sudo apt-get remove network-manager

```

It works perfectly now.

---

### Post by msiviter on 2010-10-29
I've installed wicd and uninstalled network manager but it doesn't resolve my problem, it still will not connect to the router if any security is enabled. Every time using every type of security it returns "bad password". With security turned off it connects just fine. 


Any ideas? Thanks

Matt

NB it doesnt see my android phones wireless tether either (but that's not a real concern)
I've tried caps on and off!

---

### Post by Legal Beagle on 2010-10-30
The type of security makes a difference -- are you trying it with WPA?

I've found that I've had to turn off passwords on my router for it to work consistently. If you can snag another wireless access point, here's the setup that I'm using:


Router <--- switch <--- Apple Airport Extreme (with security for all my "new" boxes)
                            <--- Old Apple airport (with no security, but restricted MAC address).


I made sure that they're not assigning new IP addresses, so they're all running off the 192.168.x.x addressing scheme off my router and everything sees everything else.

It's kind of like this example on page 48:
[http://manuals.info.apple.com/en/designing_airport_networks_10.5-windows.pdf](http://manuals.info.apple.com/en/designing_airport_networks_10.5-windows.pdf)

Hope that helps.

---

