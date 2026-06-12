---
title: "Install from internal hdd error: unable to unmount /cdrom"
date: 2009-12-26
forum: Apple Hardware Users
---

### Post by mariguango on 2009-12-26
Hello there,
i tried to use Ubuntu on USB drive with no luck, then i use different workflow - i used vmware with Ubuntu live cd for making USB boot drive, then i copy this drive with dd to internal partition. Now it boot up and i can run Ubuntu Live from my internal FAT partition.
Then i try to run installation with no luck.
It don't go forward and show error that it can't unmount /cdrom and can't make partition changes, but i used gparted before and prepared all needed partitions - root with ext4 and swap, i only set root partition in installation and press Forward, after this, on next screen (where i can change boot loader options) i press Forward again and get this crap error about unmounting.
I have bootable Ubuntu but can't install it - i'm confused.
Can you help me? May be i can install it manually or use some installation options?

Thanks.

---

### Post by tom4everitt on 2009-12-27
Interesting. 

The installer is obviously designed to be run from a cd, and not from another partition on the same computer. That this is troublesome for the partitioner is not entirely surprising. 

I guess there's no good reason for it to refuse to install on ready partitions. 

I'm afraid your easiest option is to burn a cd.

---

### Post by mariguango on 2009-12-27
Very useful answer :)
Thanks anyway.
I have no working burner, so this is not an option. 
Will be great if someone provide me how to perform manual installation or something like this.

---

### Post by tom4everitt on 2009-12-27
Haha, yeah, I sort of realized I didn't really add much :P

I'm also rather curious about how one would do this manual install. I mean, in principle you shouldn't really need to even restart the computer. It should be possible to just extract the necessary files to a suitable partition, and fix a boot loader some way. 

If you want I could just make a tar.gz of my ubuntu 9.10 system (its quite freshly installed), and send it to you through ssh or something. 

I mean, I've never done this before, but it should work right? An operative system is just a bunch of files on a partition, and a boot loader. And the boot loader you can install from the terminal in your already running ubuntu.

---

### Post by mariguango on 2009-12-27
Sounds interesting :)
Will try to make installed copy in virtual machine, then will try to copy it from live partition to hard disk.
Thanks for interesting and simple solution.

---

### Post by tom4everitt on 2009-12-27
Cool, be sure to tell me how it goes, I'm quite interested. 

I realize you may have to do some changes to /etc/fstab and /boot/grub/grub.conf, so they get the right partition numbers etc. But this is just changing some numbers in a text editor :) I'll get back to you if I think of some other files that will need to be modified. 

Good luck :)

---

### Post by mariguango on 2009-12-28
This is much harder then i think before.
Right now i can boot to live media with grub2 and refit (thanks to **pxwpxw** [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704))
I copy all files from usb partition with installed Ubuntu (from virtual machine in OSX) with "cp -Rp". This is partition (hd0,4) or /dev/sda5
Then i install grub and copy /usr/lib/grub/i386/* to /dev/sda5/boot/grub.
Then i run 
```
sudo grub
grub> root (hd0,4)

grub> setup (hd0,4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,4) /boot/grub/stage2 p /boot/grub/menu.lst "...
succeeded
Done.

grub> 

```

Now i see partition with pinguin icon in refit boot menu, but i can't boot cause "No bootable device -- insert boot disk and press any key".

I changed all info in /etc/fstab and /boot/grub/grub.cfg about disks,
remove uuid and replace them by /dev/sda5.

Any ideas how to boot in this system?

---

### Post by tom4everitt on 2009-12-28
Okay, that was a good first attempt! 

I think I can count to two mistakes from your description though. 

The first is that you've installed the old grub, whereas your ubuntu uses grub2. I think this might help you: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Second, are you sure that "cp -Rp" is what you want? I'm afraid this might skip symbolic links. Perhaps "cp -aL" would be better? You can always try to fix grub2 first, but I think you might run into problems later due to this.

---

### Post by mariguango on 2009-12-28
Thanks man, i'm appricate your help.
Finally i was able to boot from usb partition with ubuntu live media. Now i have installed Ubuntu.
And i learn a lot of things about linux and grub.

---

### Post by tom4everitt on 2009-12-28
Ok, cool! I think I should go through this method myself some day, just to see if its working. As you said, one learns a lot from these things! :)

Enjoy your ubuntu!

---

### Post by mariguango on 2009-12-28
Agreed, i'm also want to try complete this way of installing Ubuntu (or any other linux). Thanks for support.

---

