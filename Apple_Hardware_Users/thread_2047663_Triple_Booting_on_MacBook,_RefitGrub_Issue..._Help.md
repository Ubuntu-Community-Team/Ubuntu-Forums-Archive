---
title: "Triple Booting on MacBook, Refit/Grub Issue... Help!"
date: 2012-08-25
forum: Apple Hardware Users
---

### Post by pinchez on 2012-08-25
I've got a Mid 2010 13" MacBook Pro with 500GB M4 SSD, 8GB memory and have made the following partitions - Mountain Lion = 200GB, Windows 7 = 200GB and Ubuntu = 100GB.

I installed Mountain Lion first then the latest version of refit followed by Windows 7 and all worked perfect. I then installed the latest desktop release of Ubuntu 12.04.1 LTS x64 which again installed absolutely fine.

However on reboot I was presented with the Grub menu and the only thing that worked from this was the Ubuntu installation. I then rebooted holding the Apple option key down and this bought up the refit menu and since this it as always bought up the refit menu when powering on (no longer need to hold option key down) which is what I want 

But...
I can boot Mountain Lion and Windows 7 fine through refit but when I select what should be Linux, it boots in to grub and although I can then boot from there in to Linux/Ubuntu I would rather get rid of Grub completely and boot straight in to Ubuntu from refit via the nice penguin icon I've had previously!

Can anyone tell me how I can completely remove grub and just use refit to select between the 3 OS's? I don't mind reformatting the Linux partition and starting again but I really don't want to touch either the Apple or windows partition.

---

### Post by aventrax on 2012-08-27
Booting linux directly from refit is impossible because refit is not a boot loader but a boot manager. With a custom kernel > 3.3.x you could use the STUB loader and boot the linux directly but is an experimental feature at the moment there are no distribution using it.

To boot on REFIT as default choice you have to bless it, use the bless command in OSX and bless refit executable. Something like..:

bless --folder=/..... --file=/EFI/refit/....efi --setBoot


M

---

