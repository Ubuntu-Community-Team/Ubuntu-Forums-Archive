---
title: "Bentley shop manual under Wine?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-06-03
For those familliar with Bentley manuals, they are the factory manuals that the dealer uses. I need to get this working, but it only runs under Windows. I figured I'd try running it in Wine, it seemed to install OK, but launching it gave me an error......."iphpapi.dll not found". I googled it and found that file and stuck it in the folder. Now I get an error "component eztoolslib2.dll or one of it's dependencies not correctly registered: a file is missing or invalid" I can't find this file on the net. It also seems to be dependant on Internet explorer, which I dont think installed. Any ideas?

---

### Post by Inxsible on 2007-06-03
Specific programs like the one you are trying to use are hardly ever made for any other platforms than the one they are intended for.

I dont know much about the software, but I am afraid, you will have to use Windows to use that software. Do you have a dual boot ?

---

### Post by lazyart on 2007-06-03
If you have another windows machine on your network you should be able to install it on there and view it from your Ubuntu machine using remote desktop and/or rdesktop.

---

### Post by blazini on 2007-06-03
> **Inxsible said:**
> Specific programs like the one you are trying to use are hardly ever made for any other platforms than the one they are intended for.

I dont know much about the software, but I am afraid, you will have to use Windows to use that software. Do you have a dual boot ?

Right after I made this post I started thinking of this. I thought about it before, but most of the dual boot turorials suggest installing Windows XP first, before Ubuntu. The reason I am running Ubunto is cuz when I built this PC (3 weeks ago) I didn't wanna shell out the money for a fresh copy of Windows, especially since I really don't like windows that much. Reguardless of the minor compatibility issues here and there, I like Ubuntu, and I'll keep it. 

Anyway, I have Ubuntu installed on a new 500gb SATA HD. I also have a 120gb IDE HD installed on this machine. The IDE HD was a drive I used to store files on my old PC, there's no OS on it, and it's still formatted with NTFS, I just stuck it in there when I put this machine together. 

What would be the best way to stick XP on the IDE HD? I don't really plan on using XP except for Apps like the one mentioned here, so I don't want it getting in the way of my Ubuntu install. I'll probably use a ....not so legitimate copy, since I have very limited use for it.

---

### Post by Inxsible on 2007-06-03
You can install XP on the machine easily. The only problem will be that the XP installation will overwrite the MBR. Grub will be gone and and will be replaced by NTLDR. So you might have to install the grub again. Its something that you would want to avoid, but its not that difficult, if you follow a good guide -- of which there are many :)

---

### Post by Surkow on 2007-06-03
I would suggest to install Windows in VMWARE or QEMU (virtual machines) instead of actually installing Windows.

---

### Post by blazini on 2007-06-03
> **Surkow said:**
> I would suggest to install Windows in VMWARE or QEMU (virtual machines) instead of actually installing Windows.

Do I really need to go through that tho? Can't I just install Windows on The IDE drive, and change the boot order in my bios when I want to use it?

---

### Post by Surkow on 2007-06-09
> **blazini said:**
> Do I really need to go through that tho? Can't I just install Windows on The IDE drive, and change the boot order in my bios when I want to use it?

I can assure you...using a virtual machine is way more easy than actually installing Windows and solve all the problems it causes (like having to recover GRUB).

---

