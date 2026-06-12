---
title: "Ubuntu Live CDs and Macbook pros early 2011"
date: 2011-10-02
forum: Apple Hardware Users
---

### Post by tpad on 2011-10-02
This a thread showcasing my frustration with Ubuntu Live CDs and my macbook pro 8,1.

I have tried every solution in this forum to try and go around the "initramfs unable to find a medium containing a live file system" error. I have tried making a bootable USB using dd under Mac OS X, making a bootable partition with the live cd using dd, tried making a bootable external harddrive using dd, tried using an external cd/dvd drive, tried burning different versions of ubuntu to disk with absolute zero success.

The first two attempts (live usb pendrive and usb external harddrive) resulted into them not being found by bootcamp/refit. All CDs I burned and used with the internal CD/DVD drive gave me the "initramfs unable to find a medium containing a live file system" error and when I used them with my external CD/DVD drive the bootloader/isolinux just hanged and froze around.

I need linux for college as I'm taking Computer Science, but I would love to be able to use it without resorting to VMWare or Parallels. Is there another solution for the time being? Is there any other distro out there that supports these macbook pro models out of the box (don't care about missing drivers, those I can fix myself)?

Thank you so much,
tpad

---

### Post by mörgæs on 2011-10-02
Have you tried creating the USB stick with Unetbootin?

---

### Post by tpad on 2011-10-02
Came here to report my success in booting a live usb of linux with a twist. 
I had to use the file stated here [link]("http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/") and had to follow the guide.

After that, I had a hard time making my touchpad work properly since I was running 11.10. Also installed b43 to get my wireless working.

---

### Post by gus.ke on 2011-10-22
> **tpad said:**
> Came here to report my success in booting a live usb of linux with a twist. 
I had to use the file stated here [link]("http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/") and had to follow the guide.

After that, I had a hard time making my touchpad work properly since I was running 11.10. Also installed b43 to get my wireless working.
Hey, I followed this post and the installation worked fine.  However, now I can't boot to the Ubuntu partition through the Apple bootloader.  I set the location for the linux bootloader to the linux partition, not the entire drive (I didn't want to mess up the apple bootloader).  Should I have configured it otherwise?

---

### Post by tpad on 2011-10-22
Hi.

Have you installed Refit? I installed the bootloader to the entire drive, hence replacing the Windows bootloader that I had previously installed with bootcamp. The apple bootloader was not affected at all.

---

### Post by gus.ke on 2011-10-22
I can't install refit because I'm using OSX Lion.  I'll try again, applying the bootloader to the whole drive.

---

