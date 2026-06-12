---
title: "Help!!!!! - Integrated DVB-T TV-Tuner"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-07-19
Please help!
I have now been looking for at way to watch tv on my integrated tv-card for several months. 
I've regularly taken turns looking up information that would get my tv-card working.
I have installed anything and everything I came across that had the words 'tv' or 'tuner' in name or description and even if it had been mentioned on some website as having something to do with watching tv on the computer. None of these programs have brought the desired result. All roads seem to be dead ends.

From many comments/descriptions around the Net it seems it should be possible, and even without too much hassle so now I feel that I am missing something very obvious.

If someone could help either telling me that what I want is not possible or a very noob-friendly description of how to accomplish a working tv-card I will be absolutely grateful.

I own an Asus notebook, W1Jc (Ubuntu 7.04)  with integrated DVB-T tuner, I'm not sure which make or chipset - from the hardware information dialogue it says:

(Device tab):
Vendor: Philips Semiconductors
Device: SAA7133/SAA7135 Video Broadcast Decoder
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabitities: Unknown

(PCI tab):
Vendor: Philips Semiconductors
Device: SAA7133/SAA7135 Video Broadcast Decoder
OEM Vendor: Avermedia Technologies Inc
OEM Product: Unknown (0xf636)

---

### Post by Martin on 2007-07-24
first question have you installed xine?

---

### Post by spur on 2007-07-24
I don't think pou need xine specifically. Have you checked the right  input stream on the tv program. On most you have to set it to Television, composite, s video or some other. Remember to also choose the device first.
When you open the program what shows up? Remember your card as dvb-t is a digital card and the program has to support that.

---

### Post by Lakefall on 2007-07-25
I'm afraid your device may not be supported.

You should try to figure out what it is exactly and look at the [linuxtv.org DVB Wiki](http://www.linuxtv.org/wiki/index.php/Main_Page). As it is a wiki, you can help by adding a page for the device, if one does not exist. You need to create an account there before you can do that though. If it really is an integrated device, [the wiki doesn't even have a generic page for those](http://www.linuxtv.org/wiki/index.php/DVB-T_Devices), so I guess support is unlikely.

What does *lspci -v* say about it?

edit: Perhaps it's one of these?
[http://www.linuxtv.org/wiki/index.php/AVerMedia](http://www.linuxtv.org/wiki/index.php/AVerMedia)

---

### Post by fsando on 2007-07-27
Thanks a lot for the answers

> **Martin said:**
> first question have you installed xine?
I have installed Xine again, pressing the 'DVB' button results in an error dialogue:

> Input plugin failed to open mrl 'Sorry, No channels.conf found'

And a second one (they come together)

The specified file or mrl is not found. Please check it twice (Sorry, No channels.conf found)

I've seen that before and I think you're supposed to make a channels.conf with scan but what is mrl?
```
~$ scan all
scanning all
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
finn@finnubuntu:~$ 

```
Does this mean that a device should have been created in /dev/dvb/ but for some reason it wasn't?
> **Lakefall said:**
> 
What does *lspci -v* say about it?


I suppose you only want to see the video broadcast part?
```
~$ sudo lspci -v
...
07:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Unknown device f636
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
...

```
I'll give your links a closer look as soon as I get some time.

---

### Post by Lakefall on 2007-07-30
Google suggests it's AVerMedia M103 Hybrid or something like that.

[http://www.google.com/search?q=%22Avermedia+Technologies%22+f636&filter=0](http://www.google.com/search?q=%22Avermedia+Technologies%22+f636&filter=0)
[http://www.google.com/search?q=%22AVerMedia+M103+Hybrid%22+linux&filter=0](http://www.google.com/search?q=%22AVerMedia+M103+Hybrid%22+linux&filter=0)

---

### Post by fsando on 2007-08-02
Thanks I'm looking into it.
I'll be back soon -  don't have much time so it will be on/off as time allows.

---

### Post by fsando on 2008-05-27
Just to wrap this up. I never got it to work - have given up on it.

---

