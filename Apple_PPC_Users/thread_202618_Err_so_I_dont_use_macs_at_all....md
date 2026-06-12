---
title: "Err so I dont use macs at all..."
date: 2006-06-23
forum: Apple PPC Users
---

### Post by ZaethDekar on 2006-06-23
but where I work we have two iBooks with 128 megs ram and has Mac OS9. I dont know how or what the speed is but I do know that my boss wants me to try installing ubuntu onto them.  Problem is, I really dont know how to do it.


I know I have to hold command + option + shift + del to have it boot from a CD but do I have to burn the CD in Mac OS? 

Sorry to be bothering you all but I am a mainly PC user.  Windows and Linux is what I normally use so the whole mac world is sort of a stranger to me. Any assistance is greatly appreciated as well!


Also I dont plan to keep Mac OS 9.0 on the Harddrive. I plan to do a full install for Ubuntu. Thanks again.

---

### Post by Rxke on 2006-06-23
there is a very big probability it won't work with only 128Mb. You should check first if your boss agrees on upgradeing the memory.

If you're familiar with PC's you can burn an ISO with it, of course it will have to be a .ppc version of ubuntu.

---

### Post by ZaethDekar on 2006-06-23
I have the ppc version and burned the ISO and yet it still wasnt wanting to install and I saw the requirment for the ram being 192 (i think that was it). I was wondering though if setting up a swap partion on the drive would help me get around this? Otherwise do earlier versions of Ubuntu work with less ram?

---

### Post by ZaethDekar on 2006-06-23
Also the reason why I ask if it has to be burned a certain way is because when I stuck the CD into the CD Drive on the iBook a window popped up asking if I wanted to initialize the CD and gave me a few choices. Then when I tried to initialize the CD it said the CD was locked. I even tried it with a brand new CD and still the error happened.

---

### Post by kadymae on 2006-06-23
Okay -- to find out the processor speed click on the apple and select "About this mac" and that will give you the processor speed.

You need to burn the CD as an ISO.  I've never burned an ISO in OS 9, so I can't help you there.  I have burned all of my 'buntu ISOs on a Windows machine, so if it is burnt correctly, it will boot and install on the mac.

However, given the 128mb of ram, I strongly suggest installing Xubuntu.

---

### Post by ZaethDekar on 2006-06-23
[QUOTE=kadymae]Okay -- to find out the processor speed click on the apple and select "About this mac" and that will give you the processor speed.

You need to burn the CD as an ISO.  I've never burned an ISO in OS 9, so I can't help you there.  I have burned all of my 'buntu ISOs on a Windows machine, so if it is burnt correctly, it will boot and install on the mac.

However, given the 128mb of ram, I strongly suggest installing Xubuntu.[/QUOTE]


I checked under 'About this mac' and nothing came up with processor speed. Told me the operating system, how much ram, then system ram used on the harddrive, largest unused block, and that was pretty much all of it.


Do I need to set the ISO as bootable or just keep it the ISO. Reason why I ask is because for FC2 I had to set it as bootable (but I was installing it on x86 instead of ppc architecture).

I am downloading xubuntu right now but I dont think it will be done by the time I go home, Ill deffinatly be here on monday though when I get back to work.

---

### Post by Ptero-4 on 2006-06-23
If the iBooks are square and white they have 500MHz or more.
To see the processor speed look for the "system profiler" app in the Apple Menu or in the "Applications (Mac OS 9)" folder in your HD.
I had an iBook and it ran gnome quite well with 128MB of RAM.
And the CD can be burned in PC's, look for the one that says for PowerPC, download it on your PC and burn it the way you burn your PC linux isos, then when you put the CD in the iBook press C before booting and it will boot off the CD.

---

### Post by ZaethDekar on 2006-06-25
Alright, thanks. It deffinatly isnt a square one.
Ill check when i get into work tomorrow and thank you for the information.


By the way I love your sig quote as well :-D

---

### Post by warp99 on 2006-06-25
[QUOTE=ZaethDekar]but where I work we have two iBooks with 128 megs ram and has Mac OS9. I dont know how or what the speed is but I do know that my boss wants me to try installing ubuntu onto them.  Problem is, I really dont know how to do it.


I know I have to hold command + option + shift + del to have it boot from a CD but do I have to burn the CD in Mac OS? 

Sorry to be bothering you all but I am a mainly PC user.  Windows and Linux is what I normally use so the whole mac world is sort of a stranger to me. Any assistance is greatly appreciated as well!


Also I dont plan to keep Mac OS 9.0 on the Harddrive. I plan to do a full install for Ubuntu. Thanks again.[/QUOTE]

6.06 LTS (Dapper) works well on my 300mhz G3 ibook, but it has 544mb of ram. With the additional ram and using the ReiserFS file system with notail and noatime options enabled ubuntu runs FASTER then OS 9.0. You can always upgade the ram very cheap to get a really good working linux laptop. :cool:

---

### Post by ZaethDekar on 2006-06-26
Well, no one will really be using the laptops besides maybe myself and one of my bosses as experimental work. If we decide to go with Ubuntu then we will most likly be getting better laptops. In the mean time though these two iBooks are the only extra's we have.

---

### Post by ZaethDekar on 2006-06-26
Okay so I tried burning the CD using a boot emulation of a 1.44 MB disk. Now i am going to try it without having an emulation of a boot disk on the cd so it will just be the ISO.

---

### Post by 3rdalbum on 2006-06-27
How misleading a little bit of knowledge can be...

Some PCs require boot floppy emulation due to the limitations of the ancient BIOS. Macs start up using OpenFirmware, which doesn't have those archaisms.

Because I have a background in Macs, I just assumed that the "floppy emulation" bit was handled by the distro itself. On my PC I just burn an ISO and it works, without me having to set any emulation thingy.

---

### Post by ZaethDekar on 2006-06-27
Ive tried the ISO, 1.44, no emulation but still bootable and I believe the one that worked was the no emulation but still bootable. The iso burned kept saying hte CD was locked while the 1.44 just gave me error after error and eventually locked the system up. When I have more time today I will re burn with different emulations and keep them market as for what is what and see what i find out. Main reason why I am documenting most all I do is for when I leave August 1st they will know how to get it setup on the iBook should they want to start from scratch.

---

### Post by 3rdalbum on 2006-06-28
Just a couple of things I forgot to mention:

To get the Mac to boot from CD, you hold down the 'c' key during startup.

Don't tell your burning software to make it "bootable". You're burning it on a PC, for use on a Mac - what's bootable on a PC isn't bootable on a Mac.

Set it for NO emulation, NOT bootable. Just the ISO itself. And don't open the ISO file before burning it.

---

