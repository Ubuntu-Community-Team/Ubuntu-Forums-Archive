---
title: "Recover my original boot information"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by majkball on 2007-03-01
I installed Ubuntu 6.10 right now on my removable USB-HD. The reason I did this was so that I could plug in my USB-HD and choose to boot from it through the BIOS whenever I would like to use Ubuntu.

But in other situations I want my computer to boot as usual to my Windows XP partitions...

Now I just noticed that during the Ubuntu installation something was changed on mmy internal harddrive... making it load GRUB, and then everything crashes unless my USB-HD is connected at startup. I want to change this to my original boot that was at my internal HD, how do I do this?

Secondly... what will I need to add to my USB-HD to make it bootable when I want to boot from it.

---

### Post by majkball on 2007-03-01
I managed to recover my MBR on my internal HD.

But now I have an Ubuntu install on my USB-HD without any boot record. Does anyone know how I can write a Boot Record to my USB-HD so that I can boot from it?

---

### Post by dannyboy79 on 2007-03-01
you can look for the guide that tells you how to install grub onto your usb drive that contains ubuntu and you'll be set. just boot to a live cd, then follow the guides, they are out there. or you could just download the super grub disk and boot to that and then that will install grub onto your ubuntu disk.

---

