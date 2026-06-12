---
title: "Yay Wireless Problems!"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by skeating on 2007-03-19
Hello all--

I posted a request for help about two weeks ago, and though the first reply was friendly, it didn't solve my problem.  I've been busy and didn't think it would be good form to necro that old post, so I'll start anew:

I've installed NDisWrapper (and it shows that I've mounted the proper drivers to the card, etc)

The card is a TrendNet PEW321 type B

when I run lspci, i get:

```
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
01:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
```

 and when i run iwconfig:


```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

any suggestions or ideas?  I'll be on all night trying to get this to work (yay spring break!)

---

### Post by vgrisham on 2007-03-19
I have a suggestion, although you may think it counter intuitive. Download and boot to the Dapper live cd (or DVD). Edgy's wireless support is a step backwards from Dapper (see multiple threads in this forum). If it works, seriously consider installing Dapper. It is rock solid and isn't nearly as flaky as Edgy. Alternatively, wait for Fiesty Fawn. Wireless is supposed to be much improved (although I couldn't get my Atheros card to work in the Herd 5 Alpha release). 

As far as Dapper goes, I've been running it since November and I haven't found a single thing that I haven't been able to do. I'm running the latest Firefox, the latest Amarok and the latest KMyMoney. And wireless under Dapper just works.

---

### Post by skeating on 2007-03-19
is there any way that i can change the /etc/apt/sources.list to point to the dapper repositories?  I don't like burning CDs (also, I don't have any more)

I can't figure out how to edit the sources.list file (can't get su privileges)

any ideas?


PS  I'm not stupid (please see the misspelling of "wireless"), I'm just on an unfamiliar keyboard...i promise :)

---

### Post by dstew on 2007-03-19
Looks like the driver did not take.

---

### Post by vgrisham on 2007-03-19
> **skeating said:**
> is there any way that i can change the /etc/apt/sources.list to point to the dapper repositories?  I don't like burning CDs (also, I don't have any more)

I can't figure out how to edit the sources.list file (can't get su privileges)

any ideas?


PS  I'm not stupid (please see the misspelling of "wireless"), I'm just on an unfamiliar keyboard...i promise :)

In a terminal, type or paste the following command, then enter your password:
sudo gedit /etc/apt/sources.list

---

