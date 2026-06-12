---
title: "broke my osx/windows7 bootcamp"
date: 2010-09-02
forum: Apple Hardware Users
---

### Post by davidag1 on 2010-09-02
Hi I'm running an imac 1.86mhz and 1gig ram with Snow leopard and Win7 on Bootcamp. I installed unbuntu 10.4 and the mac and win partitions don't show in grub.*Also I tried to boot from CD by holding down the option key. It just goes strait to grub. 
Thanks for your help

---

### Post by vgrisham on 2010-09-04
As far as I am aware (and I'm new at this) if you want to include Linux with your booting options, you'll need to install rEFIt in OS X. Bootcamp will only deal with two operating systems, and it has no clue what Linux is.

Unfortunately, you're probably going to have to restore OS X from Time Machine or reinstall OS X from scratch. If you've used a tool like Clonezilla, you should be able to restore your drive's partitions. 

Once you've got that down, you should follow a guide to install triple booting. I followed [Lifehacker's]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required"), though I now see that there is [one]("http://ubuntuforums.org/showthread.php?t=1564943") right in our forum.

Whichever road you follow, one thing you have to be careful of (and something that caused me a bit of grief) is to make sure you install the ubuntu bootloader on the same drive as Lucid (and don't go near the Maverick beta yet as it's not playing nicely with Macbooks at the moment).

---

