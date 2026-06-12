---
title: "Should I dual-boot with vista?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ZeldaFan on 2007-06-27
I already have set up my HP dv9000t laptop dual booting between Ubuntu Studio and Windows Vista. However, to tell the truth, I've almost never booted into Windows Vista since installing Ubuntu, and it pretty much just takes space on my hard drive. My primary use for Vista is my games, which I still want to have access to. But my games maybe take a total of at most 10 gb, while the whole vista partition takes up closer to 50 gb. It's basically a waste of HD space, so is there any alternative to dual booting where I can get the full functionality of my games, especially Vista-only games. I heard something about something called VirtualBox and VMware, but I am not too sure as to how they work. Also, I doubt Wine will work too well, because some games require online access as well.

---

### Post by joe.turion64x2 on 2007-06-27
> **ZeldaFan said:**
> I already have set up my HP dv9000t laptop dual booting between Ubuntu Studio and Windows Vista. However, to tell the truth, I've almost never booted into Windows Vista since installing Ubuntu, and it pretty much just takes space on my hard drive. My primary use for Vista is my games, which I still want to have access to. But my games maybe take a total of at most 10 gb, while the whole vista partition takes up closer to 50 gb. It's basically a waste of HD space, so is there any alternative to dual booting where I can get the full functionality of my games, especially Vista-only games. I heard something about something called VirtualBox and VMware, but I am not too sure as to how they work. Also, I doubt Wine will work too well, because some games require online access as well.
VirtualBox can be easily installed in your Ubuntu and, provided you've got enough RAM you can run a virtual machine inside containing the Windows of your choice. However this VirtualBox does not support directx. Perhaps VMware does but it is not free ware.

I've read something about a 'shrink filesystem' option in Vista, try loading your games so your Vista installation reaches a 'final' size and then you could use that option, freeing this way some of the space. Afterwards, you can create a new partition out of this space and mount it in your Ubuntu filesystem.

---

### Post by starcraft.man on 2007-06-27
> **ZeldaFan said:**
> I already have set up my HP dv9000t laptop dual booting between Ubuntu Studio and Windows Vista. However, to tell the truth, I've almost never booted into Windows Vista since installing Ubuntu, and it pretty much just takes space on my hard drive. My primary use for Vista is my games, which I still want to have access to. But my games maybe take a total of at most 10 gb, while the whole vista partition takes up closer to 50 gb. It's basically a waste of HD space, so is there any alternative to dual booting where I can get the full functionality of my games, especially Vista-only games. I heard something about something called VirtualBox and VMware, but I am not too sure as to how they work. Also, I doubt Wine will work too well, because some games require online access as well.

VMware and Virtual box are both Virtual Machine implementations. Neither allows for playing of games due to the simple fact that they emulate a generic low quality graphics card. The new parallels 3.0 for the Mac allows for playing games because I believe it was written in such a way as to take direct advantage of the physical hardware of the Mac. I have to assume this has to a certain degree compromised the security of Parallels as now they interact directly with hardware and the OS unhindered, but I guess since its on the Mac most people don't care.

To answer the question, No. Vista only games cannot be implemented in anything other than Vista. Cedega and Wine both allow games to run in Linux. Neither to my knowledge has implemented enough to be able to run Vista only games like Halo 2 (although something like Alky Leaf Studios has actually enabled it for XP, only Halo 2 though). The easiest solution to playing Vista games is to continue to have a Vista partition (and shrink it down, base install of Vista only requires around 25 GB i think, 40 should be more than enough including game), while there are other solutions that might eventually come close none will get you better performance than actually booting into Vista.

Thats it.

---

### Post by ZeldaFan on 2007-06-27
Well I have an external hard drive too. Right now, its formatted with the fat32 system. If I reformat it to ntfs or whatever is best, can I install my windows games or even Windows Vista entirely on the external hard drive. The external HD is 160 gb, and my laptops HD is 100 gb. So if I can install Windows onto my external HD, and enlarge my current ubuntu partition to the full size now available using gParted, that should work too, right? By the way, I've already shrunk my current Vista partition prior to installing ubuntu, so I guess I need to find out what is taking up so much space and uninstall it.

---

### Post by mtbsoft on 2007-06-28
This might sound a little long winded but should work, though I've only done it on XP Pro.

Get a copy of Virtual PC from MS (it's free) and install it into Vista.  Create a Virtual PC and (re)install your Vista inside it along with the games you want to play in order to try them out.

If they all work, download a copy of VMWare Player (also free) for Windows and try opening the VPC image with it (it can do it, but again I only have XP).

If that works, download a copy of VMWare Player for linux and install that in Ubuntu, copy ALL the VM/VPC files to Ubuntu and try to reopen with VMWare Player.

If all this works, you should be able to do what you want.

Before you blow away the Vista partition though, create a couple of "blank" VPCs and open them with VMWare, then archive them read-only somewhere.  Whenever you want to try something new without risking your existing Vista games VM, you can just copy them, run them up and play away.

I've used a similar VPC approach with Windows for some years now, but am in the process of moving all my necessary Windows images to VMWare and running them in Ubuntu.  I'll probably keep a small XP install for special purposes but rarely use it.

Hope this helps.

---

### Post by joe.turion64x2 on 2007-06-28
> **mtbsoft said:**
> This might sound a little long winded but should work, though I've only done it on XP Pro.

Get a copy of Virtual PC from MS (it's free) and install it into Vista.  Create a Virtual PC and (re)install your Vista inside it along with the games you want to play in order to try them out.

If they all work, download a copy of VMWare Player (also free) for Windows and try opening the VPC image with it (it can do it, but again I only have XP).

If that works, download a copy of VMWare Player for linux and install that in Ubuntu, copy ALL the VM/VPC files to Ubuntu and try to reopen with VMWare Player.

If all this works, you should be able to do what you want.

Before you blow away the Vista partition though, create a couple of "blank" VPCs and open them with VMWare, then archive them read-only somewhere.  Whenever you want to try something new without risking your existing Vista games VM, you can just copy them, run them up and play away.

I've used a similar VPC approach with Windows for some years now, but am in the process of moving all my necessary Windows images to VMWare and running them in Ubuntu.  I'll probably keep a small XP install for special purposes but rarely use it.

Hope this helps.
When I started reading your post I thought you were gonna suggest running Vista inside Virtual PC running on Windows, running in VMPlayer, running in Ubuntu. Quite a lot of virtual machines!

---

### Post by ZeldaFan on 2007-06-28
Wouldn't that cause the performance of my games to suffer significantly?

---

### Post by joe.turion64x2 on 2007-06-28
> **ZeldaFan said:**
> Wouldn't that cause the performance of my games to suffer significantly?
In fact, you would need to have a top of the line PC to do this. Only consider the RAM: Vista, 1GB; Ubuntu 256MB; plus the memory required by the VMplayer and that sucked by the game itself. At least you'll require 2GB of RAM to think you are playing.

Joe.

---

### Post by mtbsoft on 2007-06-28
> **joe.turion64x2 said:**
> When I started reading your post I thought you were gonna suggest running Vista inside Virtual PC running on Windows, running in VMPlayer, running in Ubuntu. Quite a lot of virtual machines!
Hee, hee. Mad I might be, crazy I ain't, though I did once try to run a VM inside a VM - they can't run an emulator in an emulator.  For my sins I use VS in my job to develop 'doze software and the PDA emulators won't run inside VM/VPC either for the same reasons. 

> **ZeldaFan said:**
> Wouldn't that cause the performance of my games to suffer significantly?
I guess it all depends on what games you are playing and how much resources they require plus what box you're running it on, though Ubuntu seems to take less resources as a host than 'doze does. You may find that they simply won't work in a VM at all, in which case you're stuck from square one.

I've been using VMs under XP for a few years to keep all my development environments clean and separate from one another, I recently moved to VMWare from VPC because VMware provides USB support and seemed faster - it was also a precursor to my Ubuntu move.  Yes, you do get a performance hit but my own experience is that VMWare's is less than VPC and VMWare over Ubuntu seems even better still.

At the end of the day, if you try it out and don't like it you can always just blow the VMs away and keep your current scenario - you only lose time that way.  Maybe you could simply use them to determine how much smaller you can make the Vista partition then shrink that down accordingly.

---

### Post by gruffy-06 on 2007-07-07
If you're using VMware, VirtualBox, or whatever, to run Vista inside a virtual machine, be careful. The [licence agreement for Windows Vista]("http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_36d0fe99-75e4-4875-8153-889cf5105718.pdf") clearly states for each edition, except Ultimate, that you cannot install the software into such machines. Otherwise you will have violated the law. If you have to virtualize, install Vista Ultimate or XP.

You could probably use NTFS compression on your files in Vista so they take up less space, but I don't recommend this. I experienced problems using this compression method on Vista and some apps failed to start. Backup first before using this.

---

### Post by mtbsoft on 2007-07-07
> **gruffy-06 said:**
> Otherwise you will have violated the law.
Strictly speaking, you have only violated the licence agreement, not the law.  It would be up to the courts to decide if you had broken any laws - Microsoft have not quite reached the point of defining the law as yet, such concepts as fair use have still to be fully tested in the courts.

---

### Post by Sef on 2007-07-07
If you are under warranty, you may void your warranty if you delete vista.    What happens if your hardware goes bad.  Best to check with the company first about the warranty specs.

---

