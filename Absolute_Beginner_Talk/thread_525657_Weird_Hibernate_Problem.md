---
title: "Weird Hibernate Problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by fifth_rune on 2007-08-14
Yesterday I decided to finally rid myself of my Windows dual boot and go strictly Ubuntu.  I noticed however that my swap partition seemed to be in the wrong place (in my extended partition, which I was not expecting it to be).  So I decide to delete the swap as well and recreate it in another part of the drive.  After that the swap was undetected and my hibernate wouldn't work (yeah, I pretty much shot myself in the foot).  However, with some effort I restored the swap back to where it used to be and reactivated it (swapon).  Now it hibernates but when I restart it the computer acts like I shut it down instead of hibernated.  So, this is weird because I know my hibernate CAN work unlike other people who have had trouble with it (I use Feisty, btw) but now I can't get it work anymore.  Any suggestions?

Thanks in advance for any help provided.

---

### Post by Midahed on 2007-08-14
I blundered into this bug report the other day.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)

As you recreated swap (and you might be using UUIDs, as you're running Feisty), the UUID will have changed.  If you read all the comments in this bug report, you'll see that the swap partition UUID appears in /etc/initramfs-tools/conf.d/resume

You may have to edit that entry to match the new UUID (or switch to using more friendly partition references like /dev/hda2, or whatever your swap is) and then do...

sudo update-initramfs -u

Mike

---

### Post by Hospadar on 2007-08-14
The problem is that when you changed that partition, grub (and probably some other things) are still pointing to where it used to be (a partition which no longer exists) and I would bet that changing it away and back now probably some things are set correctly but others are not.

I think your best bet here would be to reinstall with the partition settings you want right off the bat.  

I believe the way hibernation works is that it save critical ram elements to swap so they may be reloaded upon resume.  Now if your swap isn't mounting correctly at startup time whatever got saved to swap would not load, hence it would behave as a normal shutdown/startup.  

There may be a way to fix this, but I can't imagine it would be easier than a reinstall.

If you have a lot of stuff configured already and want to save time from redoing it, copy all the configuration files and directories in your home directory (the hidden ones that start with a ".") and copy them onto your new machine after you reinstall.

---

### Post by fifth_rune on 2007-08-14
> **Midahed said:**
> I blundered into this bug report the other day.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)

As you recreated swap (and you might be using UUIDs, as you're running Feisty), the UUID will have changed.  If you read all the comments in this bug report, you'll see that the swap partition UUID appears in /etc/initramfs-tools/conf.d/resume

You may have to edit that entry to match the new UUID (or switch to using more friendly partition references like /dev/hda2, or whatever your swap is) and then do...

sudo update-initramfs -u

Mike

Ok, I don't know wtf you got but doing it your way just crashed my system.  I could not even boot without a kernel panic.  I would NOT recommend that solution you proposed and I was finally able to get my system working again.  Also, ironically, I was able to do what you intended and rewrite the file to my swap but it still didn't fix my hibernate.  Thanks for the suggestion, but seriously that was scary.

---

### Post by Midahed on 2007-08-14
I'm really sorry about that. :(

I had a similar problem a day or two ago with hibernate and following the recommendations in the discussion around that bug fixed it just fine.

If you got a kernel panic I should imagine that the rebuild of initrd didn't work properly.  You should be able to recover from that quite easily though, because the old initrd image should still be available on your system.

Mike

---

