---
title: "Single Boot on 2008 MacBook Air, EFI? BIOS Emulation? Best Way?"
date: 2014-11-22
forum: Apple Hardware Users
---

### Post by cb474 on 2014-11-22
I've been trying to set up Ubuntu 14.04 as the only system on a Original 2008 MacBook Air for a family member (since Apple in their kindness and generosity has thrown users of this device under the bus with no more software updates, even security updates--thanks Apple!). I am experienced with Linux as my main system on a ThinkPad, for years.

Anyway, it's confusing the options to boot in EFI mode or BIOS emulation mode, with a gpt partition scheme or msdos partition scheme. A lot of the guides out their for installing Ubuntu on Macs are pretty old and talk about EFI as experimental in Linux. But these days it's stable, isn't it?

I was able to run the Ubuntu installer (from the on the amd64+mac .iso) on the MacBook and have it install fine. It seems like it defaulted to installling in EFI mode (there's an efi partition). And basically it boots okay. But sometimes weird things happen at boot. It freezes and I have to power the system off and reboot. It acts glitchy and then boots into the Grub menu, rather than directly into Ubuntu, but then boots fine from there. Most of the time it boots fine, but occasionally I get thse glitchy things. Also, if I boot into the Mac bootloader, the hard drive does not show up as a system to boot from (although my bootable install USB shows up okay as an efi device).

I'm wondering if this odd booting behavior has to do with EFI and I'd be better off forcing the system to install on an msdos partition scheme and use BIOS emulation mode. I want to set up a system that's stable and not confusing for my linux novice family member.

What is the recommended way to install Ubuntu on a MacBook these days?

I'm also wondering, do I want the special amd64+mac .iso? I see other distros like Mint suggest the normal .iso is fine. What is different about the special mac .iso?

Thanks for any suggestions.

---

### Post by d4m1r on 2014-11-24
1) Defintely reinstall under msdos partition scheme and use BIOS emulation mode.

2) Use the regular 64 bit Ubuntu images.

Coming from someone who went through the same thing last year with a 2012 13" Macbook Pro. Got it running stably with no issues.

---

### Post by cb474 on 2014-11-24
Thanks d4m1r.

I want to use the LVM encryption option in the install. Do you know, if I create a msdos partition table first, do I need to then manually partition during the install to keep the partition table? It seemed like (at least with the Mac specific .iso) that the installer was perhaps recreating the gpt partition table, if I just went with the automatic LVM encryption option.

---

