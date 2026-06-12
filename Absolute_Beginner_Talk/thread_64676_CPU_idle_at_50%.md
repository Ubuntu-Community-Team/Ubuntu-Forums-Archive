---
title: "CPU idle at 50%"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by expendable on 2005-09-11
Hello all! I just ordered a new MS-1029 (AMD Turion MT-34 with 1 gig of RAM) and decided to install Ubuntu as the primary OS. Installation went fairly smooth but took a bit longer than on my current, two-year-old machine. After I started it up and opened the CPU monitor, I was noticing a constant usage of the CPU at 50%, and every time I opened a new program it would jump up to 100%. It was running quite slowly and causing my laptop to (over) heat. I checked the system processes and nothing apparent was causing such a dramatic rise in CPU usage (Xorg would occasionally jump to 10%). Anyhow, knowing that such usage was bad, I installed a trial version of XP x64 to make sure it was a hardware issue that I needed to address with the manufacturer. Everything started fine and the computer ran cooler and used minimal amounts of system resources.

As such, I can no longer address the issue via Ubuntu right now. I'd like to re-install Ubuntu, but I can't seem to figure out the problem and don't want to damage the system trying to find out. Is it a hardware conflict of some sort?

Thanks in advance.

---

### Post by Nequeo on 2005-09-12
I run Ubuntu on an Athlon64 chip, but haven't seen this sort of problem before.

Do you mind if I ask: What process is causing using up your CPU cycles? (you can type 'top' in a terminal screen to get a nice display). Also, did you install the i386 or the AMD64 version of Ubuntu?

Cheers,

---

### Post by expendable on 2005-09-12
Well, since I formatted over, I can't anymore. But I did check when it was still up, and the main program running that was cuasing CPU usage was Xorg and it would rarely jump above 10%. I installed the i386 version.

---

### Post by expendable on 2005-09-12
Any help?

---

### Post by chrisgibbs on 2005-10-15
the i386 is for intel chips.

You need to install the version for amd64. Then see what happens.

---

### Post by WhiteHorse on 2006-05-03
I have the exact same box and installed the amd-64 bit Ubuntu with all defaults. Other than a few sound and DMA issues it uses the CPU the same as windows XP Pro x64. I chose these options at the boot menu while installing:

boot: linux noapic nolapic

The only time the CPU heats up is when I compile something and the system automatically increases the CPU speed and the fan kicks on. Dmesg logs the scalarate CPU changes too. :P

---

