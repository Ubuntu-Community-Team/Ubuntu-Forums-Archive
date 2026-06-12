---
title: "Macbook Air Dual boot, OS X boot fail"
date: 2015-06-21
forum: Apple Hardware Users
---

### Post by William_Stone on 2015-06-21
Hi,
I have a dual boot installation of ubuntu 14.04 LTS 64 bit & OS X Lion on a mid-2012 Macbook Air w/ 4GB Ram, i5 1.6GHz Quad core, 128GB SSD. Ubuntu is on a 15GB partition. Ubuntu was installed from a USB stick, this machine has no optical drive.

Ubuntu is running fine, and is what I have been using since I installed it. However this morning I attemtped to start OS X for the first time since installing ubuntu, and OS X will not boot. After choosing OS X from the rEFit menu, the screen goes dark (not like the computer is completely off, the display still has power) and that's it, OS X never boots. 

I read some instructions about removing rEFit, but that involved working in OS X, and I'm not sure if that;s the direction to go regarding this issue anyway, so I'm asking for your advice here.

It won't be a disaster if I can't recover OS X, but there is a file I was using under OS X, and I can't find it searching the partition in the ubuntu Files explorer, but I know the name of it and I know it is there somewhere on the OS X partition. But it didn't turn up searching in Files.

Thanks!

---

### Post by typo-joe on 2015-06-22
I'm not sure exactly what you should do about the boot failure.

However, I did notice that in the Ubuntu desktop, I was able to access the partition of my mac os. You should be able to navigate your way through this partition to find the file you need. Being that it's being used by mac, may be why you can't find it when you search. Most likely what you are looking for will be stored in somewhere within the User folder, albeit a subfolder of a subfolder, etc.

As for the boot issue, I'd use the Mac OS install disk, boot from it and see if I couldn't do some trouble shooting from there. Worst case, reinstall the mac os on its partition.

I should warn, I'm new at using Linux of any sort, so use my advise at your own discretion.

EDIT: The mac os partition isn't found through the linux file browser. The drive should show up at the bottom of your 'dock' on the left of the screen, just like disks and usb drives do.

---

### Post by William_Stone on 2015-06-23
I was able to get into OS X by pressing Opt during start to start Bootcamp and choosing the Mac drive. Bootcamp does not list an option for Linux. And, in the OP I said rEFit was running at startup. It is GRUB that displays at start with options for Ubunbtu and OS X, though the OS X options in GRUB don't work. 

"The mac os partition isn't found through the linux file browser."

In Files under Ubuntu, there is a Mac drive. I can browse the drive, and I searched this drive for the file I was looking for. There is only one physical drive in the computer, with a 100GB partition for OS X and a 15GB partition for Ubuntu. When I browse the Mac drive in Files, it's just the Mac partition, not the entire physical drive. Then there is a second item in Files named "computer", and it is only the Ubuntu partition. 

Anyway, either OS can be run. It would be nice to have one boot manager listing both choices, but it's a minor issue. I'm  wondering if there is a way to get either boot manager to list both partitions.

---

### Post by este.el.paz on 2015-06-23
> **William_Stone said:**
> I was able to get into OS X by pressing Opt during start to start Bootcamp and choosing the Mac drive. Bootcamp does not list an option for Linux. And, in the OP I said rEFit was running at startup. It is GRUB that displays at start with options for Ubunbtu and OS X, though the OS X options in GRUB don't work. 

Anyway, either OS can be run. It would be nice to have one boot manager listing both choices, but it's a minor issue. I'm  wondering if there is a way to get either boot manager to list both partitions.

@W_S:

There is a learning curve to figuring out how to get things to show up in dual boot.  Using the option key should give you the OSX boot manager, and OSX doesn't exactly "recognize" linux as "existing" . . . it usually shows it as "windows" . . . .  Did you shut the computer down after the install?  Sometimes that is needed to get rEFIt to get it together and show the various choices.  It is "interesting" that GRUB will boot linux, bt not OSX, if it shows OSX as an option.

Another option is that for post 10.7 rEFIt will not work, so you would need rEFInd, which is the updated version, might give more capacity.  Also be aware that anytime you upgrade OSX, even security update, you will have to probably "rebless" rEFIt to get its boot manager window to show up . . . .

e..

---

