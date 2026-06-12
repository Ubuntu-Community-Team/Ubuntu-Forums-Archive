---
title: "Whats this? You wont turn yuorself off?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-09-19
My laptop gets to the fonal stage of shutting down with the loading bar totally black, and it doesnt turn off. Im running Kubuntu 7.04 but it also did the same thing as Ubuntu 7.04. Ubuntu 6.06 powers itself down, it works just fine.

Its pretty important as i am always on the go and my laptop is old so I cant afford to overhea it or  waste battery life, because I use it on the old bus.t

---

### Post by splintercellguy on 2007-09-19
Could it be an ACPI thing? Perhaps boot with noacpi?

---

### Post by Belliinator on 2007-09-19
Yeah well I complains when booting that ACPI cutoff is 2000 and Bios age is 1999, does that mean my BIOS is to old and will no longersupport Kubuntu? It the does an ACPI force or something.

---

### Post by splintercellguy on 2007-09-19
Perhaps the aging BIOS may be the cause of the ACPI issue, upgrade if you desire at own risk, or try booting the kernel with the noacpi option. It could be that your BIOS is blacklisted in the kernel.

---

### Post by Belliinator on 2007-09-19
How do you use the noapci boot option and what are the disadvantages?

---

### Post by splintercellguy on 2007-09-19
To temporarily boot with the noacpi option, at the GRUB menu, press e, then I think a to add, then noapic, then Enter, though could be wrong on that bit. For a permanent solution, you would edit your GRUB file:

gksudo gedit /boot/grub/menu.lst

and find a section that looks similar to this:

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=59b3081e-8857-4342-a37
3-438986a0ec7a ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

and add noacpi to the end of it. That said, I'm not really sure if noapic is the solution.

---

### Post by alienexplorers on 2007-09-19
Are you unable to get a BIOS upgrade.  My machine is 10 years old and I had to order a BIOS upgrade so I would have all the bells and whistles to run ubuntu.  I believe my BIOS came from e-support and not the manufacturer.

---

### Post by viking777 on 2007-09-19
My laptop is less than 1 year old and it won't shut down either (neither will is suspend,hibernate or log off. In fact all it will do is reboot). I have tried every distro I have ever heard of and every cheat code I have ever heard of and none of them make any difference.

The reason, I am told, is that the linux version of ACPI is much more tightly coded than the Windows version and therefore less flexible. 

There is nothing you can do except wait for the Linux ACPI to match the Windows ACPI funtionality - it hasn't happened yet.

---

