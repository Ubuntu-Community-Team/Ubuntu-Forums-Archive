---
title: "Crazy situation with Ubuntu"
date: 2020-02-06
forum: Apple Hardware Users
---

### Post by notimetocry on 2020-02-06
What im trying to achieve: Install Ubuntu on an external usb-3 SSD, install Cuda, Nvidia RTX drivers, Tensorflow, Pytorch and use my eGPU (RTX 2080S) for ML and CV.

The hardware: MacBook Pro 2018 (MacBookPro15,1), 6 Core I7, 32gb Ram running macOS Catalina.

Possible workarounds:
Not working = Using macOS: Tensorflow on macOS doesn't support GPUs, no RTX drivers from Nvidia
Not working = Live SSD with persistence: not viable since I cant install Nvidia drivers etc
Not working = VMWare, Virtualbox, Parallels, QEMU etc: Doesn't support Thunderbolt passthrough


Can anyone tell me what this error means and how I can install it? SecureBoot is disabled, install form external source is enabled, csrutil status is disabled.
This is insane. 

Error = "the 'grub-efi-amd64-signed' package failed to install into /target/"

---

### Post by CelticWarrior on 2020-02-06
Have you at least one ESP (EFI System Partition) available? If there's one in the internal drive the installer should use that by default but you may create another in the external SSD and change the UEFI settings to boot from it whenever you want to boot Ubuntu. But you may need to copy from one to another.

---

### Post by oldrocker99 on 2020-02-06
This happened with me, trying to install and getting the same GRUB error.

The reason is that I had been trying to install in UEFI mode. When Legacy mode is used, everything will progress swimmingly.

---

### Post by notimetocry on 2020-02-06
macOS has its internal EFI partition. I can boot to the Ubuntu installation USB and I created the /efi, /boot, /home and /swap partitions. It then starts installing and towards the end it has the fatal error with that message.
Im not sure what to do

---

### Post by notimetocry on 2020-02-06
How do I switch to that mode?

---

### Post by CelticWarrior on 2020-02-06
> **notimetocry said:**
> How do I switch to that mode?

You don't in a Mac. That (usually bad) advice is applicable to PCs only.

Sorry to say @oldrocker99, you need an update yourself. Very soon Legacy mode won't be available in new systems because it's a relic from the time when OSes without UEFI support were still supported but that time ended in 2014 when XP was axed. UEFI mode also has great advantages for dual or multi-booting.

---

### Post by wildmanne39 on 2020-02-06
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by notimetocry on 2020-02-06
Any advice how I can install Ubuntu? I really need to move past this. Im losing so much time with something that should be so easy and fast.
Please help me. Im pretty much lost.

---

### Post by notimetocry on 2020-02-06
Well what a pity that there aren't any replies but THANK GOD its in the right sub-forum. What would we do without that. Its not like you are killing conversations by moving threads around pointlessly. You are the hero we don't deserve, doing gods work.
Thank you sir!

---

### Post by notimetocry on 2020-02-06
> **wildmanne39 said:**
> *Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*


Really pointless moving my thread to a near dead sub-forum. The grub error is not necessary a MacBook issue and all you do by moving it is just filtering out loads of experienced people that might had an answer. Pointless and pedantic exercise like sorting pencils by size and color.

Absurd.

---

