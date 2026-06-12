---
title: "Successful install:  Macbook Pro 4,1(early 2008) with Lubuntu 18.04"
date: 2019-09-12
forum: Apple Hardware Users
---

### Post by hecresper2171 on 2019-09-12
Hi,

I hope it's OK to post about successful installs.

I am happy to share that my early 2008 Macbook Pro 4,1 is smoothly running Lubuntu 18.04 LTS alongside OS X Lion.

Steps taken when it finally worked:

1. Installed OS X Lion
2. Shrunk the SSD drive and left only 40GB for OS X using Disk Utility in OS X
3. Used Rufus on a Windows PC to create a UEFI bootable USB with Lubuntu 18.04
4. Booted the Macbook off that USB
5. Picked 'Try Lubuntu' and installed to hard drive alongside OS X
6. Grub install failed as most cases do, so booted back into OS X and installed rEFInd from OS X's terminal
7. The first time it didn't boot to Lubuntu, so re-ran the rEFInd install script, rebooted and it worked
8. All the hardware is working, but WiFi took a little more work but was not that hard

Though I did a lot of internet searching looking through other posts and forums, only a couple of sites were on point for me:

1.  Freedompenguin: [https://freedompenguin.com/articles/just-ask-matt/old-imac-ubuntu-studio-installation/](https://freedompenguin.com/articles/just-ask-matt/old-imac-ubuntu-studio-installation/)
2. For wifi: [https://askubuntu.com/questions/136532/wireless-interface-not-found-on-a-macbook-4-1](https://askubuntu.com/questions/136532/wireless-interface-not-found-on-a-macbook-4-1)
3. For rEFInd: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Hope this helps others as well.

---

### Post by este.el.paz on 2019-09-12
That's great, "success" always feels good . . . but these days in linux, possibly since 16.04, we don't really "need" rEFInd to boot and run linux on a Mac--you just have to pick the "EFI boot" disk image from the boot manager, then when you run the system from that choice the install will work with booting while holding down the alt/option key.

The Grub file has to be pointed to the EFI partition of the disk . . . if you ran "automatic" it may or may not show that, but if you run the install as "custom" you point the grub to the EFI parition and flag it as "efi/boot" . . . something like that, from memory.  The installers are seemingly changing over time, but, generally getting "smarter" about it, and more or less if you can boot the live system, it should install well . . . ???

The rEFInd app used to be required, and it does provide some more functions that make multi-booting easier, like being able to tab down for "single user" boot, rather than having to quickly hit keys . . . but the installation got much more complicated, so I just moved on without it.

eep

---

### Post by ryansenn on 2019-09-15
I'm more impressed that you still have a working laptop from 2008 laying around. That's 11 years! But yeah really goes to show how far ubuntu has come, pretty awesome.

---

### Post by neufena2 on 2019-09-30
Have you managed to get the trackpad working correct?  Onmy 4,1 Macbook the system works well except the trackpad which is really laggy.

---

### Post by hecresper2171 on 2019-10-21
For me, it just worked.  No extra tweaks or anything else. 

Also, I have an update: I found a much better way to install Lubuntu/Ubuntu on the Macbook Pro 4,1(Early 2008).

I used this howto article here: [https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)

Much straight forward install.  Hope it helps others as well.

Another addition:

1. Edit the grub menu line at first boot and add nomodeset to the quiet splash line
    should look like this:  quiet splash nomodeset ---
    Press F10 to continue booting

2. Once logged in, open a terminal and do this:

sudo cp /etc/default/grub /etc/default/grub.bak
sudo nano /etc/default/grub
Add nomodeset to the same line as quiet splash
Should look like this:  "quiet splash nomodeset"
Save the file then
sudo update-grub

---

### Post by hecresper2171 on 2019-10-21
> **ryansenn said:**
> I'm more impressed that you still have a working laptop from 2008 laying around. That's 11 years! But yeah really goes to show how far ubuntu has come, pretty awesome.

It was a handy me down from my manager.  Then soon found out that it was stuck with an outdated OS X.  That's when I found out linux, especially Ubuntu, would run perfectly on it.  I've seen other articles and howtos for installing Windows but won't be doing that any time soon.  I'm very happy the way it turned out. \\:D/

---

### Post by randommike on 2019-12-22
Hi, I too have a early 2008 MBP. Installation goes through well. But during reboot after installation, it hangs in the purple screen. I understand it is because of video drivers. Did you encounter this problem?

Thanks.

---

