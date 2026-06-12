---
title: "ubuntu hangs.."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by banda on 2007-06-11
i've installed feisty on my comp.. it is also running perfectly even with beryl.. almost
the problem i am facing is that it hangs up from time to time (~2wice in an hour) which is driving me nuts. everything else works like a charm
(when it hangs i can't even move the mouse and does not respond to any keys)
it is not something that i do that triggers it .. sometimes it hangs just after bootin
and sometimes while i m using firefox
i am not sure if its beryl or nvidia drivers or firefox but i m sure that it does not have anything to do with system load as my cpu never sounds half as occupied as it does with windows(runs vista ok)

i dont know if its related but when i try to restart x by logging off then doin ctrl+alt+backspace it does not work instead it goes to the terminal and displays me some stuff and then ok against each of them and then just sits there.. ultimately i have to restart

please help me to fix this ..

my conf-
3.0 ghz p4
512ram
256mb - nvidia 7300le

---

### Post by wpshooter on 2007-06-11
Have you tried un-installing Beryl ?  See if the behavior goes away, if so, you have found the culprit.

---

### Post by Wardazo on 2007-06-11
Hi

Why don't you uninstall beryl or nvidia and see if the problem continues. On a fresh install I'd reckon they'd be the problem, but you'll only find out by uninstalling them.

Good luck.

Ward

---

### Post by banda on 2007-06-11
it has been hanging since before i installed beryl and i have also tried uninstaling it so i m pretty sure its not beryl, also all its animations etc are smooth and it does not hang as soon as i click something
i think its either firefox or nvidia cuz as much as i remember  the hanging started after i installed nvidia drivers
but i dont know how to check if thats true..

---

### Post by tdrusk on 2007-06-11
> **banda said:**
> i've installed feisty on my comp.. it is also running perfectly even with beryl.. almost
the problem i am facing is that it hangs up from time to time (~2wice in an hour) which is driving me nuts. everything else works like a charm
(when it hangs i can't even move the mouse and does not respond to any keys)
it is not something that i do that triggers it .. sometimes it hangs just after bootin
and sometimes while i m using firefox
i am not sure if its beryl or nvidia drivers or firefox but i m sure that it does not have anything to do with system load as my cpu never sounds half as occupied as it does with windows(runs vista ok)

i dont know if its related but when i try to restart x by logging off then doin ctrl+alt+backspace it does not work instead it goes to the terminal and displays me some stuff and then ok against each of them and then just sits there.. ultimately i have to restart

please help me to fix this ..

my conf-
3.0 ghz p4
512ram
256mb - nvidia 7300le

Are you using wireless? If so, post your wireless card. If you don't know what it is run
```
lspci
```

---

### Post by banda on 2007-06-11
its a wired connection... this is what that command gives me.. 
(thanx for trying to help.. )

> 00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 LE (rev a1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by tdrusk on 2007-06-11
> **banda said:**
> its a wired connection... this is what that command gives me.. 
(thanx for trying to help.. )

Okay just checking because the bcm43xx-fwcutter program was making me hang.

I guess check and make sure you are running the latest version of the NVIDIA drivers since that's what you think it is. Good luck.

---

### Post by banda on 2007-06-11
yup they are the new version (installed yesterday)
any1 else here please help.. (in the last 30 mins i have booted twice)

---

### Post by Tomosaur on 2007-06-11
Definately worth scrapping the nvidia driver to eliminate that from the possible causes. The problem with accessing virtual terminals (ctrl+alt+f1) also suggests some problem with the graphics.

---

### Post by banda on 2007-06-11
so i should just reinstall the drivers ??

---

### Post by lazyart on 2007-06-11
How many video cards do you have there?

---

### Post by banda on 2007-06-11
i don't have ati .. only nvidia 7300 le card!

---

### Post by Wardazo on 2007-06-11
Hi

"as i remember the hanging started after i installed nvidia drivers". 

I'd uninstall that driver if I were you.

Ward

---

