---
title: "How to install vista after ubuntu to dual boot ?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by dfk789 on 2007-04-06
Hello, i'm a beginner so this seemd the appropriate place to post.

So my problem, i'm currently running Feisty 64bit edition, and i'd like to get windows vista installed, but i'm unsure of how to go about doing this without having my ubuntu installation destroyed.... as i'd quite like to keep it. i've searched around a bit trying to find a how-to, couldn't find anything, most were about how to do it the other way around.

Anyone help me please ?

---

### Post by Bachstelze on 2007-04-06
I don't know Vista but assuming it behaves like XP, just create some empty diskpace to install it in and go on. It will overwrite GRUB with it's own bootloader but it is fairly easy to recover (search for it in the Wiki).

---

### Post by dfk789 on 2007-04-06
Hmmm, ok.  Not to sure though since, i've read about vista needing certain things to boot, and active partition stuff that confuses and worries me....

---

### Post by Doug11 on 2007-04-06
> **dfk789 said:**
> Hmmm, ok.  Not to sure though since, i've read about vista needing certain things to boot, and active partition stuff that confuses and worries me....

Don't worry. I dual boot Vista and Ubuntu and I didn't see any difference between Vista and XP. Once you install vista, you will more than likely have to reinstall grub. Here's and easy how-to.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Bachstelze on 2007-04-06
The 1.2 paragraph written by me, by the way ;)

---

### Post by sirhalos on 2007-04-06
They are correct with stating all you need to do is reinstall GRUB. Of course the easiest way would be install Windows Vista then install Ubuntu Linux so GRUB finds it.

To install GRUB again after you install Windows Vista insert the bootable CD of Ubuntu Linux and go to your command prompt and type as followed.

First change root to your hard drive. If your hard drive is mounted located where it is mounted at then issue the command chroot *destination of where your hard drive install of Ubuntu is located*

Next type sudo grub
Next set grub to now be the boot device by typing root (0,0) this is assuming you have one hard drive.
Next please go to your grub setup and edit it and add Windows Vista to it, will have examples in the file it is located in /boot/grub/grub.conf

Hope that helps

---

### Post by dfk789 on 2007-04-06
Ok then, that all sounds peachy :D. Seems simple enough to do, thank you peoples :)

---

