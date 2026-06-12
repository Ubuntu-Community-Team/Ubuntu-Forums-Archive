---
title: "Internal Card Reader"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by superintelligentape on 2007-06-26
I have an internal car reader inside my computer, but it wont read my SD card. I think it is because Ubuntu doesnt support it or have a driver for it..mycomp. is a compaq presario r3000, si if anyone can help then i would appreciate it. (BTW if you know a way to add files like music to a Pocket PC device tell me bc tats what im trying to do with the SD card)

---

### Post by superintelligentape on 2007-06-26
Anyone?

---

### Post by joe.turion64x2 on 2007-06-26
> **superintelligentape said:**
> Anyone?
I suggest you to search your device's name in this forum, and then in Google along with the word Ubuntu. Somebody should have accomplished what you are trying to do, if possible.

---

### Post by HarshReality on 2007-06-26
type lspci in terminal and see if the reader is there so you know the name of it or goto the manufacturers website and lookup your hardware I lay money its an ENE chipset reader and if that is thecase your out of luck like so many of us

---

### Post by joe.turion64x2 on 2007-06-26
> **HarshReality said:**
> type lspci in terminal and see if the reader is there so you know the name of it or goto the manufacturers website and lookup your hardware I lay money its an ENE chipset reader and if that is thecase your out of luck like so many of us
Another unlucky guy here, my laptop has an ENE card reader. Not big deal, just got an external USB reader and it reads even more card types.

Joe.

---

### Post by superintelligentape on 2007-06-27
Ok I typed in lspci into terminal but I cant find my card reader...any ideas? Or maybe I just dont know what to look for...

---

### Post by HarshReality on 2007-06-27
OK here is an example of the lspci output... of course this is for my laptop so your most likely will vary

```

02:01.0 **CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)**
	Subsystem: Hewlett-Packard Company: Unknown device 006a
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 50000000-51fff000 (prefetchable)
	Memory window 1: 54000000-55fff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001

02:01.1 **FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller**
	Subsystem: Hewlett-Packard Company: Unknown device 006a
	Flags: medium devsel, IRQ 10
	I/O ports at 3c00 [size=128]
	Capabilities: [a0] Power Management version 2

```

Hope this helps you recognize what your sorta looking for.....

---

### Post by dptxp on 2007-06-27
Those ENE guys..... When will they learn ?
Has Microsoft paid them for not writing a Linux Driver ?
I too am a victim of ENE.

---

### Post by Inxsible on 2007-06-27
you need to install the tifm packages. I had downloaded those packages from Ubuntu forums itself. I dont rbr the poster now :(  I am currently at work, but i can attach that package later tonight and then you can install it. 
 
Alternatively you can search the forums for the tifm pacakges.

---

### Post by zerobinary on 2007-06-27
my guess is ur sd card is so big 
since socard reader don't support 2 gb ones

---

### Post by superintelligentape on 2007-06-27
> **HarshReality said:**
> OK here is an example of the lspci output... of course this is for my laptop so your most likely will vary

```

02:01.0 **CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)**
	Subsystem: Hewlett-Packard Company: Unknown device 006a
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 50000000-51fff000 (prefetchable)
	Memory window 1: 54000000-55fff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001

02:01.1 **FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller**
	Subsystem: Hewlett-Packard Company: Unknown device 006a
	Flags: medium devsel, IRQ 10
	I/O ports at 3c00 [size=128]
	Capabilities: [a0] Power Management version 2

```

Hope this helps you recognize what your sorta looking for.....

Yea, all I needed to know is what the card reader was called ima look for it now thx!

---

### Post by superintelligentape on 2007-06-27
Ok my card reader is: Texas Instruments PCI1620 PC Card Controller (rev 01)
Doesn't say ENE anywhere so so far I'm happy, now for the google searching

---

### Post by Inxsible on 2007-06-27
Here it is..

try installing this package. Worked for me after i did

download this on the Desktop.

cd to the desktop and then  and then extract it. cd into the extracted folder.

```
sudo chmod +x install.sh
``` and then ```
sudo ./install.sh
```

there is also a readme file from where you can follow instructions if you prefer the gui way of doing it.

---

### Post by superintelligentape on 2007-06-27
I installed it the way in the readme...but still no dice I get nothing when I plug in my SD card

---

### Post by Inxsible on 2007-06-27
> **superintelligentape said:**
> I installed it the way in the readme...but still no dice I get nothing when I plug in my SD card
 
Dont know what the problem could be. Did you try a reboot ?
 
Mine worked after I installed the package.

---

### Post by superintelligentape on 2007-06-27
I just rebooted and still nothing..no notification when I put in the card and nothing shows up under computer...

---

### Post by macogw on 2007-06-27
You can try the setpci / sdhci hack.  Google for it, as I don't know how to do it.  If tifm doesn't work though, the developer should be notified.  That's version 0.8 which is the same one as is in Feisty's kernel after updates (2.6.20-16), so guys, you can stop suggesting my script as it's only needed on 2.6.20-15 since that one has version 0.7 which doesn't work.  If version 0.8 isn't working (as you said), then that's a bug upstream.

---

### Post by joe.turion64x2 on 2007-06-27
Is there a service to be enabled in Ubuntu for the reader to work? In some other Linux distros it is called PC/SC daemon I think.

---

### Post by superintelligentape on 2007-06-28
> **zerobinary said:**
> my guess is ur sd card is so big 
since socard reader don't support 2 gb ones

64mb is definetely not too big for any card reader out there

---

