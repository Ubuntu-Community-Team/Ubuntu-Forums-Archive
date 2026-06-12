---
title: "Uninstall/un-partition"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Greg1977 on 2006-05-20
I have installed Ubuntu before on an old system and love it, but now feel ready to install it onto the 2nd hard drive of my newer computer, perhaps alongside another distro or two. The only thing that concerns me is how to "uninstall" the distro and "unpartition" the drives and get both hard drives back to normal should I want to. Of course, I don't think I'd want to, but just in case. Do I have to reinstall Windows from scratch? Any advice greatly appreciated.

---

### Post by cotcot on 2006-05-20
The GParted LiveCD is good to modify partitions : []("http://gparted.sourceforge.net/livecd.php")
You could leave your MBR untouched by installing the bootloader to removable media (for instance grub-install /dev/fd0 to have it on a floppy)

---

### Post by rdd on 2006-05-20
Another way ist to just install grub to the MasterBootRecord and should you ever want to wipe Linux again, you just pop in your WinXP-CD, start the recovery console and type in 'fixmbr' and it will delete grub from the MBR. 

Now Windows will boot normally again without Grub. Then you can use your favourite Windows partition editor (or even the Windows tool) to delete the Linux partitions.

Although I think it highly unlikely that you'll want to remove ubuntu again. If you run into problems, just ask here.

---

### Post by billt1984 on 2007-12-25
i know i sound like super noob and i am i just got this ubuntu on my computer now i got a 4 gig flash drive for christmas i want to install ubuntu on it and take it off my hard drive i made it way to big 45gigs. anyways i want to take ubuntu off the laptop and just boot from the flash drive when i want ubuntu so how do i install the grub to the master boot record. ohh i forgot my laptop is giving me problems someone in the house hit "anykey" will it was booting up and windows reformated over its self so now wont boot properly and only way i can seem to boot ubuntu is off the cd. thank god its free and friends pass it on. sorry if its alot of extra info but like i said im super noob.

---

