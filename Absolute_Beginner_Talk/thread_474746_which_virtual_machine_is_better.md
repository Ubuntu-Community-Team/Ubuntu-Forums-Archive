---
title: "which virtual machine is better"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Dai777 on 2007-06-15
Hi Folks looking for some advice on which virtual machine to use VMWare or VirtualBox
Which one use more memory to run ubuntu?
which one runs ubuntu faster?

I know the virtual machine may not make a difference to the way Ubuntu runs but you never know?
At the moment I'm running VMWare Dapper and using 160mb memeory
and it's slowish compared to windows ( I know this is coz it's in a virtual machine).

Any ideas of how to speed up Ubuntu in a virtaul machine.

---

### Post by Bachstelze on 2007-06-15
vmware for me, it is far less buggy than virtualbox. virtualbox is "more free" (as in freedom) than vmware but it's not as mature yet.

---

### Post by shelzmike on 2007-06-15
I have to agree with you there. VMWare is much better. I had a few issues at first, but they were by far because of me. Now that I have familiarized myself with it, it is so simple to use and have not had too many (if any now that I think about it) problems with it.

---

### Post by Golyadkin on 2007-06-15
I absolutely love virtualbox, it is very nice to use (new version 1.40 out just recently) and runs like a dream. Easier to use than VMware in my opinion.

And how much RAM it uses it something you control yourself, both in Virtualbox as in VMware. You chose with a slider how much of your computers RAM you allow the virtual machine to use. I suggest you don't put it to more than half of your physical memory size.

---

### Post by lazyart on 2007-06-15
tried both, like both.  For some reason I couldnt get virtual box to work on my AMD64 install though it worked fine in 32 bit, but it works fine for others.

Currently I am hosting a blog from a Dapper install in VMware.  Cool stuff.

---

### Post by Golyadkin on 2007-06-16
I have to add, I am running Virtualbox inside of Ubuntu (AMD64) to virtualize Windows. Not the other way around, which you seem to want to do.

---

### Post by Golyadkin on 2007-06-16
This is my Virtualbox, it has every Windows program I ever need :) 
[img]http://www.android42.net/got/VirtualBox.png[/img]

---

### Post by starcraft.man on 2007-06-16
> **Dai777 said:**
> Hi Folks looking for some advice on which virtual machine to use VMWare or VirtualBox
Which one use more memory to run ubuntu?
which one runs ubuntu faster?

I know the virtual machine may not make a difference to the way Ubuntu runs but you never know?
At the moment I'm running VMWare Dapper and using 160mb memeory
and it's slowish compared to windows ( I know this is coz it's in a virtual machine).

Any ideas of how to speed up Ubuntu in a virtaul machine.

I vote Virtual Box, I agree its not completely as good as VMware Workstation, but it does everything it needs to and does it cleanly and free. I don't think either uses more or less memory, it just depends how much you allocate the VM itself.

Any OS you have in a VM should get at least 256 MB ram, 160 is low. I find 512 to be ideal on my computer. Apart from giving it more ram, there isn't much to do to speed it up...

---

### Post by Error1312 on 2007-06-16
Virtual box does a perfect job for me. Maybe VMWare has a bit higher performance but it's more of a hassle to set it up in my opinion.

---

### Post by Nekiruhs on 2007-06-16
Hassle to setup? I found VMWare easier to do than VirtualBox. I managed to setup Ubustu in like 10 minutes (Minus the actual install)

---

### Post by starcraft.man on 2007-06-16
I've used both extensively (VMware workstation and Virtual Box binary version). Neither takes any longer in my experience to completely configure than the other. Once you know what to do its really a non-issue, it shouldn't be relevant at all to which VM product to use IMO.

---

### Post by the8thstar on 2007-06-17
I have three partitions on my disk:

1. WinXP
2. the recovery partition for WinXP
3. U7.04

Does VMWare or VirtualBox allow you to use the recovery partition as the source to create the virtual file? If yes, how could this be done?

---

### Post by Midahed on 2007-06-18
I tried VirtualBox on my Ubuntu 7.04 Feisty 64-bit host virtualising Windows 2000.  The VirtualBox installation went OK, but I had problems installing Windows 2000 because there seem to be problems getting it to partition and format the virtual disk.  I got over that by using an XP CD to partition and format before going back to the Windows 2000 installation.  However, I found VirtualBox a bit flaky.  I couldn't use the guest O/S for more than 15 minutes without having some sort of lock-up or crash.

Installing VMware was a dream, as was installing the Windows 2000 guest.  So far I've seen no lock-ups or odd behaviour at all.

Judging purely on the time it took to boot into the guest O/S, I'd say there is little difference between the two in terms of performance, but VMware is the product of choice for me.  I may try VirtualBox again sometime in the future when it's a bit more mature.

Mike

---

### Post by shelzmike on 2007-06-18
> **Nekiruhs said:**
> Hassle to setup? I found VMWare easier to do than VirtualBox. I managed to setup Ubustu in like 10 minutes (Minus the actual install)

I agree here 100%. I think the bottom line here is that they are both pretty darn similar in their capability and functionality. No matter which one you use, it will take a little tooling around  to become fluent. So, taking the neutral route...do either, become familiar with it and you will never miss anything from the other. 

I found that after about 3 virtual machine installs with VMWARE,  I was able to quickly install any subsequent  VMs very quicly...like Nekiruhs said in 10 minutes (although, if you use someting like QEMU to set up the VMDK files, then it takes even less time). Bottom line - just pick one and dive in.

---

### Post by shelzmike on 2007-06-18
> **the8thstar said:**
> I have three partitions on my disk:

1. WinXP
2. the recovery partition for WinXP
3. U7.04

Does VMWare or VirtualBox allow you to use the recovery partition as the source to create the virtual file? If yes, how could this be done?


Good Question. Off the cuff and completely unresearched, I would say no only because the only way I am familiar with setting up a virtual machine is to have an ISO or alternate image that will allow booting and installation. Now, that being said, I have not had much experience with Recovery Partitions, except with the DELL recovery partition for windows. If this is what you are referring to, then it may be possible, but you will have to dig into how you can extract the image from the parition. If you can do that, then you should be able to. Alternately, if the image is a Ghost of some sort, what you may be able to do is install a fresh windows OS as the Virtual Machine, extract the Ghost Image from the recovery partition and then share it somewhere so that you can update the Guest Windows OS with this Ghost. 


Again, the disclaimer here is that I am merely brainstorming  here and have no experience doing this. 

Can you specify what your recovery partition is? Is it something that  came with the computer, or is it one you made yourself?

---

