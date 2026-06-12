---
title: "UPDATE: Booting Ubuntu in pure EFI/GPT"
date: 2007-05-07
forum: Apple Intel Users
---

### Post by benanzo on 2007-05-07
It's not ready yet.

As many of you know, I have been toying with the idea of getting Feisty to boot in pure EFI/GPT environment in order to do away with the need to install GRUB/LILO to the MBR and use rEFIt to manage a multi-boot setup.

This would benefit anyone who wants to boot [OS X] or [Ubuntu] or [OS X + Ubuntu] or [OS X + Ubuntu + 64bit Vista] (since there's no chance of 32bit Windows ever being booted in EFI without BIOS emulation.)

After some tinkering I managed to start Ubuntu from an EFI shell which I booted to from a USB stick (I don't recommend this headache.)  However, ELILO isn't very granular about the boot parameters that can be set and I was only able to get Ubuntu to boot with 800x600 resolution using the vesa driver.  Apparently the prop. ATI driver can get it's info from EFI, but I haven't got a MacBook Pro, so that wasn't tested.  At this point the Intel graphics chips require a BIOS (which is emulated on Macs) to get it's info and properly provide X what it wants in order to get any acceleration (or a higher res.)  This is also a problem for those of us using 915resolution to patch the BIOS in order to get native resolution, in my case 1280x800.  No chance.

So, at this point it is perfectly *possible* to boot ubuntu with ELILO in EFI, but you're left with a pretty unusable system.  I contacted the maintainer for elilo-installer who said that the efi code is compiled into i386 kernel which makes it inaccessible to the current edition of efibootmgr which looks for it to be modular.  Therefore, efibootmgr is useless to set EFI boot params right now.

I'll keep trying periodically and let you all know.

---

### Post by mustang on 2007-05-07
Sweet, thanks for taking the time to experiment and reporting back to us.

One question

> 
This would benefit anyone who wants to boot [OS X] or [Ubuntu] or [OS X + Ubuntu] or [OS X + Ubuntu + 64bit Vista] (since there's no chance of 32bit Windows ever being booted in EFI without BIOS emulation.)


I don't mean to trivialize your effort but how exactly would we benefit from direct EFI booting versus BIOS emulation? I could only see the bootup being tightened up by a couple of seconds and even, who reboots these days with suspend working almost seamlessly?

---

### Post by ronocdh on 2007-05-07
> **mustang said:**
> ... who reboots these days **with suspend working almost seamlessly**?
This from the guy who spent weeks on end troubleshooting the suspend on the firstgen MacBooks? ;)

---

### Post by benanzo on 2007-05-07
I understand you're reasoning, and believe me, I have seriously questioned my motivation.  However, I think this is important for the long-term so we can get out from under the emulated BIOS workaround.  I really just want native support and I want Ubuntu to *feel* like it belongs.  If you're not using rEFIt, you can definitely feel the workaround-ness of it considering GRUB takes ~10-15 seconds to boot from power on.


> who reboots these days with suspend working almost seamlessly?

Oh BTW, did you get the suspend issues figured out?

---

### Post by mustang on 2007-05-08
> **ronocdh said:**
> This from the guy who spent weeks on end troubleshooting the suspend on the firstgen MacBooks? ;)

Yes yes :) I take a lot of pride in showing off my finally suspending macbook :)

> 
I understand you're reasoning, and believe me, I have seriously questioned my motivation. However, I think this is important for the long-term so we can get out from under the emulated BIOS workaround. I really just want native support and I want Ubuntu to *feel* like it belongs. If you're not using rEFIt, you can definitely feel the workaround-ness of it considering GRUB takes ~10-15 seconds to boot from power on.


I see what you mean. 

> 
Oh BTW, did you get the suspend issues figured out?


Yeah I finally did :) Party is over at my thread, everyone's invited :) 
Thanks for offering your help btw in that thread of yours. Turned out I was completely off on the permissions issue.

---

### Post by thully on 2007-05-08
Just FYI, you don't need rEFIt to do an install anymore with Feisty + latest version of Boot Camp.
Feisty takes care of creating a proper GPT/MBR hybrid, and Boot Camp will boot a Feisty partition with GRUB.  I have a dual-boot going right now, and it worked as seamlessly as installing Windows in Boot Camp.  Granted, BIOS emulation is still used, but there is no 15-second wait and I can easily choose between the two OSes on startup - though Linux is labeled "Windows".

I'm not sure if this would hold if I blew away OS X during partitioning, but I will say that it has operated pretty seamlessly for me as it stands now with 40GB for OS X/20GB for Ubuntu.

---

### Post by benanzo on 2007-05-08
I think I'm having an EFI/MBR problem.  looking into it.

---

### Post by ronocdh on 2007-05-08
> **thully said:**
> Just FYI, you don't need rEFIt to do an install anymore with Feisty + latest version of Boot Camp.
Feisty takes care of creating a proper GPT/MBR hybrid, and Boot Camp will boot a Feisty partition with GRUB.  I have a dual-boot going right now, and it worked as seamlessly as installing Windows in Boot Camp.  Granted, BIOS emulation is still used, but there is no 15-second wait and I can easily choose between the two OSes on startup - though Linux is labeled "Windows".

I'm not sure if this would hold if I blew away OS X during partitioning, but I will say that it has operated pretty seamlessly for me as it stands now with 40GB for OS X/20GB for Ubuntu.
Glad to hear Feisty is now capable enough to handle the dual boot without rEFIt, but how would your system handle triple booting? I believe the Boot Camp utility still only allows the creation of a single additional partition, so you'd still have to partition using the terminal (or iPartition or whatever else suits you). But on the boot screen, would there be OS X and then two versions of "Windows"? Just curious; I installed rEFIt when I was just dual booting Windows XP and OS X (in other words, nothing Boot Camp couldn't handle by itself) because it's just so much prettier! =)

---

### Post by thully on 2007-05-08
Boot Camp still doesn't handle triple-boots - it only works for a dual-boot setup.
To install such a setup with it, you just use it as if you are running a Windows/OS X dual boot, and then delete the Windows partition and create Linux partitions during the Feisty install.

---

### Post by ronocdh on 2007-05-08
> **thully said:**
> Boot Camp still doesn't handle triple-boots - it only works for a dual-boot setup.
To install such a setup with it, you just use it as if you are running a Windows/OS X dual boot, and then delete the Windows partition and create Linux partitions during the Feisty install.
Thanks. For me the genuine triple boot setup using rEFIt is still the better option. Plus rEFIt is *way* prettier. ;)

---

### Post by Jonne on 2007-05-08
> **thully said:**
> Boot Camp still doesn't handle triple-boots - it only works for a dual-boot setup.
To install such a setup with it, you just use it as if you are running a Windows/OS X dual boot, and then delete the Windows partition and create Linux partitions during the Feisty install.
This confuses me a bit: you need to *delete* your Windows partition? How is it still a triple boot then? I only count OS X and Ubuntu then...  Do you mean resize the ntfs partition with gparted?

---

### Post by benanzo on 2007-05-08
It works the same.  I am working on a guide that uses only the MBR as the partition map.  No GPT whatsoever.  The benefit to this is that you can create an extended partition (which GPT doesn't support) containing as many logical partitions as you want.  You could therefore have OS X, Windows and Linux installed on the three primary partitions and then create an extended partition containing as many logical parititions as you want for swap or share or backups or whatever.

GPT supports up to 128 primary partitions which is utterly useless if you want to install Windows or Ubuntu since they require BIOS emulation/MBR which only supports 4 partitions total (whether primary or extended, though extended can contain an infinite number of logical parititons.)

rEFIt just says that it can't find a GPT partition table (because there isn't one, it's an MBR disk.)  But it still boots all the OSs the same, with the pretty menu.

---

### Post by Jonne on 2007-05-08
I currently have an iMac at work, and I run Windows on it (and there's also a OS X partition that I hardly use, but I won't blow it away). So if I stick the Feisty liveCD in it and install Ubuntu as if it's a regular dual boot (shrink the ntfs partition, create an ext3 partition, install to ext3 partition) , everything should work fine? no messing with rEFIT and such?

---

### Post by benanzo on 2007-05-08
right, the Ubuntu partition editor (GParted) is GPT-aware, which means that it will automatically sync the GPT and the MBR, or it should.)  So when you power on, hold option and select Windows, you'll boot to Ubuntu.  I would still recommend using rEFIt.  It's trivial to install and uninstall.  It will negate the need to hold option for the OS selector.  You can configure which OS is the default boot, and it has the proper "Linux" label rather than saying "Windows."

---

### Post by AWerner32 on 2007-05-09
This is kinda unrelated but when i installed ubuntu it destroyed the MBR of my vista partition so now that won't boot is there anyway to restore the mbr to it

---

### Post by Jonne on 2007-05-10
I installed rEFIt. I was reluctant at first because i thought rEFIt was just an ugly hack, but I guess i was wrong. It's well-tested and looks pretty.

When my ubuntu cd's arrive through shipit I'll install Ubuntu on a new partition.

---

### Post by AWerner32 on 2007-05-28
I had a tripple boot with no refit, I installed the ubuntu partition between the mac and windows with the grub only on the ubuntu partition with the windows boot loader, so i can choose either to boot to mac or to the grub and from grub i can boot to either windows or ubuntu. Its kinda tedious and i reinstalled refit but it did work without it.

---

### Post by AWerner32 on 2007-05-28
and on the note of destroying the MBR, if you make sure you install the grub only on the linux partition it should eliminate that problem. at the last stage of the install click advanced and deleted (hd0) then hit ok, then click it again and it should say /dev, you then need to put the partition that you are installing linux on, mine for example is /dev/sda3. that should save you mbr

---

