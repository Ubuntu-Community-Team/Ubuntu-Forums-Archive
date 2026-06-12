---
title: "rEFIt - Ubuntu Partition Not Detected"
date: 2009-10-30
forum: Apple Hardware Users
---

### Post by besweeet on 2009-10-30
So my original situation was that, with GRUB2 (1.97 beta or something like that), I could boot Ubuntu, but I couldn't boot Windows 7; it would just kick me back to GRUB. So I reinstalled the Windows 7 bootloader. I can't boot Ubuntu from it via EasyBCD because I guess none of the bootloaders support ext4.

So I installed rEFIt. Windows is detected, but my Linux partition isn't. I went to the partition tool thing from it and it said that nothing needed to be changed.

Any ideas? Would really like to easily be able to boot all three whenever I want.

---

### Post by leafw on 2009-10-30
I had a similar problem after installation: rEFIT would see the ubuntu partition, but I couldn't boot from it. So I booted from the CD (hold 'c' and reboot), then from the partition editor "gparted" I added the 'boot' flag to the root partition of ubuntu. For some reason that did the trick--even though the boot flag was already there.
Also make sure that the MBR is installed in your ubuntu root partition, but you say grub was fine, so no problem.

---

### Post by rifak on 2009-10-30
well if you installed windows after ubuntu, then you'll have to fix grub from live cd. here's a link for the new grub2 fix: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

if im mistaken with this, let me know

---

### Post by rifak on 2009-10-30
also, just so you know, refit will not recognize 9.10 as a linux os...it'll show the legacy-os icon (the gray diamond) but it WILL still boot into ubuntu when chosen. im not sure if it's grub2 or ext4 that refit doesn't recognize yet. but just to be clear, although it doesn't show a linux os, it still works

---

### Post by Andre_44 on 2009-11-19
I can confirm that it does indeed work with 9.10, but with a legacy icon, I've been trying to figure out how to fix that but haven't had any luck. does anyone have an idea?

---

### Post by besweeet on 2009-11-19
> **Andre_44 said:**
> I can confirm that it does indeed work with 9.10, but with a legacy icon, I've been trying to figure out how to fix that but haven't had any luck. does anyone have an idea?

I changed the images manually for my icons. They're located in /efi/refit/icons.

---

### Post by Nohtanhoj on 2009-11-20
> **ego-sum-deus said:**
> also, just so you know, refit will not recognize 9.10 as a linux os...it'll show the legacy-os icon (the gray diamond) but it WILL still boot into ubuntu when chosen. im not sure if it's grub2 or ext4 that refit doesn't recognize yet. but just to be clear, although it doesn't show a linux os, it still works

For some reason, mine does not... I can boot from the Linux partition if I hold down Option when the computer is in pre-boot stage (which is all well and good), but I've been wondering why rEFIt doesn't want to recognize Linux.

---

### Post by lexfati on 2009-12-02
@besweet:  Did you replace the legacy OS icon with the linux icon then, or was there a way to point the partition at the linux icon?  

On my macbook running Debian I lost the icon with the upgrade from Lenny to Squeeze, and updated from Grub2 1.96 to 1.97 beta.  I got my rEFIt linux icon back by removing 1.97 and reinstalling 1.96, but it didn't turn out to be easy.  If there's an easier (and therfore less risky way) I'm all for it.

---

### Post by Gfr0ehrer on 2010-01-19
This problem with icons is because refit cannot yet read grub2. I followed [this guide]("http://brettshaffer.com/blog/linux/downgrade-grub-2/") and downgraded grub2 to grub. Refit is now using the linux icon and all is well.
I am using ext3 partitions for my ubuntu 9.10 install, so you might want to research if grub can handle the newer ext4 if you used that partition type during install.

---

### Post by lexfati on 2010-01-20
> This problem with icons is because refit cannot yet read grub2
 
Or is it that refit can't read the *latest* GRUB2? I have my linux icon in refit using GRUB2 version 1.96.

---

### Post by linuxopjemac on 2010-01-20
I think that rEFIt can't read ext4.

---

### Post by lexfati on 2010-01-20
That could very well be, but even on ext3 refit didn't recognize the icon using v 1.97, but when I went back to version 1.96 I got my icon back.

---

### Post by linuxopjemac on 2010-01-20
ok, so you might be right too :)

---

### Post by kev0153 on 2010-02-05
This shows a way to change the icon if you don't want to go back to an older version of grub.  Haven't tried it yet but it looks like it should work.

[http://ubuntuforums.org/showthread.php?t=1346933](http://ubuntuforums.org/showthread.php?t=1346933)

---

