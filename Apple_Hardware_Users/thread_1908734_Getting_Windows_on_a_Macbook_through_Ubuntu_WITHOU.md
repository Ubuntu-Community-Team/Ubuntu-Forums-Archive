---
title: "Getting Windows on a Macbook through Ubuntu WITHOUT Mac OS."
date: 2012-01-14
forum: Apple Hardware Users
---

### Post by Alexand3rS on 2012-01-14
Hi, I've got (what I think is) a late 2006 Macbook that runs Ubuntu 11.10 just fine. When I received the laptop I immediately got rid of OS X because I simply cannot stand it. I think Ubuntu is a great OS but I'd love to be able to use Windows on this laptop too.

When looking up instructions on how to get Windows on a Mac, I usually find instructions on how to tripleboot OS X, Windows, and Ubuntu, or how to get Windows on a Mac through OS X.

What I'm asking, is if there's a way to get Windows on my Macbook only using Ubuntu, as I don't have OS X at all.

Thanks.

---

### Post by Linforcer on 2012-01-14
I guess the main issue is the need for rEFIt to facilitate the doube-boot... I'm fuzzy on the details, but you want to look into creating a (small) hfs+ partition for rEFIt to live in, you want to check the rEFIt documentation for that. I believe there is also an efi grub, though I have not investigated it and don't know if it will help facilitate mac os-less dualboot on the mac.

Afterward, it should be as simple as partitioning the drive and installing Windows. Since I think the custom EFI on the mac still wants GUID partition table you should probably still use the MAC OS X install disc's Disk utility to create the partitions (if you have not already)  and format them using the installation process, though a gparted live cd might do the trick as well. 

I THINK an altenative to all of this is installing regular GRUB, and using the option key at boot to boot your "windows", which will in reality boot GRUB and this will let you choose between Windows and Linux (much like on most other machines) I have no experience with this way of doing it.

---

### Post by Alexand3rS on 2012-01-14
Thanks, I'll look into that.

Also, I don't have the OS X DVD.

---

### Post by Linforcer on 2012-01-14
Actually I had a quick look in the documentation, and you might even want "Installing on the EFI System Partition".

Though one way or another it looks like you will temporarily need OS X to set it up, regardless... You may want to contact the refit people, though the closest thing to a forum appears to be feature requests.


I never realized what a pain this was. I guess there aren't many people who would get a mac without running Mac OS on it (hell, the only reason I have one it to triple-boot and that building a hackintosh is a lot of work)

good luck

---

### Post by Q-collective on 2012-01-15
You should be able to just create a new NTFS partition via [GParted](http://gparted.sourceforge.net/).

But it might not work that easily as Apple locked down their hardware pretty good. The easiest thing to do then is probably to purchase [Snow Leopard](http://store.apple.com/us/product/MC573Z/A), install it and then to create a Windows partition via Boot Camp.

Why on Earth did you remove OS X. That is a little beyond me. It's not like it's eating your whole hard drive.

---

### Post by Alexand3rS on 2012-01-18
> **Q-collective said:**
> You should be able to just create a new NTFS partition via [GParted](http://gparted.sourceforge.net/).

But it might not work that easily as Apple locked down their hardware pretty good. The easiest thing to do then is probably to purchase [Snow Leopard](http://store.apple.com/us/product/MC573Z/A), install it and then to create a Windows partition via Boot Camp.

Why on Earth did you remove OS X. That is a little beyond me. It's not like it's eating your whole hard drive.

With OS X and Ubuntu, the Macbook would boot straight into OS X on startup. I found getting rid of OS X to be simpler than remembering to hold the Apple key on startup each time.

I also bought the Macbook second-hand, which is why I don't have an OS X DVD or whatever it comes on. But thanks, I'll look into that.

---

