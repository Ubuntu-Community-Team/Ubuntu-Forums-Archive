---
title: "Live-CD trouble with ps/2 mouse and keyboard"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Lutger on 2006-05-20
Hi, yesterday I tried the 5.10 Breeze Badger live-cd, coming from windows as a complete linux-newbie. Sorry if this has been posted before, I couldn't find an answer: 
As the thread title indicates, my mouse and keyboard didn't work. On-board ethernet was also not detected, however my primary concern is the mouse and keyboard since, you know, it's hard to anything without them.
I have also tried mandriva and knoppix live-cd, with those the keyboard did work however the mouse gave the same issues.

I have tried googling for some hours, and found some threads or info where people bring up similar issues, but this didn't enlighten me as to what the problem is and what is involved in a solution.

I would like to learn more about linux, maybe install a dual-boot with windows XP but since I can't get these live-cd's to work I have some doubts. 

Is this a known issue, does it have something to do with the BIOS, the kernel or the hardware? Does anyone know how much trouble a solution will be and would he or she be so kind as to point me in the direction of answers?
Thank you.

---

### Post by jorn on 2006-05-20
Browsing this forum regularly, I don't mean it's a main issue to have trouble with mouse or keyboard. What causes it, I don't know. What hardware do you use?
Usb mouse and keyboard?

---

### Post by S{yndrom}e on 2006-05-20
hmm i had the same problem with my keyboard. Try reconnecting your mouse and keyboard after the Linux distro is booted up. If it works after that, you need to reconfigure your current keyboard and mouse to be ther default option.

---

### Post by Lutger on 2006-05-20
I have a logitech ps/2 keyboard (the standard cheap media keyboard), and a trust optical ps/2 mouse.
Motherboard: abit ax8. (VIA K8T890 chipset)
Processor: AMD64 3200.

I have a (rotten) serial mouse somewhere, maybe I'll try that. Haven't tried any older distro's / distro's with a different kernel yet. I hope to get into some form of linux without buying new hardware to see what's it like in there:D

---

### Post by S{yndrom}e on 2006-05-20
ahh you run an amd64 machine. Did you download the correct version of the Ubuntu Live CD? There is specific option for amd machines that want to run ubuntu.

---

### Post by Lutger on 2006-05-20
I have tried both the intel x86 and amd64 live-cd, same symptons. btw, is the amd64 ubuntu a fully 64-bit OS?

Some symptons: the mouse light (I don't remember the correct term) dies as soon as ubuntu is booted. Then when i boot up XP it remains dead, I have to plug it in and out and reboot to get it working again. Under ubuntu, switching mouse and keyboard makes the keyboard behave as the mouse (ubuntu thinks it's a mouse). Don't ask me why I did this. ](*,) 

Reconnecting the mouse and keyboard didn't help. The mouse lights up and dies again. 

Thanks for your suggestions. Is there a live-cd of a previous version of Ubuntu and do you think that this may be worth trying?

---

### Post by S{yndrom}e on 2006-05-20
I guess u could try with the prievous cd. Do you have any alternative mouse/keyboard to plug into your machine? If you do try plugging it in and see if  it works with the new mouse or keyboard.

EDIT: Wait i am asuuming your mouse isn't USB. Try enter BIOS and disabling the USB mouse function if it is enabled. and vice versa if you use an USB mouse.

---

