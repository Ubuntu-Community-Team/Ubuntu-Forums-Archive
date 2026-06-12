---
title: "GRUB-install from Live CD?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-09-16
I'm trying to install from a live cd, but GRUB isn't working for me.  When I boot it either goes straight to Windows, or after disabling the Windows drive in BIOS, I get an error about cannot locate operating system.

When I try to run grub-install from the live cd to any of my drives, I get the error "Could not find device for /boot: Not found or not a block device." 

What kinds of things would cause that kind of error?

Thanks

---

### Post by catlett on 2006-09-16
Did you run the installer when you booted to the live cd? The grub menu doesn't come up when you run the live cd. It boots into the menu for the live cd.
Then you press enter and there is a little setup before you get into the Ubuntu desktop. Once you are the desktop, there is an icon for the installer. Double click and the installer runs. At the end of the install, grub will be installed. Once it is copmp[lete you will be asked to remove the cd and reboot. That is when you will see grub.
Now the issue is, did you get through the instalation without errors? Can you boot into the live cd? If you can boot to the live cd, post the output of this command ```
sudo fdisk -l
```That will show your partitions. If we can discern which one has UBuntu on it, we can mount it and check for grub's folder, as well as the other system files to see if everything was installed properly.

---

