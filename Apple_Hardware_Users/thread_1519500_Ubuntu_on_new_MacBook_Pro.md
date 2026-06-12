---
title: "Ubuntu on new MacBook Pro"
date: 2010-06-28
forum: Apple Hardware Users
---

### Post by blueridgedog on 2010-06-28
I am a full time Ubuntu user and am due a new laptop.  I was thinking of a 13" MacBook Pro for two reasons, one it would give me a chance to learn the Mac OS and second the hardware is impressive.

Two questions then, can I get Ubuntu working 100% on this unit (all hardware usable) and will I be able to dual boot it between Ubuntu and the Mac OS?

If I need to for work, could I even triple boot this into an MS OS?  I assume that it is nothing more than a PC at this point since they have switched to intel chips.

---

### Post by Helios747 on 2010-06-28
That is correct. You can triple boot. Ever since Apple went Intel, their computers are now basically PCs with an EFI and a GPT/MBR hybrid partitioning scheme.

There are a few limitations though.

The way the GPT/MBR hybrid works, you can have a maximum of 4 primary partitions readable by Ubuntu or Windows on the drive. No logical or extended partitions. (as extended partitions do not exist in GPT)

Second, No USB booting (easily), this bugs the crap out of a lot of people, but it just simply isn't possible with the irritating way Apple coded the firmware. There IS a workaround however, you can add an entry into grub to chainload the USB device. (grub legacy works best for this)

Third, (And this is applied to you with the mac you are looking at) the Intel/NVIDIA hybrid isn't completely supported in Ubuntu, YET.

AFAIK Ubuntu only sees the NVIDIA chip, it won't switch to the Intel GPU to save power. Again, YET.

I don't know TOO much about the 3rd bit because I own a MacBook 5,1. I'm only going off of what I read about the hybrid graphics setup.


P.S.: See this thread about the NVIDIA/Intel GPU hybrid situation. [http://ubuntuforums.org/showthread.php?t=1453607]("http://ubuntuforums.org/showthread.php?t=1453607")

---

### Post by blueridgedog on 2010-06-28
Thanks.

I know nothing about Macs, but think the hardware and design is fantastic and it looks like a great notebook, with as much battery time as my current netbook.  I have found my iPhone is a great product and think that I should look at other Apple products.

Is this guide worth following?

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

---

### Post by Helios747 on 2010-06-28
That is an excellent guide. I would also refer to this page when setting up ubuntu.

[https://help.ubuntu.com/community/MacBook6-1/Lucid](https://help.ubuntu.com/community/MacBook6-1/Lucid)


Ubuntu isn't perfect OotB on Macs, but after following the directions on that page you should be good to go :p

P.S.: When you get to the part about the wireless, you want the Broadcom STA driver in restricted drivers, NOT the firmware extractor.

P.P.S: You probably won't need to manually set the fan speed, it works fine on my mac.

---

### Post by buntuLo on 2010-06-28
macosx is booted via an EFI boot loader, while Apple implemented an alternative bios-emulation boot method for mswin.
with linux, you can actually choose the easy way and boot with bios-emulation, using the default grub-pc installed with ubuntu; or you can install yourself and configure grub-efi to boot in EFI mode.

afaik, EFI or BIOS will not make important differences on that hardware: the actual 13'' MacBookPro is the updated version of the 13'' MacBook 5.1, and i believe they both have only one graphic card.
instead, on models with two graphics adapters, Apple made impossible to use the powersaving graphics card in bios-emulation mode, so that the laptop has considerably longer battery life in macosx than mswin. on those models (i believe only 15'' and 17'', just check their specs), EFI booting may be desirable.

ciao, Lo.

---

### Post by Helios747 on 2010-06-28
It does make a difference. GRUB2's implementation of EFI is half baked, at best. No GPU acceleration if you EFI boot.

---

### Post by blueridgedog on 2010-08-11
I did order the new MacBook Pro 7,1...it has shipped, so I will soon be able to add comments.

Note that based on this:

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

You can now install and run most items from the daily build.

---

### Post by benced on 2010-08-12
okay, i got a macbook pro 7,1 13 inch a couple or so weeks ago and have followed all the instructions on the wiki page, 

hibernate still does not seem to work and my firefox is constantly stalling (possibly due to the slow disk drive read/write issue)

scrolling is not ideal (for me anyway) as kinetic scrolling hasn't been coded yet,
And the touchpad detection isn't fully optimised yet for the touchpad on it i don't think,

I am looking forward to being able to do some fancy multitouch stuff on ubuntu though,

however everything else on the wiki that i've tried works (only not tried firewire and monitor out yet)

using macOSX mainly just now until some of these issues are resolved but having fun hacking away on linux on the odd occasion until it's fully operational

---

### Post by anupamdas on 2010-10-27
Any more news on this? I just ordered a 13" Macbook pro, anyone tried Maverick on it yet or should I go for Lucid? Cheers.

---

### Post by blueridgedog on 2010-10-27
Lucid worked on mine, but an update killed the sound ([http://ubuntuforums.org/showthread.php?t=1577878](http://ubuntuforums.org/showthread.php?t=1577878)).  I have not been able to resole the sound issue, but may try a clean install of 10.10.

---

