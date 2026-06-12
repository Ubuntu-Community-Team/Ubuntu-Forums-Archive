---
title: "Lockup: I/O and IRQ Conflicts galore"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Adelus on 2006-03-22
Since I reinstalled Ubuntu to dual boot on my system, neither WinXP or Ubuntu will run very long before locking up, usually while using the internet or browsing any files. I've found a few I/O errors and IRQ conflicts, all dealing with the PCI bus and my Nvidia card.

I can't put all the details in as I'm sure this thing will conk out again soon, so I'll edit it again later. I'd love to get this thing running fine again, so I would appreciate anything you can tell me with the limited information I was able to provide.

I can't force IRQ from the mobo, and when I tried to reinstall my Nvidia drivers the system crashed.

Thanks for any help.

EDIT: IRQ problems are gone. Some info from system information I was able to get:

I/O Port 0x00000000-0x00000CF7	PCI bus
I/O Port 0x00000000-0x00000CF7	Direct memory access controller
	
I/O Port 0x000003C0-0x000003DF	PCI standard PCI-to-PCI bridge
I/O Port 0x000003C0-0x000003DF	NVIDIA GeForce FX 5200
	
Memory Address 0xA0000-0xBFFFF	PCI bus
Memory Address 0xA0000-0xBFFFF	PCI standard PCI-to-PCI bridge
Memory Address 0xA0000-0xBFFFF	NVIDIA GeForce FX 5200
	
I/O Port 0x000003B0-0x000003BB	PCI standard PCI-to-PCI bridge
I/O Port 0x000003B0-0x000003BB	NVIDIA GeForce FX 5200

---

### Post by Adelus on 2006-03-23
Bump. I've looked around and haven't found an answer yet.

New info: I can mount and view files on my windows partition from Ubuntu, but when I try to move files over from the windows drive to the FAT32 partition on my Ubuntu drive, I get an I/O error and Ubuntu stops it from occuring. When I do the same when running Windows, the system simply crashes and reboots as soon as the command starts.

---

### Post by Kapre on 2006-03-23
Adelus - I've had similar problem when I started on Hoary (will all of a sudden stop in XP or Ubuntu [Gnome] - and I have to reset my PC everytime this happens). I don't know if we will have the same result, but what I did was re-installed to the latest (at that time Breezy RC1) and problem dissappeared. It most probably was due to some programs (not 100% sure it's from the IRQs) running. BTW, did you do a kernel upgrade (did you rebuild your own kernel?) as this might have caused it too. For your XP, back it up and try defragging it (to fix/move some errors).

K

---

### Post by Adelus on 2006-03-25
I'm feeling it's a hardware problem. I backed up all my important Windows data to my iPod and reinstalled Windows, no go. Now I just have Ubuntu, which while more stable, is also a victim.

When the comp starts up, it says that the Ethernet Controller and the USB controller are both using IRQ 12 on the boot screen. My mobo (ASRock) has no IRQ forcing and the USB and Ethernet are both on the mobo itself (The only card in there is the video card, and I don't know how to check for I/O and IRQ conflicts in Ubuntu yet).

---

### Post by Adelus on 2006-03-25
You can close this thread now. The problem was my video card. I swapped it out with my old one and it works fine now.

---

