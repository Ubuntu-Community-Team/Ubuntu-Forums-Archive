---
title: "Booted in Ubuntu &amp; Lubuntu then Windows, but Crashed and Can't Boot Again in Ubuntu"
date: 2017-10-03
forum: Apple Hardware Users
---

### Post by HDTimeshifter on 2017-10-03
I have a 2008 MacBook Pro (2.4 GHz) that was given to me with the keyboard unscrewed and missing a hard drive. I put in a hard drive with Windows 7 from an old non-powering Dell laptop and it booted up, but the mouse and keyboard didn't work to log in. So I swapped in my hard drive from a 2007 Acer laptop (1.66 GHz) with a dual boot Windows 7 and Lubuntu 16.04 (added since Windoze ran like a slug) and it booted fine and I was able to use the keyboard and mouse. I put that Dell drive in my Acer and reformatted with Ubuntu 16.04. Then I swapped drives again and the MacBook booted in Ubuntu, but I couldn't get the Airport Extreme wifi working. Some quick research showed I had to run Wine or some other method to configure the wifi in Windows or Mac OS, so I swapped the drives again and booted from the Windows 7 partition, but while it allowed me to use the keyboard and mouse to log in this time, it froze up with a blank screen and dead arrow cursor. I tried rebooting a few times and was unable to get to the boot menu (F2 or/and F10) to boot from the Lubuntu partition. I swapped drives again (to the Ubuntu-only drive) and it wouldn't boot again or allow me to get to the boot menu. All that happens now, is the unlock button power light comes on and I can hear the fans, but nothing displays. I am able to shut down by holding the power button and restart, but keep getting a blank screen. Anybody know what else I can try or what is wrong?

---

### Post by kevin160 on 2017-10-05
I have no idea why you would need to use windows to configure your mbp wireless.  Sadly, there is so much outdated or just-plain-wrong information out there.  I could be wrong, but I think your card is a Broadcom 4321, which means all you need to do is "sudo apt install firmware-b43-installer b43-fwcutter" while connected via ethernet.  

As for booting, go [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) and [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) and if you have to use 32-bit EFI [https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)

---

### Post by HDTimeshifter on 2017-10-05
Actually I had found some instructions on configuring the wireless in Linux. Unfortunately I couldn't get it to boot to try that out. I'm not sure either the SuperGrub2 or rEFInd solutions will work as it seems as if the video is dead since I don't get beyond a blank screen at boot and no way to select boot device. I did try unplugging and removing the battery to reset it and in case it was going to sleep instead of fully powering down when I held the power button down for several seconds. I guess I'll try inserting an Ubuntu 16.04 install disc (and a Ubuntu 16.04 USB stick - I think I created one) to see if I can get it to boot off of those.

---

