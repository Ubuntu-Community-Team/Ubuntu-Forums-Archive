---
title: "Video Drivers"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-03-10
Hi all,
How can I make sure I have the correct graphics card driver? My installation went fine but I seem to have some graphics problems. The screen resolution is stuck on 1024x786 and windows move clunkily round the screen. 
It's an oldish machine. 1.3ghz CPU, 512mb RAM, and the graphics card is, I think, a Voodoo 4/5 64mb card.
But when I had windows on this machine it used to easily run emulators like zsnes and gba. Under linux, these are unusably slow and jerky, with stuttering sound.

Thanks in advance.

---

### Post by Famicommie on 2007-03-10
Open up a terminal, and type:

```
lspci
```

And then display the output, please.

---

### Post by Fidelio on 2007-03-10
OK:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:08.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 4 / Voodoo 5 (rev 01)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

---

### Post by Fidelio on 2007-03-10
Anyone help me with this?
I read somewhere else that I should have something called glide. I found this on the synaptic update and put it on. It hasn't made any difference.
I really like Ubuntu so far, except for the sluggish performance. Any ideas?

---

### Post by c174 on 2007-03-10
(I don't know about this, but did you install libglide3? Try searching on"voodoo" in synaptic. Maybe you didn't pick the right package)

---

### Post by Famicommie on 2007-03-10
Could you please post the output of glxinfo ?

---

### Post by Fidelio on 2007-03-11
Actually, I reinstalled after I tried editting the conf file and it all went Pete Tong. I reinstalled with a new TFT monitor and the screen res is higher now. I guess ubuntu must detect something about the monitor.
Still sluggish on graphics though. I'm 50/50 whether to persevere with ubuntu or just run xp. I run xp on my music pc and I seem to have got away with instaliling and activating it on my home computer from the same disk.

---

