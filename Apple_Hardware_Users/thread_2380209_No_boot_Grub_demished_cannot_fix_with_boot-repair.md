---
title: "No boot: Grub demished cannot fix with boot-repair"
date: 2017-12-14
forum: Apple Hardware Users
---

### Post by lucas-weteling on 2017-12-14
Hi,
I am running ubuntu 17.10 on my iMac. Went perfect.  Unfortunately, by mistake I've deleted grub or grub2, I think, I'm not sure what happend. The iUbuntu-pc doesn't start anymore.  
I wanted to fix it with boot-repair. So I runned ubuntu usb live, installed boot-repair and runned. I couldn't fix grub. (or grub2).
 I saved my data in pastebin [http://paste.ubuntu.com/26183254/](http://paste.ubuntu.com/26183254/)
Is help possible? Or is it hopeless? 
Regards, Lucas

---

### Post by oldfred on 2017-12-14
Moved to Apple sub-forum since iMac.

Do not know Mac, but see  a couple of issues.

Since they converted to Intel chips, Macs have used EFI, the predecessor to UEFI. Which also uses gpt partitioning.
Older BIOS systems use MBR(msdos) partitioning. A few older installs of Windows required BIOS/MBR and then on a Mac they created a hybrid configuration where the first 4 partitions were MBR and rest were gpt, but first 4 had to be kept in sync.
You really should install Ubuntu in UEFI boot mode, and not use hybrid partitioning.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
convert hybrid to protective MBR gdisk experts commands  p, x, n, p, w
[http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro](http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro) 
    
You have Ubuntu in BIOS boot mode as it shows grub in gpt's protective MBR and you have a bios_grub partition. You also show both MBR & gpt partitions.

You also show rEFInd which is for UEFI boot, but may boot a BIOS install.
You show the mount of the efi system partition in fstab, so at some point you did have Ubuntu installed in UEFI boot mode.

---

### Post by lucas-weteling on 2017-12-14
Tanks for the answer. I have read the URLs, but I do not know if these URLs are suitable for a Mac. The last URL even says "not for mac".
I was hoping to fix it with boot repair, but that went wrong. See the pastebin for data. 
In my view, I had to repair something. Is that  the MBR? Thereafter I can clean install ubuntu, I hope. 
I'm stuck.  What can I do?
Regards, Lucas

---

### Post by oldfred on 2017-12-14
The last link is in my signature and for UEFI in general. Only some may apply to Macs, and I do not know difference.
The other links are also general but should apply to Mac also as it used the hybrid partition table for Booting Windows in BIOS mode where the Mac booted in EFI mode.

---

### Post by lucas-weteling on 2017-12-15
Thanks, sorry. Situation is worse now. 
I cannot boot in live usb now. I boot in yellow EFI boot (I see two of them) and I choose "try ubuntu without installing". 
Then apears black screen with a not blinking cursor.
 I tried the same usb stick on my other iMac (running osx) that went well I, could run ubuntu live. So the usb stick is ok.

On the bad iMac booting with key "option" down and choose for "Window" (I think that is the old ubuntu 7.10 that was on my iMac) shows:
GNU GRUB version 2.02 beta3-4ubuntu7
Minimal Bash-like line ediing is suported. For first word , TAB list possible command completions. Anywhere else TAB lists device or file completions.
grub>

Are there Grub commands I can use? Or is that the wrong way?

Regards, Lucas

---

### Post by oldfred on 2017-12-15
There are grub commands you can try.
But you have grub in MBR for BIOS boot which may not work. Not sure if that is what you now are loading.
So manual boot may be just forcing a BIOS boot of your UEFI install.
You have an UEFI install, since fstab shows mount of /boot/efi.

       See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,3) ? If so, run the next command. Change if not hd0,3.

 Adjust drive, partition to your install:
ls (hd0,3)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,3)/boot # Do you see the kernel and initrd image files ?
ls (hd0,3)/boot/grub # Do you see lots of *.mod files and grub.cfg ? 


This may work, just to find grub.cfg in your install & use it:
configfile (hd0,3)/boot/grub/grub.cfg

OR directly load kernel:
set prefix=(hd0,3)/boot/grub
set root=(hd0,3)
linux (hd0,3)/vmlinuz root=/dev/sda3 ro
initrd (hd0,3)/initrd.img
boot

---

### Post by lucas-weteling on 2017-12-15
Thanks
Grub ls gives:

grub> ls
(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (cd0)
grub>ls (hd0,gpt3)
(hd0,gpt3): Filesystem is ext2.
grub> ls (hd0,gpt2)
(hd0,gpt2): Filesystem is unknown.
grub> ls (hd0,gpt1)
 (hd0,gpt1): Filesystem is fat.
grub> ls (hd0,gpt3)/  # gives a lot of dir and 'vmlinuz' and 'initrd.img'
grub> ls(hd0,gpt3)/boot  #I see the kernel, I think
grub> ls (hd0,gpt3)/boot/grub #have only two dir's
grub> ls (hd0,gpt3)/boot/grub/i368-pc #has a lot of mod files and grub.cfg is possible but cannot see because it moves very fast, so I am not sure dat grub.cfg exist in that dir.

So I tried:
grub>configfile (hd0,gpt3)/boot/grub/i368-pc/grub.cfg
Nothing happened
How can I locate grub.cfg?

Regards, Lucas

---

### Post by oldfred on 2017-12-15
If grub.cfg is missing or corrupted, the the direct boot of kernel if in hd0,gpt3 may work.

I would really try to get live installer to boot, as then you can run Boot-Repair and a full uninstall/reinstall of grub. 
And boot in UEFI mode.

---

### Post by lucas-weteling on 2017-12-18
Hi @oldfred

In the grub way I did not succeed in starting ubuntu.
I finally installed a USB El Capitan (OSX). When it turned out well I installed ubuntu 10.7. It is running well now. 
Downloading the data takes more time. Nevertheless, thanks for the help. 

Kindly, Lucas

---

