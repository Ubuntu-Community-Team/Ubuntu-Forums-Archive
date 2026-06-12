---
title: "Running ubuntu on Q"
date: 2006-08-25
forum: Apple PPC Users
---

### Post by iraszl on 2006-08-25
I would like to run ubuntu on Q, but I don't know how to go about it. :-k  Can somebody help to give me a lead? Do I have to download a disk image or what? Thanks guys! :)

---

### Post by kostkon on 2006-08-25
I suppose if you download the Ubuntu iso image, you will be able to use it on Q and run it. I assume you can do this, because actually Q is a port of Qemu on Macs, and can boot an OS from an iso file.

Ah and something else; you'll need to download the i386 version of Ubuntu and not the PPC. Q only supports i386 emulation and not PPC or any other CPU type.

---

### Post by iraszl on 2006-08-25
Cool. Thanks!

---

### Post by undead-monkey on 2006-08-26
i just did it yesterday, not really worth it but if you really want to, heres how.

Burn the Ubuntu live cd iso to a disk (Q would not boot from the image for me) and mount it on your desktop.
Start a new VM on Q. Use the default Windows XP setting (disable set time to host) with at least 256 ram (i used 512) boot from cd-rom option, and a harddisk (5Gb or more). Now load up the live Cd and go through the installer. IT WILL PROBABLY TAKE HOURS. After that, remove CD, change the boot setting to the Hard disk you just made and installed to, and restart Ubuntu. 

Note: Ubuntu runs slow as hell on  the current version of Q (use the most recent UN-stable build, it runs the best) and is really not worth the time. You really cant do anything with it but if your board like me, and want to do it for the sake of doing it, by all means go ahead.

Good luck, and have fun waiting

---

### Post by iraszl on 2006-08-26
Please see the attached screenshot. How do I boot with the noapic option. Where do I set that option?

---

### Post by undead-monkey on 2006-08-29
when the first menu screen pops up and gives you the options to boot from live cd, etc.. hit F6 and type " live ACPI=OFF" then hit enter and it should boot fine from the cd

---

### Post by undead-monkey on 2006-08-30
I suggest trying out Parallels. You cant download it and get a 1 month trial activation key from thier website.
It isnt cheap, but damn is it fast compared to Q and Qemu.

---

