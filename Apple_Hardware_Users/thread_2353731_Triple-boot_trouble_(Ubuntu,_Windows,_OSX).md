---
title: "Triple-boot trouble (Ubuntu, Windows, OSX)"
date: 2017-02-24
forum: Apple Hardware Users
---

### Post by vegarab on 2017-02-24
Hi.
 
I have a somewhat unusual setup of OSes and bootloaders on my MacBook atm. I have a 512GB SSD, where I have done the following:


I had OS X installed. Through BootCamp, I installed Windows 10, splitting the SSD roughly 50-50. It has been running nicely, using the Boot Camp loader to choose between Windows and OS X when booting.
Some weeks ago I wanted to install Ubuntu, now my main OS, so I did. I took some space from both the Windows and OS X partition, and installed Ubuntu through a live-disc onto the new partition, which I split into 3: root, home and swap. 
Obviously, this messed with my bootloader, so I installed reFind in OS X, and now all OSes shows up in the reFind loader when I boot. However, there are couple of issues:
 
1. I have 2 options for Ubuntu:
i) Boot boot\vmlinuz-4.0.0-63-generic from 68GiB ext4 volume (that is my root volume)
ii) Boot Linux (legacy) from 65GiB ext4 volume
 
i) This is what I use to boot ubuntu, but it is somewhat weird. The screen goes black, and there is just a low of white text flying over the screen, with a green OK! in front. If I boot from hibernate, I can see it loading from swap, before it gives me the lock-screen.
ii) This just gives a black screen and a blinking dash, as if it cant find any boot-media.
 
2. I have 2 options for Windows:
i) Boot Microsoft EFI boot from EFI 
ii) Boot Windows (Legacy) from BOOTCAMP
 
i) This makes Windows start trying to boot, then goes to Automatic Repair, and gives a blue screen: "Recovery, your PC/Device needs to be repaired. You need to use recovery media... ". With the 0xc00000000e error. I have tried to have it do an automatic repair with a recovery media, but that was non-conclusive.
ii) This gives me the GNU GRUB loader, where I can choose between Ubuntu (which gives a normal ubuntu boot with the purple backgrond, ubuntu logo and 4 dots that represents the loading bar) and Windows Boot Manager (on /dev/sda1), and just gives a GRUB screen saying "Error: invalid signature".
 
OSX boots as normal from the OSX boot from Recovery HD (OS X partition) in reFind. 
 
Now I want to fix this bootloader mess without having to reinstall any OSes, if possible.
What is up with the Ubuntu-boot?

Edit: This is how my partitions look: [https://imgur.com/a/Ffv49](https://imgur.com/a/Ffv49)
 
Thank you.

---

### Post by howefield on 2017-02-24
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by oldfred on 2017-02-24
I do not know Mac.

But do you have hybrid partitions? And then BIOS boot loaders?
That used to be a requirement as Windows only booted in BIOS mode from MBR partitions.
It seems like rEFInd is giving BIOS boot options in addition to UEFI boot.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html) 

Someone that knows Mac may want more details:

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by vegarab on 2017-02-24
[http://paste2.org/5wg145fE](http://paste2.org/5wg145fE)
Here you go.

I honestly do not know if I have hybrid partitions, nor do I fully understand what it means. As I said, I installed in the following manner:
OS X is preinstalled. Installed Windows 10 through Boot Camp -> Installed Ubuntu on a new partition -> installed reFind with the default settings in OS X. That is the current state of the system.

---

### Post by vegarab on 2017-02-24
Boot-repair wont run on my Ubuntu install because it boots in Legacy mode. Should I create a live disk with boot-repair and try to run it?

---

### Post by vegarab on 2017-02-24
Created a boot-repair USB and ran it. Here is the outcome:
[https://paste.ubuntu.com/24059953/](https://paste.ubuntu.com/24059953/)

---

### Post by vegarab on 2017-02-24
That did something, but did not fix my Windows install. When I boot, GRUB is what I am presented with. It has my Ubuntu install, 2 faulty Windows options (EFI and UEFI) that both end in the same bluescreen as earlier. There are also alot of macOS and reFind options that do nothing. 

By holding down Option during boot, I can choose Macintosh HD and boot to macOS. The earlier-working Ubuntu drive now gives "error: file /boot/grub/i386-pc/normal.mod not found. Entering rescue mode.... "

Windows option from holding Option during boot also results in the same bluescreen. 

I am fearing I might need to do a reinstall of maybe both Ubuntu and Windows here?

---

### Post by vegarab on 2017-02-24
I gave up and formatted the Windows partition. My recovery disk didnt even recognize it as a Wndows install (bootrec /rebuildbcd). 
I cannot install Windows to my system because of the partition table. I am forced to boot the USB with Window as EFI, and then it requires a GPT disk. What now??

---

### Post by oldfred on 2017-02-24
Windows is then seeing the MBR partitions from the hybrid configuration.
You need to use gdisk to sgdisk to remove hybrid configuration.
I think installing Ubuntu in BIOS mode converted it to hybrid and used MBR(msdos) partitions.

With a Mac you only want UEFI boot with gpt partitions.
And how you boot install media, UEFI or BIOS is then how it installs.
Windows will only install in UEFI mode to gpt.
But Ubuntu will install to gpt or even MBR with either UEFI or BIOS. So important to have have partitioning match booting mode.

Some links, but do not know nor use a Mac, so not sure how good they are.
 [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528) 
   Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by vegarab on 2017-02-24
Thanks. 
I changed it to MBR protective and managed to install Windows. I can now boot into all three OSes through reFind. I just need to do some configs of reFind and GRUB to remove all unnecessary boot-options.

---

