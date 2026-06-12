---
title: "WiFi problem on G4 iMac running 14.04"
date: 2015-03-14
forum: Apple Hardware Users
---

### Post by Martin_Srensen on 2015-03-14
I have a puzzling WiFi problem with our iLamp running 14.04.1

It has a built in AirPort card, but as that is ancient and does not support WPA (which our networks are set up to use) I decided to plug in a more recent USB adapter I had lying around.

The machine reports it as a Realtek RTL8188S, and it also claims to connect to the WLAN, all well and good. I just do not have access to anything.

When I open System Information -> Interfaces it claims that wlan0 has a believable ip address (192.168.x.x)

When I open Network connections -> Network Name -> Edit, I see that it is set to Automatic (DHCP), but Addresses are empty.

When I open Network Settings -> DNS the only DNS server is itself, 127.0.1.1

I left the AirPort card in, can that give problems?

I have been messing with networks before, but mostly on OS X. Could be something simple...

---

### Post by rican-linux on 2015-03-14
can you send the output of your lsmod?

---

### Post by Martin_Srensen on 2015-03-15
> **rican-linux said:**
> can you send the output of your lsmod?

Here it is:

> [FONT=courier new]Module                  Size  Used by[/FONT]
[FONT=courier new]rfcomm                 59709  0 [/FONT]
[FONT=courier new]bnep                   15661  2 [/FONT]
[FONT=courier new]bluetooth             360536  10 bnep,rfcomm[/FONT]
[FONT=courier new]parport_pc             36057  0 [/FONT]
[FONT=courier new]ppdev                   9199  0 [/FONT]
[FONT=courier new]lp                      8879  0 [/FONT]
[FONT=courier new]parport                36819  3 lp,ppdev,parport_pc[/FONT]
[FONT=courier new]snd_powermac           65375  1 [/FONT]
[FONT=courier new]mac_hid                 3597  0 [/FONT]
[FONT=courier new]snd_pcm                94032  1 snd_powermac[/FONT]
[FONT=courier new]snd_page_alloc          7356  1 snd_pcm[/FONT]
[FONT=courier new]r8712u                176651  0 [/FONT]
[FONT=courier new]rtc_generic             1187  0 [/FONT]
[FONT=courier new]snd_seq_midi            5892  0 [/FONT]
[FONT=courier new]snd_seq_midi_event      6943  1 snd_seq_midi[/FONT]
[FONT=courier new]snd_rawmidi            22228  1 snd_seq_midi[/FONT]
[FONT=courier new]snd_seq                62457  2 snd_seq_midi_event,snd_seq_midi[/FONT]
[FONT=courier new]snd_seq_device          6906  3 snd_seq,snd_rawmidi,snd_seq_midi[/FONT]
[FONT=courier new]snd_timer              22194  2 snd_pcm,snd_seq[/FONT]
[FONT=courier new]snd                    64958  9 snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_powermac,snd_seq_midi[/FONT]
[FONT=courier new]soundcore               1096  1 snd[/FONT]
[FONT=courier new]apm_emu                 1404  0 [/FONT]
[FONT=courier new]apm_emulation           6981  1 apm_emu[/FONT]
[FONT=courier new]michael_mic             2184  4 [/FONT]
[FONT=courier new]uio_pdrv_genirq         3754  0 [/FONT]
[FONT=courier new]uio                     9785  1 uio_pdrv_genirq[/FONT]
[FONT=courier new]airport                 3654  0 [/FONT]
[FONT=courier new]orinoco                73356  1 airport[/FONT]
[FONT=courier new]cfg80211              424569  1 orinoco[/FONT]
[FONT=courier new]hid_apple               5782  0 [/FONT]
[FONT=courier new]hid_generic              928  0 [/FONT]
[FONT=courier new]usbhid                 46604  0 [/FONT]
[FONT=courier new]hid                    92296  3 hid_generic,usbhid,hid_apple[/FONT]
[FONT=courier new]nouveau              1085947  2 [/FONT]
[FONT=courier new]firewire_ohci          34367  0 [/FONT]
[FONT=courier new]sungem                 29314  0 [/FONT]
[FONT=courier new]firewire_core          63034  1 firewire_ohci[/FONT]
[FONT=courier new]ttm                    77426  1 nouveau[/FONT]
[FONT=courier new]sungem_phy             11874  1 sungem[/FONT]
[FONT=courier new]crc_itu_t               1471  1 firewire_core[/FONT]
[FONT=courier new]drm_kms_helper         43971  1 nouveau[/FONT]
[FONT=courier new]drm                   271232  4 ttm,drm_kms_helper,nouveau[/FONT]
[FONT=courier new]uninorth_agp            7396  1 [/FONT]





An interesting detail: the machine seems to have managed to contact a time server - the PRAM better is dead of old age, but during my messing around it got the right date and time.

---

### Post by rican-linux on 2015-03-15
Sorry I also meant to include this command lspci

---

### Post by Martin_Srensen on 2015-03-15
> **rican-linux said:**
> Sorry I also meant to include this command lspci

Like this:

> 0000:00:0b.0 Host bridge: Apple Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: NVIDIA Corporation NV17M [GeForce4 440 Go] (rev a3)
0001:10:0b.0 Host bridge: Apple Inc. UniNorth/Pangea PCI
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB controller: Apple Inc. KeyLargo/Pangea USB
0001:10:19.0 USB controller: Apple Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Inc. UniNorth/Pangea GMAC (Sun GEM)


Hope this makes you wiser.

I must admit it is _many_ years since I have done anything in a terminal - I got "The complete Idiot's guide to UNIX" out for the occasion :-)

---

### Post by rican-linux on 2015-03-15
Is that the entire output?  I don't even see the built in airport card. I would expect to see that.

---

### Post by rican-linux on 2015-03-15
I would expect to see something like this:

```
rican-linux@ibookG4-MATE:~$ lspci
0000:00:0b.0 Host bridge: Apple Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV360/M12 [Mobility Radeon 9550] (rev 80)
0001:10:0b.0 Host bridge: Apple Inc. UniNorth 2 PCI
**0001:10:12.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:10:1b.1 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:10:1b.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)
0002:20:0b.0 Host bridge: Apple Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Unassigned class [ff00]: Apple Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
rican-linux@ibookG4-MATE:~$ 

```

---

### Post by rsavage on 2015-03-16
> **Martin_Srensen said:**
> 

It has a built in AirPort card, but as that is ancient and does not support WPA (which our networks are set up to use) 

Airport (classic and extreme) do support WPA.

---

### Post by Martin_Srensen on 2015-03-16
> **rsavage said:**
> Airport (classic and extreme) do support WPA.

OK, I thought it only supported WEP. I will try to run with AiPort card only tomorrow morning. The reason I thought is was so was because:

We have two networks,

- one I have set up on own AP's with WPA and that we normally use
- the one set up by the Telecom Provider (directly on the ADSL box), which I only connect to when I want to check if it is ok. I am not sure if that is WEP or WPA.

The Lubuntu desktop gave me 3 options of connecting:

With the USB adapter to both APs; only the connection the my own AP allegedly worked. The ADSL one spent ages not connecting.
With the AirPort my own AP was greyed out, I am not sure if I tried the ADSL box.

If I don't get it to play soon I may have to try setting up a powerline connection, that way I can have a ethernet socket.

Thanks,

Martin

Edit: Just tried without USB WiFi adapter, built in AirPort behaves the same.

---

### Post by Martin_Srensen on 2015-03-17
I just had a 3rd look: Of course I am running WPA2 on my own WiFi, that the original Airport Card can't.

---

### Post by Martin_Srensen on 2015-03-17
OK, I now changed from WPA/WPA2 to plain WPA*), and the iLamp connects through the old AirPort card. I now just have to check if it works where I want it to work, but at least I can connect with my MacBook.

It still does not explain why I apparently get a connection I do not have access to using the USB adapter - or why lspci is not reporting any of them for that matter. Perhaps some sort of "the other one handles this"? Oh well

Thanks for you time

Martin

*) I think I can live with the sightly higher security risk. We are in the countryside, and the only neighbour who can possibly see the signal is more into nicking scrap metal than any computer related crime.

---

