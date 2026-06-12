---
title: "Need help with screen freezes / dual Nvidia GPU / MacBook Pro 15'' Mid 2009"
date: 2022-05-03
forum: Apple Hardware Users
---

### Post by mhs2508 on 2022-05-03
Hi there,

I need some help here with my MacBook Pro 15'' Mid 2009, 8 GB RAM, Dual Nvidia GPU (9400M / 9600 GT). A few days ago I installed the latest Ubuntu Budgie 22.04 on my old MacBook Pro. The installation went smoothly (using a USB stick). I'm pretty sure it is an EFI installation (I read something that it might be important to install as BIOS mode, although I have no clue what's the difference), because upon startup it says "EFI".

My problem is the following: After firing up the GUI (Budgie, lightdm) and starting some apps (Firefox, Libre Office), the screen freezes. Sometimes after quite a while it recovers, but mostly the screen hangs and doesn't come to live again. 

After reading some articles in the net I discovered that the problem might be the dual GPUs combined with the nouveau drivers. And I believe it to be true, because after logging in to the console (my Mac is set to multi-user.target for the moment), there is always an error message on the prompt:

```
[   57.158707] nouveau 0000:**02:00.0**: up: init failed, -2
[   57.158789] nouveau 0000:**02:00.0**: bcp: init failed, -2
```

After some research I found this command and executed it:

```
**lspci -nnk | grep -i "VGA\|'Kern'\|3D\|Display" -A2 **
**02:00.0** VGA compatible controller [0300]: NVIDIA Corporation G96CM [**GeForce 9600M GT**] [10de:0647] (rev a1)
    Subsystem: Apple Inc. G96CM [GeForce 9600M GT] [106b:00bc]
    Kernel driver in use: nouveau
--
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation C79 [GeForce 9400M] [10de:0863] (rev b1)
    Subsystem: Apple Inc. C79 [GeForce 9400M] [106b:00bb]
    Kernel driver in use: nouveau

```

I'm no expert, but it seems to me, that nouveau has problems with the Nvidia 9600M GT GPU (**"02:00.0"**)

I found this article ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) and installed nvidia-340, but the drivers doesn't seem to be active.

Can you help me here? What do I have to do to fix this?

Thanks in advance :-)

---

### Post by mhs2508 on 2022-05-10
Really? No one has an idea? :-(

---

