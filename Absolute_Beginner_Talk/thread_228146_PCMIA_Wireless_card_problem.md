---
title: "PCMIA Wireless card problem"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Yserbius on 2006-08-02
I have a Marvell Liberatis wifi card (PCMIA) that works fine with Windows. There are currently no Linux drivers for it so I used ndiswrapper. Following the instructions from the online help, everything seemed to work fine until [HTML]<code>sudo modprobe ndiswrapper</code>[/HTML] which gave me an error [HTML]<code>Module ndiswrapper not installed</code>[/HTML]. Whats wrong and how can I fix this? Oh yea and the ndgtk said that hardware and software were properly installed.
On a related note I usually use Verizon Mobile Office with my LG vx3300 to connect. Anyone know of a Linux port for this? Or at least a driver so I can use it as a modem?

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-22
these comands is useful and i use it to install my usb senao adapter

ndiswrapper -i filename.inf
ndiswrapper -m
ndiswrapper -l

---

