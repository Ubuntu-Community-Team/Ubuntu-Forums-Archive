---
title: "Trouble installing drivers for Nvidia 8600GS"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by elaleks10 on 2008-01-24
I have just started using Ubuntu 7.10 and I would love to be able to use all the eye candy features that Beryl, Compiz can offer, but I ran into problems when searching for drivers for my graphics card. 

I have being surfing the internet trying to find a solution but to no avail. I have an Nvidia GeForce 8600M GS graphics card and as far as my understanding goes there are no proprietary drivers in Ubuntu 7.10 for this card. 

So my question is, is there any easy way I can manually install the card? or just a way around it so that I can enjoy all the nice visual effects of Beryl...

Again Im quite new at this, yet anxious to learn. Any help is greatly appreciated. :)

---

### Post by warrior24 on 2008-01-24
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this will work get the one that says envy new and save it to desktop and then click on it, thats about it

---

### Post by rhc on 2008-01-24
There is a program called Envy.
Try that.

---

### Post by elaleks10 on 2008-01-24
Thank you for the very quick responses. I will definitely be looking into Envy as soon as I get home. I'll keep you guys updated :)

---

### Post by elaleks10 on 2008-01-26
I went ahead and tried Envy New but that didn't work...it says there was an error in the installation process and the log says this:

Envy - Version 0.9.10
ENVY ERROR: Nvidia card not found

Is there something (maybe run command) that im supposed to do before I run envy? I noticed on Envy theres another option for installing the drivers manually. Is that what I should resort to? and if so, which version am I to install? I downloaded the drivers for my graphics card which are supported by version ( 100.14.09 ) from the nvidia website. This version doesn't appear under the manual installation of envy...Does that mean Envy will not work for me?

Now that I have downloaded the drivers from the nvidia website, is there an easy way to install my drivers myself, or should i stick to Envy?

---

### Post by PmDematagoda on 2008-01-26
Post the output of:-
```
lspci
```

---

### Post by Bill_58503 on 2008-01-26
> **elaleks10 said:**
> I have just started using Ubuntu 7.10 and I would love to be able to use all the eye candy features that Beryl, Compiz can offer, but I ran into problems when searching for drivers for my graphics card. 

I have being surfing the internet trying to find a solution but to no avail. I have an Nvidia GeForce 8600M GS graphics card and as far as my understanding goes there are no proprietary drivers in Ubuntu 7.10 for this card. 

So my question is, is there any easy way I can manually install the card? or just a way around it so that I can enjoy all the nice visual effects of Beryl...

Again Im quite new at this, yet anxious to learn. Any help is greatly appreciated. :)
I have a Geforce 8600 GT and Gutsy recognized at the first boot? I got a message in the tray about enabling restricted drivers, I said ok rebooted and it has worked great since.

 I thought all the geforce 8 series cards used the same driver??

---

### Post by Bill_58503 on 2008-01-26
Oops I missed that you have a (m)obile card. 

Can't help you there.

---

### Post by elaleks10 on 2008-01-27
Bill I do have the (m) mobile card, but thank you for trying to help...

PmDematagoda.. This is what I get after running lspci

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware Inc Unknown device 0790 (rev 02)
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:02.0 USB Controller: VMware Inc Unknown device 0770


By the way, as I looked through the Log, I realized I completely forgot to mention that Im running Ubuntu as a virtual machine through VMWare as you may notice, Im sorry I didn't include this before 

Hope this helps

---

### Post by swoll1980 on 2008-01-27
I just anwerd this in my last post this is the best soulution for an up to date driver
[http://ubuntuforums.org/showthread.php?t=679424](http://ubuntuforums.org/showthread.php?t=679424)

---

### Post by NullHead on 2008-01-27
I'm not sure that vmware can run compiz or beryl. You would need to install it on you're actual hdd to get those features.

---

### Post by swoll1980 on 2008-01-27
vmware uses a virtual 8mb video card and is incapable of creating 3d effects

---

### Post by elaleks10 on 2008-01-27
Is it the same for all versions of Vmware? I've got VmWare workstation 6.0...
If this is the case then I will go ahead and set up dual boot...

Thank you for everyone who helped out...ubuntu community is indeed the best and i will definitely keep using and learning ubuntu...

---

### Post by swoll1980 on 2008-01-27
Yeah theres no way, not yet at least to get 3d effects in a VM

---

