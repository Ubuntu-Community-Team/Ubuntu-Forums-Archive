---
title: "Full Installation To USB Drive"
date: 2018-05-18
forum: Apple Hardware Users
---

### Post by mw123 on 2018-05-18
Hi,

I am trying to install Ubuntu on a usb drive. I am not looking for a live usb with persistence, I want an actual full installation. For instance, before, I was using pop_os! ( excellent operating system by the way! ), which is based on Ubuntu. I have a usb that has a full version of pop_os! on it, and can be booted from any computer. It wasn't a live version. I tried that with Ubuntu, and that did not work. I selected erase disk and install Ubuntu, and then chose my usb drive on the following page. After the installation finished, the drive did not show up to be bootable. Worse, it had somehow messed up my boot loader - I am on a macbook. I could only boot into macOS by holding option. If I directly booted, I got a grub console. I eventually fixed it in recovery mode. I think this has to do with the install location of the grub boot loader. Can anyone help me?

Thanks!

---

### Post by sudodus on 2018-05-19
I wrote a detailed description of a full Installation To USB Drive at the following link. I hope it can help you get what you want.

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by oldfred on 2018-05-19
+1 on sudodus' link & instructions.

I just installed 18.04 to a flash drive on a PC, not Mac but still UEFI.

Some highlights of issues.
You have to partition in advance with gpt and have the ESP - efi system partition (FAT32 with boot flag)
But Ubuntu installs only to first ESP it finds usually sda or internal drive. For me it overwrote my /EFI/ubuntu which was the default boot of my internal drive.
So if you have an internal install of Ubuntu be sure to back up ESP and particularly /EFI/ubuntu folder.

I tried copying /EFI/ubuntu from sda to flash drive, not sure that worked. You have to copy twice, once to /EFI/ubuntu on flash drive, but again to /EFI/Boot and rename grubx64.efi to bootx64.efi.
All UEFI systems boot from external devices using ESP on external device and /EFI/Boot/bootx64.efi which can be any UEFI boot file, Windows, Mac or Linux.
You also need to edit fstab to use ESP of flash drive not the ESP of internal drive.

I was able to boot flash drive initially by using the entry on my sda drive which UEFI still saw as default entry.
I also did this to get grub installed to flash drive, so not sure if copy of files or actual grub install worked. the -removable creates the bootx64.efi file. I notice with 18.04 for first time the standard install of grub does create /EFI/Boot/bootx64.efi. 

       sudo grub-install --removable /dev/sdX  # where sdX is removable drive. 

You will also need the noatime parameter in fstab, so system is not writing on access of file. 
Someone posted that removing snaps sped up boot. I do not use snaps so uninstalled those. Not sure with other changes if it did anything or not.
I also change from standard gnome to gnome-panel which is more of a lightweight gui like the now very old gnome2 (before Unity) or like Mint or Bundgie (I think).

---

### Post by ubfan1 on 2018-05-19
Take a look at critical bug 1173457, [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457), and click on the
"Does this affect me?" button.  Oldfred's "copy the hard disk's EFI/ubuntu to the USB" should work, (or just copy the entire
/EFI) since the UUID used in /EFI/ubuntu/grub.cfg should be the USB's root.  Other possible problems are mentioned in the
bug, but only affecting secure boot (grubx64.efi used when shimx64.efi should be used).

---

### Post by mw123 on 2018-05-19
Sorry, I am pretty much a complete beginner, and I pretty much have no idea what you are talking about. Where is /EFI located? I do not have an internal Ubuntu install. What is ESP, gpt, and fstab? Thanks!

---

### Post by sudodus on 2018-05-19
Maybe you can try according to my link.

If it works, fine,

otherwise go into the complicated things according the @oldfred's and @ubfan1's advice.

---

### Post by oldfred on 2018-05-19
The link in my signature has at the bottom quick explanation and links to more info on most of the Acronyms we use.

---

### Post by C.S.Cameron on 2018-05-19
There are several methods of doing a Full install on this Ask Ubuntu page: [https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/983692#983692](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/983692#983692)
There are quite a few ways to do a Full install to USB, I prefer making the first partition FAT32 or NTFS so the drive can be used for data on a Windows PC.
I usually include a /home partition so the drive is easy to update version to version.

---

### Post by mw123 on 2018-05-19
How do I make a ESP partition on macOS? Where is /efi, and can you explain what these partitions do?

---

### Post by oldfred on 2018-05-19
Moved to the Apple sub-forum.

The ESP - efi system partition is FAT32 formatted with boot flag. 
Not sure how Mac does that.

UEFI suggests that ESP be first partition. If you have a Mac, you probably already have the ESP as all newer Mac use gpt with EFI (now UEFI v1, but with some updates for parts of v2) boot which was the predecessor to UEFI.

Some Mac specific links:
       FAT32 format  & label with boot flag on Mac
[https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation](https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation)
Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528)
[URL="https://help.ubuntu.com/community/MacBookPro12-1/Wily"]https://help.ubuntu.com/community/MacBookPro12-1/Wily

      [/URL]
 [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
    
       Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528)
[https://help.ubuntu.com/community/MacBookPro12-1/Wily](https://help.ubuntu.com/community/MacBookPro12-1/Wily) 
   Triple Boot Mac, Windows 10 & Ubuntu 2016
[https://www.innoq.com/en/blog/triple-booting-a-mac/](https://www.innoq.com/en/blog/triple-booting-a-mac/) 
   EFI-Booting Ubuntu on a Mac
[http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) 
    
[URL="https://help.ubuntu.com/community/MacBookPro12-1/Wily"]
[/URL]

---

### Post by mw123 on 2018-05-19
Everyone is talking about /efi, but where is that?

---

### Post by mw123 on 2018-05-19
Where can I find /efi?

---

### Post by mw123 on 2018-05-19
Sorry, I didn't see the second page and repeated my question #-o

---

### Post by sudodus on 2018-05-19
Maybe you can try according to my link (in my first post, Post #2)

That method assumes, that you unplug or disconnect the internal drive. Can you do that? (I have no Mac computer and don't know if it is easy or difficult to unplug or disconnect the internal drive.)

- It may work without going into details, and if it works, fine,

- otherwise go into the complicated things according to @oldfred's and @ubfan1's advice.

---

### Post by mw123 on 2018-05-19
That's a little hard for me to do, sorry!

---

### Post by sudodus on 2018-05-19
What you intend to do is not the easiest way to install Ubuntu. But it is possible.

Please take your time and read the links provided by @oldfred et.al. and after that ask again, if there are still things that need explanations.

[hr][/hr]
For example, an efi system partition will be created and used when the new operating system is installed unless there is already such a partition that is working with the current installed system (MacOS). If you want an external drive with an operating system, that is independent of the internal system, you need an efi system partition in the external drive.

---

### Post by mw123 on 2018-05-20
Never mind, I thought Manjaro looked cool and tried it out. It is great so far. I have it installed onto my flash drive, and it works on multiple computers.

---

