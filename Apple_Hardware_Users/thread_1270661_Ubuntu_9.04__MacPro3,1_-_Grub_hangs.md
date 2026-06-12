---
title: "Ubuntu 9.04 / MacPro3,1 - Grub hangs"
date: 2009-09-19
forum: Apple Hardware Users
---

### Post by digitaladdictions on 2009-09-19
I am trying to install Ubuntu 9.04 on a MacPro3,1 and having problems booting to it post install. I have all 4 hard drive bays filled and installing Ubuntu on one of the 4 hard drives all by itself.    

Using rEFIt to boot to the Install CD I started by booting in Live mode to see just how well things would work. While I did not do a great deal of testing xorg worked and more importantly networking worked.  As long as networking was working I could download what I Needed to get anything else working so I installed. 

The installer identified the disk that I wanted to install to as sdc. Durning the last step of the install I had grub install to sdc.  I did not choose sdc1 since it was the only OS on that disk so I figured it would be best to have it in the MBR of that disk.  

In any-case after rebooting rEFIt identified the new install passed control off to grub but grub immediately hung.  All I got was "Grub _" on the screen nothing else. I then tried installing grub to sdc1 again with the same result.  

After googling I found a reference on the Ubuntu forums about grub64.efi which I installed. rEFIt booted to it and I had a grub command line.  search /vmlinuz returned hd1,1.  I tried various times to boot to the kernel using grub64.efi but each time I issued boot the machine would just reboot and I would be back at rEFIt.  

search --set /vmlinuz
linux /vmlinuz boot=/dev/sdc1
initrd /initrd.img
boot 

I tried /dev/sda[1,2] thru /dev/sdd[1,2] with the same results.  

End result grub64.efi just keeps rebooting and the regular grub hangs at "Grub _"

Any advice?

---

### Post by sdunlapa on 2009-10-08
You should start here. [http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187). I had the same problem. I eventually installed grub to my primary/Leopard hard drive and now I just hold down the alt/option key when restarting and choose the drive that has ubuntu on it.

The only problem I have now is after I used refit it installed syslinux onto my primary drive so now when I hold down alt/option during a reboot my options are 1 OS X disk and 3 Windows disks. 1 of the 3 Windows disks only boots to a black screen showing "Missing operating system". 

Anyone now how to fix that??

---

