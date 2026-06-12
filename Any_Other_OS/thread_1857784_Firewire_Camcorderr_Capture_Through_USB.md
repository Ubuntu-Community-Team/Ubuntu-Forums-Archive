---
title: "Firewire Camcorderr Capture Through USB"
date: 2011-10-10
forum: Any Other OS
---

### Post by tigreped on 2011-10-10
Hi, I'm running Mint 11, which works pretty much like an Ubuntu distro, so I'm assuming any solutions here should do for me, correct me if I'm wrong on that as well.

I have a JVC GR-D850UB camcorder that I used to broadcast live on a MacBook via livestream, conecting the camera through it's DV firewire port.

I wish to try it on my compaq notebook running mint, that does not have FireWire ports.

So I went on ebay and (now I'm starting to think naively) got myself a firewire to usb adapter cable. I suppose the cable is working just fine.

So I plugged the dvd end on the JVC camera, plugged the usb end of the cable to my notebook, turned on the camera, set it to REC mode, and got absolutly nothing on "dmesg | grep usb". Setting it to PLAY mode made no difference eiter.

So I'm supposing there was no understanding between both parts.

What I guess that I want to know is if there is a way to, using only software, simulate the processing of the firewire standard (IEEE1394) data, through the usb2.0 port, so that the computer gets to recognize the raw data from the camera, in order for me to stream the data in tools such as livestream.com.

If there's absolutly no way to do this and the only way is to indeed get a firewire card, that would end this thread quickly, but I'd end up sad! Hope someone has some clever solution to it.

Cheers.

---

### Post by Perfect Storm on 2011-10-11
Moved to Other OS/Distro Talk.

---

### Post by mips on 2011-10-11
> **tigreped said:**
> 
So I went on ebay and (now I'm starting to think naively) got myself a firewire to usb adapter cable. I suppose the cable is working just fine.

Got a link to the adapter cable, sounds fishy?

---

### Post by tigreped on 2011-10-11
> **mips said:**
> Got a link to the adapter cable, sounds fishy?

mips the cable is one as such:

[http://www.ebay.com/itm/5ft-USB-Firewire-iEEE-1394-4-Pin-iLink-Adapter-Cable-/300448018068?pt=LH_DefaultDomain_0&hash=item45f418ee94](http://www.ebay.com/itm/5ft-USB-Firewire-iEEE-1394-4-Pin-iLink-Adapter-Cable-/300448018068?pt=LH_DefaultDomain_0&hash=item45f418ee94)

---

### Post by mips on 2011-10-11
I'm gonna say no ways in hell will that cable work as I see no electronics that do protocol conversion. I think you got scammed.

---

### Post by tigreped on 2011-10-11
> **mips said:**
> I'm gonna say no ways in hell will that cable work as I see no electronics that do protocol conversion. I think you got scammed.

Well, I understand a cable alone can't manage such protocols conversion. What I'm asking if there is any implementation on **software** that could read the usb port, access the ieee1394 firewire data through it and manage the communication between camcorder and computer.

Should I assume that it has not yet been tried out? Cause I'm sure it's not impossible. :c)

---

### Post by mips on 2011-10-11
> **tigreped said:**
> What I'm asking if there is any implementation on **software** that could read the usb port, access the ieee1394 firewire data through it and manage the communication between camcorder and computer.


I don't think so seeing the protocols are implemented in the hardware (chipset).

---

