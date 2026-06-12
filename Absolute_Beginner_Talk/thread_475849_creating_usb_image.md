---
title: "creating usb image"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Thomas Delbeke on 2007-06-16
How do I create a usb image of a win XP recovery cd? My dad's desktop crashed and the cd rom drive is broke. I made an image file of the recovery cd (ISO) with the menu that appears when you right click the icon on the desktop and choose copy disk. I selected image file and copied to desktop. Then I copied the ISO to my USB jetflash drive. I chose boot from USB drive on my dad's desktop (dell dimension). It says F1 (reboot) or F2 (boot menu), but the F1 key doesn't do anything and F2 gives me some fancy system statistics. I can't change boot sequence to USB. It is not in the menu. It is only available after restart and F12 (boot menu) and then choose boot from USB.

Am I doing anything wrong or is it just impossible? Is there a different image format for USB files?

Thank you,

Thomas

---

### Post by starcraft.man on 2007-06-16
I think you can use the same process as [detailed here]("https://help.ubuntu.com/community/Installation/FromUSBStick"). It's for making a USB install with the Feisty image, I assume its same for win xp.

---

### Post by Thomas Delbeke on 2007-06-16
Hi,

I didn't manage to get syslinux to work properly. But thanks for the info anyhow. I installed the hp key drive utility. I found out that syslinux was installed on my usb stick when I used the application. I installed the ISO image. I could now indeed boot from the stick. It asked me: boot: And then I didn't know what to type. It said F1 for advanced options. Doesn't show real info. It did run vmlinuz or something like that and initrd I believe. Then it proudly said: ready and went asleep. I didn't get a command prompt. I could type something but it didn't recognize the right keyboardtype. No command worked. I tried boot root ls ls - la cd .. and some other stuff. I checked the Transcend Jet Flash website and it said I couldn't make my stick windows bootable. Only DOS bootable.

Can you or anyone else help me out? Please beware, I'm dumber then I sound.

---

### Post by Thomas Delbeke on 2007-06-17
> **Thomas Delbeke said:**
> Hi,

I didn't manage to get syslinux to work properly. But thanks for the info anyhow. I installed the hp key drive utility. I found out that syslinux was installed on my usb stick when I used the application. I installed the ISO image. I could now indeed boot from the stick. It asked me: boot: And then I didn't know what to type. It said F1 for advanced options. Doesn't show real info. It did run vmlinuz or something like that and initrd I believe. Then it proudly said: ready and went asleep. I didn't get a command prompt. I could type something but it didn't recognize the right keyboardtype. No command worked. I tried boot root ls ls - la cd .. and some other stuff. I checked the Transcend Jet Flash website and it said I couldn't make my stick windows bootable. Only DOS bootable.

Can you or anyone else help me out? Please beware, I'm dumber then I sound.
Hi, I also have a bootable floppy drive at that computer. Maybe  I can install a driver on an floppy to boot from the USB key?

Thanks!

---

### Post by orb9220 on 2007-06-17
> I made an image file of the recovery cd (ISO)

copy the .iso file to usb key and booting from that will not work.
Because bios boot cannot boot an .iso

You can try to mount .iso file or put in xp CD and just flat out copy all the contents to the usb key. Then  at the prompt type setup.exe.

Don't know myself  what a usb key will do with a copy of xp on it tho.

---

### Post by Thomas Delbeke on 2007-06-22
Hi, it didn't work. So I bought a second hand DVD-drive. I've installed it properly (physically). Now I can put the recovery-cd in that drive and close it. But the BIOS menu says IDE-device not installed. How do I install it on a system without a functional OS? I don't have a driver for the DVD-RW drive but I do have the exact specs. Please help!

---

### Post by Thomas Delbeke on 2007-07-05
Ok thank you everyone,

It didn't work but I bought a used DVD-R/RW drive and then reinstalled without problems. I am currently trying to upgrade the whole PC. I already bought a second hand flat screen, with low resolution, since the CRT was defect, so far my dad is happy.

Thank you,

Thomas

---

