---
title: "About to setup dual boot"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Zralou on 2006-03-12
Hi Guys

My first post on this forum so hope y'all bear with me!!.

I currently am running Win98 and WinXP, I tried the 'live' version from CD of Ubuntu last night, and now want to install Ubuntu as well.

I want to keep Windows (for now!!!) until I get proficient with Linux, so I want to dual (triple) boot.  I tried this once before with Mandriva Linux, but endded up loosing my Win98 and having to format my HDD.
I've now installed 'System Commander' to handle the boot process, and now I need to know how to set up Ubuntu to work with SC.  How do I stop Linux bootloader from overwriting SC and still have SC add it to the boot list?

I've already partitioned the HDD into 3 sections for each OS.

Thanks
Sara Lou

---

### Post by aysiu on 2006-03-12
I'd say about 90% of the time, when you install Grub to the Master Boot Record (MBR), it'll automatically recognize Windows and add it to the boot menu.

If it *doesn't*, there's no need to reinstall Windows. You can usually add Windows manually to the boot menu, and if you want to restore Windows' boot loader, you can run the *fixmbr* command from the Windows installer CD.

Not using Ubuntu's Grub for a dual boot is just making the installation process more difficult for yourself.

Follow these steps to set up a dual boot:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

If you like videos, you could try following this tutorial, too:
[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu)

---

### Post by chuckyp on 2006-03-13
You may have an issue because you are using SC but just look at what grub wants to do before you commit the changes.

---

### Post by dermotti on 2006-03-13
System commander will boot linux no problem.

I think you can just tell it not to install grub during the install process.

---

