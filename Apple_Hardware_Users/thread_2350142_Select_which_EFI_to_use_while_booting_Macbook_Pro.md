---
title: "Select which EFI to use while booting Macbook Pro"
date: 2017-01-21
forum: Apple Hardware Users
---

### Post by astrosfan1996 on 2017-01-21
I installed Ubuntu 16.04.1 LTS to a flash drive (I also told the installer to install the bootloader there) last night and discovered this morning that I could boot Ubuntu simply by inserting the flash drive with the computer turned off and then turning the computer on. No holding down option and selecting boot media; it just automatically booted Ubuntu. I then noticed that if I shut down the computer and removed the flash drive that the computer would boot into GRUB next time I turned it on (again, without selecting boot media). I though this was odd, since I had told the Ubuntu installer to put everything on my flash drive. I later decided that I wanted the computer to boot OS X (I have Sierra 10.12.2) automatically instead, so I booted OS X by holding option on boot and selecting Macintosh HD as boot media, then in system preferences I went to select startup disk and chose Macintosh HD (it was the only option). Now when I reboot the computer boots OS X automatically, but now I have no way of booting Ubuntu from my flash drive. I am able to run Ubuntu live from another flash drive by pressing option and selecting EFI boot, but I cannot boot my installation.

I booted the Live USB and mounted the EFI partition on my built in SSD and was surprised to see two folders within EFI/EFI: APPLE, and ubuntu (see screenshot). So it appears that the Ubuntu installer did install a bootloader on my SSD, but now my question is how would I select the ubuntu one if I want to boot Ubuntu?

---

### Post by &amp;KyT$0P# on 2017-01-21
While booted into Mac OS, backup your system, then try installing [rEFInd]("http://www.rodsbooks.com/refind/").  Does it give you the option to load GRUB?

---

### Post by oldfred on 2017-01-21
It looks like your Mac is like PCs.

Ubuntu on a PC only installs to the ESP - efi system partition seen as sda.
So that is why you have /EFI/ubuntu in your ESP.

But flash drives only directly boot from /EFI/Boot/bootx64.efi.

So you have to copy /EFI/ubuntu from ESP on sda to ESP on flash drive. You did create one on flash drive by partitioning in Advance?
And then copy again from /EFI/ubuntu to /EFI/Boot and then rename shimx64.efi to bootx64.efi.
The version of shim you are copying is hard coded to find more boot files in /ESP/ubuntu and that is why you also need that folder.

---

### Post by astrosfan1996 on 2017-01-21
[FONT=verdana]> **halogen2 said:**
> While booted into Mac OS, backup your system, then try installing [rEFInd]("http://www.rodsbooks.com/refind/").  Does it give you the option to load GRUB?

[/FONT][FONT=verdana]Ok, so I installed rEFInd on my flash drive (on a separate HFS+ partition) and it works now! But when I boot Ubuntu and log in the system hangs after I enter my password. It was doing this before too, but I was more worried about fixing my boot setup to worry about it. Any ideas? I have a MacBookPro12,1 2.7GHz Intel Core i5
[/FONT][FONT=verdana]
Also, in case anyone else has the same question about selecting EFIs and wants OS X to be the primary OS choice, after installing rEFInd I went to System Preferences and chose Macintosh HD as my startup disk. You can still boot using rEFInd if you hold down option at boot and select it.[/FONT]

---

