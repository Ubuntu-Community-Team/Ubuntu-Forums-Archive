---
title: "multiple ubuntus in grub?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by psycosmyth on 2006-08-30
I have searched this 'cause I saw this last week but I can't find it.

I have two pair of ubuntu os's listed in my grub menu. I know I at least need two. What's with the others? I think they are the same kernel.:-k

---

### Post by aysiu on 2006-08-30
If they're the same kernel, one's probably regular and the other "recovery mode." You should keep both versions of that same kernel.

If you want to remove the older kernel, search for *linux-image* in Synaptic or Adept.

---

### Post by psycosmyth on 2006-08-30
wow your fast!
I was about to edit this. I was wrong, ones -23- and ones -26-.
If 23 is stable ill yank it:p Do that in Windows!!:mrgreen: 
I get parranoid when I see things I'm not used to.

---

### Post by Jareth on 2006-08-30
Paranoia is my constant companion my friend.

sos, spooky reply.

---

### Post by grim918 on 2006-08-30
You can also modify the file /boot/grub/menu.lst and just comment out the
kernels that you dont want to show when grub loads.

esample:> #title          Ubuntu, kernel 2.6.12-10-386
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
#initrd         /boot/initrd.img-2.6.12-10-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.12-10-386 (recovery mode)
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
#initrd         /boot/initrd.img-2.6.12-10-386
#boot


---

### Post by CarpKing on 2006-08-30
> **grim918 said:**
> just comment out the
kernels that you dont want to show

Is there any disk space difference between this and uninstalling the "linux-image" package?  Or is that package mainly just there to tell grub what to boot?

---

### Post by Toxicity999 on 2006-08-30
By default when you install a new kernel the old one still remains this is a *good* thing because though ubuntu is GREAT about kernel upgrades running smoothly you never know if a new kernel might break for some of your hardware! This isn't a bad thing, you can edit grub to display only 2 of the latest kernels (what I would insist on.) or you can uninstall the old kernel by poking around synaptic once you know the new one works fine for you.

To the poster above me. Editing Grub to not show older kernels doesn't uninstall anything. The Grub config file just has a list of instructions of what to run for booting into various kernels. Kernerls don't uninstall by themself and are left to the user to uninstall old ones as they see fit. As I said above it's usually good to have the newest and second to newest installed at any given time just incase theres any regression in the new kernel. Meaning something slipped throug hthe cracks and the new kernel decides it won't talk to your hardware anymore.

Also, as you install new kernerls if you use the proprietary graphic drivers fro mthe repos make sure you wait to uninstall the old kernel untill the new restricted modules come out! They usually aren't set to print simultaniously, which they should be realistically.

---

### Post by AntiFlash on 2006-08-30
i agree about the ubuntu/kernel/upgrade's in grub.  I like having the most current stable with recovery as well as the next-newest kernel with recovery.  It allows for much more flexibility and net...more stability overall.  I have botched my installs more times than i can remember and it's great to know that i have multiple options to save my install without having to go at a fresh one...

---

### Post by psycosmyth on 2006-08-30
very cool! I had a good idea that was what it was all about, I had just converted to Gnome from Xfce and I wanted to check to see if my last instal from a kde live disk was ghosting around. My initial response to this was panic, now if it showed WinME I would have smashed the daylights out of my box.:-D

---

### Post by Toxicity999 on 2006-08-31
right grub is meant to be dynamically updating in a modern distro but there is a section that isn't 'automagically' updated as the y call it there.  Windows options by default go there so if you killed the windows partition the menu link would stick around it's not REALLY there it's just linked.

---

### Post by Kevbert on 2008-01-10
I have a similar problem.  I have two different Ubuntu kernels on my system.  My default OS is Ubuntu 7.10 32 bit and my other systems are Ubuntu 7.10 64 bit and XP.
During loading both Ubuntus seem to have the same name.
My menu.1st file:-

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f01f6ae-321a-4daa-83ac-053a2dfb4841 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f01f6ae-321a-4daa-83ac-053a2dfb4841 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1  

The reason I've installed both versions of Ubuntu is due to the fact that I have an AMD2 X64 based machine and I believe that some programs do not support 64 bit processors.
What I want to do is to edit the OS titles so that I can distinguish between the two versions and then make the 64 bit Ubuntu my default OS and not the 32 bit one.
I've tried using StartUp-Manager but this only shows one Ubuntu.

---

