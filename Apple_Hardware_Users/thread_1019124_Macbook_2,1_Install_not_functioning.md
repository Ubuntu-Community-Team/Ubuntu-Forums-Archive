---
title: "Macbook 2,1 Install not functioning?"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by WalrusWarfare on 2008-12-22
Hello all, I've recently decided to make the swap to Ubuntu from my Mac OS. The reason being I hate wasting HDD space on installing windows just to run games/necessary programs. In any case, I made my Ubuntu disc and am currently posting this from the "Try before you install" selection.

I have a few questions/problems.
1. I installed Ubuntu earlier today. Before I installed it, I ran DBAN and erased any remnants of Mac's OS. After installing Ubuntu, I rebooted my computer and I was met with the "OS not found" screen my Mac produces when I have no OS. Basically I had a flashing folder with a question mark on it. I found this strange, as I'd gone through the whole installation.
I'm currently running the installer again in the background. When it brought up the partitioner, it listed my HDD as solely devoted to sdc1/2 or whatever. Ubuntu was not on the HDD at all. The installer says it is partitioning my HDD to contain these scripts/files/whatever in a minimal amount and giving me mostly Ubuntu. Is this going to work?
2. I have a built-in iSight camera. Does this work with Ubuntu?
3. How in the hell do I right-click using the 2,1 Macbook? I've found users saying f12 or the apple key, but none of these work for me.
4. Is there any way for me to reconfigure the keyboard to function using the apple key instead of control. I loved my Mac's keyboard layout and set up and it saddens me to lose it.
5. Is there a way to do 2-finger-scroll on the touch pad like with Macs? I find the side-of-the-pad-scrolling to be frustrating since my track pad is so large.

Those are my main concerns. I appreciate any help you can offer and apologize if I'm reposting something you folks have answered hundreds of times.

---

### Post by hyperboloid on 2008-12-22
You have been bitten by the [Ubuntu installer bug]("http://ubuntuforums.org/showthread.php?t=767677"), which wipes out the MBR on your disk, rendering it impossible to boot after a successful install. Happened to me, too. 

You can fix it quickly by using a rEFIt rescue CD to re-sync the MBR on your disk. See [https://help.ubuntu.com/community/Intel_iMac#NOTE ON INSTALLATION BUG]("https://help.ubuntu.com/community/Intel_iMac#NOTE ON INSTALLATION BUG") for details. You need to burn a rEFIt CD using another computer, just google rEFIt to find the download. 

Good luck.

---

### Post by WalrusWarfare on 2008-12-22
Much appreciated, Hyperboloid. I was just reading the other threads about this. I'm sitting in an airport, so I'll have to do this later when I have a more stable internet connection and more time.
Thanks again

---

### Post by hyperboloid on 2008-12-22
> **WalrusWarfare said:**
> Much appreciated, Hyperboloid. I was just reading the other threads about this. I'm sitting in an airport, so I'll have to do this later when I have a more stable internet connection and more time.
Thanks again

You might check the Wiki documentation for answers to your other questions; see [https://help.ubuntu.com/community/MacBook2-1/Hardy]("https://help.ubuntu.com/community/MacBook2-1/Hardy"). Beware that some information may be for 8.04 Hardy, so be careful.

To right click I just hold down two fingers on the trackpad and click; middle click is three fingers plus click. Dunno if that works on your hardware, though.

---

### Post by cyberdork33 on 2008-12-24
Just a question, why don't you dual-boot?

---

