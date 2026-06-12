---
title: "Wireless and sound trouble"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by StormGuy on 2006-12-16
I've been having some trouble getting my Broadcom 4311 card and my soundcard to work with Ubuntu on my laptop.

I've sorta managed to isolate what my problem is concerning my wireless card.  I have uninstalled an reinstalled the driver (according the the tutorials mentioned) many times, but the part I always get stuck at is section 7 of this  [walkthrough]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-6d614c29580a2a14cec5fa52014380e98af72e45")

My output from iwconfig is
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It looks fine, except for the ESSID section, which ought to contain my ESSID.  Also, whenever I run wifi-radar to try to find a wireless access point, it starts spamming this messagein in the terminal:
```

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

```

With regard to my sound problem, aplay -l returns this:
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Which, according to the Sound Problem Solutions Guide means my problem ought to just be that my sound is muted.  I've run the alsamixer command and the sound is both unmuted and at full blast.

---

### Post by x64Jimbo on 2006-12-16
I don't have the experience necessary to help with the sound, but your wifi problem is simple. Your interface can't scan for APs, but since you know your SSID, you can set it yourself. (preface all the following commands with sudo)
ifconfig eth1 down
iwconfig eth1 essid <your ssid>
ifconfig eth1 up
dhclient eth1

---

### Post by StormGuy on 2006-12-16
It keeps saying I don't have an eth1 device to manipulate:

```

eth1: ERROR while getting interface flags: No such device

```

Is it possible that there is a setting somewhere that is making my wifi-radar think I want it to use my eth1 to look for ports?  I don't know if that's possible or makes any sense...but it was my firsth thought :)

---

### Post by Jussi01 on 2006-12-16
Have you checked that the PCM volume is also up? this can affect all the sounds on your machine.

---

### Post by StormGuy on 2006-12-16
It's strange, after a fresh reboot...it no longer detects my soundcard when I use aplay -l :(

lspci -v returns this...which I think is my soundcard:

```

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
            Subsystem: ATI Technologies Inc Unknown device 437b
            Flags: bus master, slow devsel, latency 64, IRQ 10
            Memory at c00000000 (64-bit, non-prefetchable) [size=16k]
            Capabilities<access denied>

```

---

### Post by StormGuy on 2006-12-16
On the bright side, I'm getting a *beep* sound now when I try to move my curser in the terminal window using the left and right arrow keys...which, I guess is good. :)

---

### Post by x64Jimbo on 2006-12-17
> **StormGuy said:**
> It keeps saying I don't have an eth1 device to manipulate:

```

eth1: ERROR while getting interface flags: No such device

```Is it possible that there is a setting somewhere that is making my wifi-radar think I want it to use my eth1 to look for ports?  I don't know if that's possible or makes any sense...but it was my firsth thought :)
Substitute wlan0 for eth1 in all the commands I gave you.

---

