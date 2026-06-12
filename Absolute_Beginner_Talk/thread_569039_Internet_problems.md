---
title: "Internet problems"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by uniterror on 2007-10-06
I installed a fresh copy of the 7.10 beta fine with no problems until i tried connecting to the internet

and even from the Live CD i couldn't get anywhere despite being connected to the internet

I tried pinging 192.168.0.1 and i get fine results, ive disconnected the router for the time being and i get no advances

The only problem I've seen is that for the network cards I'm stuck on that main loopback (lo) setting

and when i try to configure to my ethernet card I get an "Interface does not exist" error

I've looked around but i'm sure other people have had this problem

suggestions?

---

### Post by ofb on 2007-10-06
Okay, give us some output to look at. In a terminal, enter each of these,

sudo lshw -C network
cat /etc/network/interfaces
sudo ethtool eth0

Also, have you used 7.04 successfully?

---

### Post by uniterror on 2007-10-06
I haven't tried 7.04 yet
I was thinking about resorting back to it though if it could somehow help with the internet connection

and heres some information you asked for

in result to sudo lshw -C network i got
```

*-network
description: Ethernet interface
product: RTL- 8139/8139C/8139C+
vendor: Realtek Semiconductor co.,Ltd.
physical id:3
bus info: PCI@0000:02:03.0
logical name: eth0
version:10
serial:00:13:d4:e2:09:35
size: 100 Mb/s
width:32 bits 
Clock: 33 mhz
capabilities pm bus_master cap_list ethernet physical tp mil 10bt 10bt-fd 100 bt 100bt-fd auto negotiation 
Configuration: auto negotiation=on broadcast=yes driver= 8139too driver version=0.9.28 duplex=full latency=64 link=yes maxlatency=64  mingnt=32 module=8139too multicast=yes port=MII speed=100 Mb/s
```
**In result to cat /ect/network/interfaces i received**
```

auto lo 
iface 10 inet loopback


iface eth0 inet dhcp
auto eth0

```

**And lastly in result to "sudo ethtool eth0" i received **
```

supported ports: [TP MII]
supported linkmodes: 10baseT/half 10baseT/full  100baseT/half 100baseT/full 
supports auto-negotiation:Yes
advertised link modes:  10baseT/half 10baseT/full  100baseT/half 100baseT/full 
Advertised auto negotiation: Yes
speed: 100Mb/s
Duples: Full
port: MII
phyad:32
Transceiver: Internal
Auto-negotiation: On
Supports wake-on:pumbg
wake-on:d
current message level: 0x00000007 (7)
link detected :yes

```

I tried my best to get it copied right

any suggestions would be greatly appreciated

---

### Post by ofb on 2007-10-06
Oh geeze, did you do that longhand? Ouch. I was thinking you'd copy the output to a CDRW or floppy. I'm glad I didn't ask for dmesg.

Although I may next. Hum...

Kinda funny "auto eth0" is below the "iface eth0" line but I suppose that's okay. 

I don't see an IRQ listed at the end of that lshw.

Try,

cat /proc/interrupts

Look for an IRQ listed for eth0 in there. It may be sharing with other devices, though that's fine. We're just making sure it's showing up.

Also when you boot, see what the BIOS assigns. Right after the memory check clicks by, you'll very briefly get a screen showing devices and IRQ, then the Grub screen. Back at that device & IRQ screen, hit the Pause/Break key to pause it and see what IRQ is assigned to eth0. Hit space-bar to resume.

And yeah, toss in 7.04 and see if that works, if you have it handy. Beta does mean beta, after all.

---

### Post by uniterror on 2007-10-06
alright thanks, at the moment i'm burning 7.04 hopefully that will work

but as far as the IRQ situations I didn't see anything at the boot screens about an IRQ

for the commands all I see about the eth0 is 

```
10:    11 IO-APIC eth0
```

I know it may not be alot of help, but i'm rather about what the problem is here

and yea i did longhand all of that, i dont have even a CD drive on this computer, and i cant seem to get my flash drive to work yet

thanks alot though, have any suggestions

---

### Post by ofb on 2007-10-06
Yeah, that part of the boot screens flashes by pretty quick. It's the brief flash right after the memory-check page.

The  /proc/interrupts file shows IRQ 10. Now /why/ was that not included in lshw then?

And for that matter, I really expected the first line of that lshw output would say something like "*-network:0 DISABLED". But other than the missing interupt (IRQ), things look good.

Are you familiar with BIOS? If so, have a look to see if PNP (Plug'n'Play) is enabled under Boot options. Disabled is prefered, and is probably what it's set at.

Also run,
dmesg | grep 8139too

See if that brings up any interesting lines. Like including the word 'disabled'

I don't have a clear idea right now. I'm trying to find clues to take us to the trouble. Going to have to think for a bit.

Meanwhile, yeah see if the 7.04 LiveCD connects okay.

You can also run the same commands to look for differences.

Incidentally, has this computer run any OS successfully with its current configuration? That'll confirm we're not just having bad hardware or bad cable problems.

---

### Post by uniterror on 2007-10-07
well In the BIOS plug and play is on
I've ran the first few commands again and Im not seeing anything Disabled
I ran dmesg as well and theres no disabled

I know i'm not giving alot of information but is there some sort of configuration i should be doing to get the internet to work or is it all auto enabled at the start

and yes i have had used XP and vista until just now switing over, i did a full format first though so the drive was clear

---

### Post by ofb on 2007-10-07
> **uniterror said:**
> I know i'm not giving alot of information but is there some sort of configuration i should be doing to get the internet to work or is it all auto enabled at the start

It should just up & go. Autodetection is very good these days. But the great thing with the LiveCD is you can test that before installing, to see if you have the rare problem. 

Try it with the BIOS PnP disabled. It's not as useful as the name makes out. Normally the BIOS assigns all the interrupts. PnP passes that task to the OS, which is a Windows thing. (My Win doesn't /need/ it though. I'm not sure what the supposed advantage is.) Linux uses the BIOS's assignments. 

After that, and if 7.04 is no good, I think looking at Network Manager is next. It's for roaming connections like wifi. I had that get in the way of connecting on a Kubuntu 7.04 install, and removed it via Synaptic. (since I didn't have a roaming laptop.)

I'll look into that later to give you the proper names under Gnome. Right now I've got to stop for the evening.

---

