---
title: "Rename &quot;Boot EFI&quot;"
date: 2014-04-26
forum: Apple Hardware Users
---

### Post by Vinodh Moodley on 2014-04-26
I installed Ubuntu 14.04 LTS on my MacBook Air 2013 6,1 in dual boot configuration with Mavericks. I did not use refit or refind and chose to use Apple's EFI boot. When I hold down the Option key on startup, I get the option to choose between "Mavericks" and "Boot EFI". Choosing "Boot EFI" boots Ubuntu. Does anyone know how to rename "Boot EFI" to "Ubuntu"? Renaming "Mavericks" is just a matter of booting into OS X and renaming the Mavericks partition using the Finder. I tried the "bless" command in Terminal to rename the EFI boot volume to Ubuntu but it didn't work. Any help is appreciated.

---

### Post by Quackers on 2014-04-27
I don't know whether that should be done or not.
I suspect that renaming it may break the boot sequence as the files needed to boot are in that folder.
For example, if you now install Windows in EFI mode, that too will have files placed in the EFI Boot folder and on booting you would select that option from the boot menu and you'd get a choice between booting Windows and Ubuntu.

Just my best guess.

---

### Post by Vinodh Moodley on 2014-04-27
Thanks for the reply. If I plugin a bootable USB installer, then I get two Boot EFI's which means that if I install Windows in EFI mode, then i'll just get two Boot EFI's, one for Ubuntu and one for Windows. I also saw on a screenshot somewhere that what i'm asking is actually possible but I can't find info on exactly how to do it.

The other issue that I would love to sort out is:

When I select "Boot EFI", GRUB loads and then boots Ubuntu. There is a way to boot into Ubuntu directly via EFI stub without using GRUB at all. I also read in several places that this is possible but I can't find any info on how to exactly do it.

---

### Post by Quackers on 2014-04-27
As I said, I'm not sure about your first point, so can't really comment further on it.
The only way I know of to boot Ubuntu via EFI stub is by using rEFInd which will do that after copying the appropriate driver across (details on the rEFInd site).This method of booting will boot Ubuntu more directly (by-passing grub) but then there is no way (that I know of) to enter boot prompts, should a booting problem occur.

---

### Post by Vinodh Moodley on 2014-04-28
I deleted Ubuntu and created some free space for Fedora. I installed Fedora and it automatically created a separate EFI HFS+ partition. On restart, if I hold down the Option key, I get the Apple boot picker showing the Fedora logo and the Fedora name below it. Selecting it starts up Fedora.

I'm not sure why but Fedora works great out of the box with both my MacBooks with regards to EFI booting. Ubuntu needs extra attention just to boot and it's still not the way I would like it. If I had the know how, I'd use the Fedora installer to Ubuntu.

---

### Post by Quackers on 2014-04-28
Interesting. Fedora must do it differently.

---

### Post by Vinodh Moodley on 2014-04-28
Fedora created a System/Library/CoreServices folder within the EFI partition and added a SystemVersion.plist file as well as a dummy mach_kernel. This plist text file has the name of the OS in it. I created a separate HFS+ partition, named it "ubuntu", added grub and the above-mention folder and edited the plist file accordingly. I then deleted all the files in the apple efi folder, blessed grub and rebooted. Holding down option gives the option of choosing OSX or "Boot EFI" with the Ubuntu logo. This means that I got Ubuntu to boot via efi from a custom efi partition but I still cannot understand where the name "Boot EFI" comes from and why Fedora works fine. 

These explain how to do what I want but I some steps just doesn't work: 

[http://nosemaj.org/dual-boot-mac-linux](http://nosemaj.org/dual-boot-mac-linux)

[http://glandium.org/blog/?p=2830](http://glandium.org/blog/?p=2830)

---

### Post by Vinodh Moodley on 2014-04-28
Nevermind. I got it working! Once I did all the stuff that I mentioned above, "EFI Boot" appeared as per normal in the boot picker. Actually booting into Ubuntu and then restarting with the option key held in showed "ubuntu" instead of "EFI Boot". I'm not sure why this finally fixed it and i'm also not sure if I can get it working again but it works for now. \\:D/

---

### Post by Quackers on 2014-04-28
Do you still have a firmware.scap file in EFI/APPLE/EXTENSIONS folder? 
That is used to process firmware updates and should not be removed.

---

### Post by Vinodh Moodley on 2014-04-28
> **Quackers said:**
> Do you still have a firmware.scap file in EFI/APPLE/EXTENSIONS folder? 
That is used to process firmware updates and should not be removed.

I deleted it but it gets recreated by itself. Just checked now and it's back.

---

### Post by Quackers on 2014-04-28
That's alright then, though it didn't appear to re-create itself on mine. Anyway, as long as it's there that's ok.

---

### Post by Vinodh Moodley on 2014-04-29
Here's a short video I made of what the boot picker looks like on my MacBook Pro. I think it looks better than using refit or refind. It doesn't do anything better than refit/refind but I prefer using the built-in capability rather than using a 3rd party app. Also, if anyone needs to know how I did it, feel free to request and i'll write a short how-to.

[video=youtube_share;w0RM3L8r4cE]http://youtu.be/w0RM3L8r4cE[/video]

---

### Post by Quackers on 2014-04-29
That's very neat. It's a bit involved but neat.
If you reboot holding the Alt key and get your boot menu up and then hold down the shift key (and keep holding it down) whilst clicking on Ubuntu does the grub menu appear?

---

### Post by Vinodh Moodley on 2014-04-29
> **Quackers said:**
> That's very neat. It's a bit involved but neat.
If you reboot holding the Alt key and get your boot menu up and then hold down the shift key (and keep holding it down) whilst clicking on Ubuntu does the grub menu appear?

It doesn't appear. I think that this is because I edited GRUB to have a zero timeout and not to search for other OS's. I would prefer not to use GRUB at all but I'll learn how to do that eventually. I'm still recovering from brain pain after figuring out the whole rename "Boot EFI" episode.

Also, my method is not that involved. All you have to do is create a small HFS+ partition (200mb) for efi, copy the relevant boot files, bless GRUBx64.efi and boot.efi. The boot files can be edited in any text editor but should be used as is if you only want to use it for Ubuntu. I can upload the boot files and any relevant info eg. screenshots etc if anyone needs it.

---

### Post by Quackers on 2014-04-29
I would expect grub to appear.
I appreciate the grub timeout but what happens if you install a new kernel, for instance, that won't boot? With no access at all to grub you can't choose to boot a previous kernel and you're locked out of Ubuntu (other than a chroot).
That was the downside to booting Ubuntu from EFIstub (can't enter boot prompts).

Yours look better than mine ever did though :D

---

