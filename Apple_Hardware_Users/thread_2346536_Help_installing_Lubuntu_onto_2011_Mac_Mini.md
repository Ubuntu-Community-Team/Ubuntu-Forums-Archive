---
title: "Help installing Lubuntu onto 2011 Mac Mini"
date: 2016-12-15
forum: Apple Hardware Users
---

### Post by thegrassman on 2016-12-15
I don't know if I'm an idiot or what, but I've been trying to do this all day and I can't get my Mac Mini to boot Lubuntu from USB. When I boot up the Mini, I hold the option key but there are no drives listed on the screen for me to select. The Lubuntu USB is supposed to show up on that screen as one of the options. I've done this successfully before as the Mini is currently running Linux Mint, but it's years old, now, and due for a refresh. I don't know what I did to make this work before, but I can't seem to do it this time. Maybe it was easier because I was coming from OSX to Linux. This time I'm going Linux to Linux.

Anyway, the DVD-ROM doesn't work so I have to do this via USB. How do I do this? I'm thinking maybe my bootable USB needs to be GPT instead of MBR, but I don't know how to change it. Can anyone help me?

---

### Post by ajgreeny on 2016-12-16
How did you create the bootable? USB?  You can not simply copy the lubuntu.iso file to the USB and expect it to boot, you have to use a utility or application that transfers the iso as an image.

You do not need the USB in GPT format, but standard msdos partition table and fat32 partition are required.

---

### Post by thegrassman on 2016-12-16
I used SUSE Studio Imagewriter 1.10 to create the bootable USB. I've successfully created many other bootable USBs using this process, so I don't think I'm doing that wrong. The problem seems to be unique to the Mac Mini.

I've formatted thumb drive to be fat32, but is it possible the Imagewriter app I'm using is formatting things in it's own way? It doesn't give me any options to change anything, nor does it make any mention of formatting the drive.

---

### Post by ajgreeny on 2016-12-16
> **thegrassman said:**
> I used SUSE Studio Imagewriter 1.10 to create the bootable USB. I've successfully created many other bootable USBs using this process, so I don't think I'm doing that wrong. The problem seems to be unique to the Mac Mini.

I've formatted thumb drive to be fat32, but is it possible the Imagewriter app I'm using is formatting things in it's own way? It doesn't give me any options to change anything, nor does it make any mention of formatting the drive.
Sorry, I can't help with that as I have never heard of the SUSE Studio Imagewriter and never used really Suse either, but I think it's unlikely.

---

### Post by g33zr on 2016-12-17
Imagewriter is what you use if you want to install openSUSE. You could try to use unetbootin, but I'd recommend Etcher if you want to boot and install a Linux distro on your Mac. If you were using Manjaro, I'd recommend isousb, which is perhaps the best gui tool I've used to create a bootable ISO.

---

### Post by thegrassman on 2016-12-18
I don't think Imagewriter is limited to openSUSE isos. I've used it to create bootable USBs for many distros without issue. Indeed, the USB I created for this mac works fine on other computers. The mac just won't see the bootable drive.

Thanks for the Etcher recommendation. It's a nice piece of software, although it didn't work for me in this case. As before, the mac does not see a bootable USB drive when I hold down the Option key at boot. I really don't know what to do here. I don't want junk the mini. It's a good PC and I have a use for it, but I can't get this thing to run the Ubuntu installer.

---

### Post by thegrassman on 2016-12-18
I'm reading the instructions located here: [https://support.apple.com/en-us/HT202796](https://support.apple.com/en-us/HT202796)

It says right at the top: "For best results, your external hard drive, thumb drive, SDHC or SDXC  card, or other storage device should be formatted as Mac OS Extended,  not FAT, ExFAT, or NTFS. And to function as a startup disk, it needs to  be using a GUID partition map."

I really think the GPT thing is my problem. I just don't know how to fix this on a linux box. I don't have another Mac with OSX, so I can't just follow the instructions on that page.

---

### Post by g33zr on 2016-12-18
Are you dual-booting the Mac Mini or have you already wiped the drive? I have an older iMac (2009) on which I had initially dual-booted with Manjaro and then wipe the drive and ran just Manjaro. Later, I decided to install Ubuntu and used Etcher to create a bootable iso, formatted as FAT 32. I was able to see the usb drive and experienced no problem with the boot and install.

---

### Post by thegrassman on 2016-12-18
I wiped it and installed Linux Mint a couple years ago. It's been running that exclusively since then. FWIW, I vaguely remember thinking, at the time, that what I did to get Mint installed wouldn't be repeatable since the process required OSX as a starting point. It's a vague recollection so I don't know for sure if it's even true, but it seems to be relevant now that I'm trying to do it again. Either way, I've made a number of attempts and scoured the web for answers, but I can't get this Mac to see the bootable USB. I'm starting to wonder if it's something wrong with my hardware. I don't know what that would be, but my struggle appears to be unique.

---

