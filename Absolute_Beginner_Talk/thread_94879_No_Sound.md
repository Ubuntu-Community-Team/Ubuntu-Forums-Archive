---
title: "No Sound?"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-11-25
I just installed Ubuntu 5.10 on my laptop (a gateway 3550GZ) and i have absolutely no sound....i was just wondering if their is a driver missing or how i find it out? It's a factory laptop (meaning it was built by a company not me). I've opened the sound panel and it allows me to increase all sounds to max, (CD and master, ect...), just to make sure.

but when i go to System --> prefs --> sound and i go to play a sound i press the button but hear no sound, same w/ playing a cd in sound juicer.

sorry if this is a very common topic, but it just something i would like to know. 

thx mates,
cheers,
ad

---

### Post by matthewv on 2005-11-25
You get no sound at all. What happens when you run alsamixer?? Do you see your sound card name and levels?? If not, run lspci, and post the entry for your sound card here.

---

### Post by adduds on 2005-11-26
I don't think i have alsamixer, under System --> prefs --> sound 

General Tab: Default sound card:
                                   Intel 82801db-ICH4

i ran lspci results:

adduds@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:07.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:07.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:02:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

sorry i've only had this unbutu for like 5.10 sorry if i'm breaking forum rules by posting that

thx cheers,
ad

---

### Post by pizzach on 2005-11-26
This is a non-thoughtful answer that might fix the problem but is totally shooting in the dark and works for me for no good reason.

For Hoary and Breezy I typically have to compile the Alsa driver and install it to get sound working.  Don't know why.  But it works for me.  My motherboard is different, but it is also made by intel.

[http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by adduds on 2005-11-26
[QUOTE=pizzach] My motherboard is different, but it is also made by intel. [/QUOTE]

ya? i'll try it out! :) this is laptop so :S:S, i should still be able to get it working tho i hope!

i'll keep ya updated

---

### Post by adduds on 2005-11-26
does it matter which alsa-drive i d/l?

---

### Post by adduds on 2005-11-26
i d/led alsa-driver-1.0.10.tar.bz2....i open the archive and get a folder

and i opened the install and i get madd listings to do stuff i do not undertsand how to do:confused:

---

### Post by adduds on 2005-11-26
[QUOTE=matthewv]You get no sound at all. What happens when you run alsamixer?? Do you see your sound card name and levels?? [/QUOTE]

isee my cardname 0: Intel 82801DB-ICH4(Alsa Mixer) or 1: Analog Devices AD1981b(OSS mixer)

and yes i see the levels

and when i go to play a cd like Nirvana - In Utero it starts playing but no sound comes out my speakers..... (or any sound at all for that matter)

concerned :( i need sound,
ty,
ad

---

### Post by gamerchick02 on 2005-11-26
Did you check and see if anything is muted in the mixer?  It sounds stupid, but that's the problem I had!  

Amy

---

### Post by adduds on 2005-11-27
all sounds are enabled and maxed

cheers,
ad

---

### Post by FaBi3ttO on 2005-12-01
[http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4]("http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4")
I've followed the steps and it worked for me.

Hope it helps.

---

### Post by adduds on 2005-12-01
Omfg Thank You Soooooo Much Buddy!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I Appreciate It!!!!!!!!!!!!!!!

---

### Post by adduds on 2005-12-01
5 bloody days!:KS :KS :KS :KS :KS :KS :KS :KS

---

