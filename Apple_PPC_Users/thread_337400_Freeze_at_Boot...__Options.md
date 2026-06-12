---
title: "Freeze at Boot...  Options?"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by kaerfull on 2007-01-12
I have a 867Mz Quicksilver and I'm trying to get Ubuntu going on a dedicated internal hard drive. I couldn't get 6.06.1 LTS or 6.10 CDs to boot. They would always hang at the "Mounting Root File System" point. I was able to boot and install 5.10. After loading all 5.10 updates I then let Ubuntu update itself to 6.06. As I expected, after the update was complete, the reboot freezes at the "Mounting Root File Sytem" the same as it did with the CD. Do I have any options other than being stuck with not being able to go beyond 5.10?

---

### Post by kaerfull on 2007-01-14
OK, so none of the big heads here have any suggestions for me, eh? How about this one then. How do I install a Flash plug-in for Firefox. Downloaded the Linux installer for Flash 7. When I run it, it acts like it's doing something but I never see the plug-in getting to the Plug-in folder. A manual insall doesn't go much better as I don't have permission to alter the plug-in folder. Is there a way to have access to anything I want to change whether the OS wants me to or not? Yes, I'm new at this.

---

### Post by precinto on 2007-01-14
hi there, you should try with some booting option. I think you can see the options in the help menu of the intaller boot. When I first installed on my acer I had to use no acpi=off option for it to install, but i don't know which one should you use. You could even try modifiying you current menu.lst file to boot from you existing kernels with some options.

And Flash, I think you just can't have flash on ppc. But I'm not sure. 

Good luck.

---

### Post by 3rdalbum on 2007-01-14
> **kaerfull said:**
> Is there a way to have access to anything I want to change whether the OS wants me to or not? Yes, I'm new at this.

Create an application launcher on your top panel. Set the command as "gksudo nautilus". Then you'll be able to modify any file you want, within that window.

As far as Flash goes, Adobe don't make a version for PowerPC. Do you really need animated advertisements?

---

