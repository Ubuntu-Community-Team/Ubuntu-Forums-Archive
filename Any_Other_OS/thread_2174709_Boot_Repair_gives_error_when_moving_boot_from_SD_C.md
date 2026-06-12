---
title: "Boot Repair gives error when moving boot from SD Card to USB drive"
date: 2013-09-15
forum: Any Other OS
---

### Post by P_THE_AWESOME on 2013-09-15
Hi,
I recently installed XBMCbuntu onto an 8GB SDHC Card on my Samsung N310. I quickly realized that there is no option in the BIOS to boot to the SD Card. I know I can buy an USB SDHC card reader ad boot directly to it, but I would prefer not to. I have another operating system on the main HDD that I just want to leave alone. I make a liveusb of Linux Secure Live and tried moving the boot from the SD Card to another blank USB drive. I made a 1GB ext4 partition at the front of my USB drive in gParted. Then I ran Boot repair and it said an error has occured: [http://pastebin.ubuntu.com/6112588/](http://pastebin.ubuntu.com/6112588/). I found out how to do all of this on the Ubuntu Tutorial here: [BootPartition]("https://help.ubuntu.com/community/BootPartition"). Basically what I want to do is have a way to boot to the SD Card (XBMCbuntu) or my HDD. Do I need a bootloader or OS selector? I tried burning [Graphical Boot Manager]("http://gag.sourceforge.net/") with Unibooten on Windows, but every time I selected "Default" (the only option) it would just bring me back to the Unibooten screen. 

Any help is greatly appreciated!

P.S. This is my first time on this forum. Should this post be in a different Category?

---

### Post by oldfred on 2013-09-15
If BIOS does not let you boot SD card then other boot loaders will not chain load to boot that.

You can try this:
       Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by P_THE_AWESOME on 2013-09-15
Thanks for the quick reply! Do you mean the "Plop Boot Manager" or the "plopKexec"? If it's "Plop Boot Manager", which file should I download to burn to my USB Drive? While chain-booting is probably the best option, I thought that the BootPartition Tutorial might work in a similar way as moving the boot to a CD when the BIOS does not allow to boot from a USB drive. I was going to use a USB drive to boot to the SD Card.

---

### Post by P_THE_AWESOME on 2013-09-15
Never mind on which file. I just downloaded "Plop Boot Manager" (plpbt-5.0.14.zip) and I see the ISO. I will report my results after I try it.

---

### Post by P_THE_AWESOME on 2013-09-15
Well, I booted into it, but I couldn't tell what HDD was what. Could it be the problem that my SD Card is GPT and not MBR? I don't know which one is currently is, but would it make a difference to my BIOS?

---

### Post by P_THE_AWESOME on 2013-09-16
Well, I checked and it's MBR. I'm going to try what was said to do here: [http://ubuntuforums.org/showthread.php?t=986126&page=3&p=11915401#post11915401](http://ubuntuforums.org/showthread.php?t=986126&page=3&p=11915401#post11915401). This should do it. I'll respond when I try it.

---

