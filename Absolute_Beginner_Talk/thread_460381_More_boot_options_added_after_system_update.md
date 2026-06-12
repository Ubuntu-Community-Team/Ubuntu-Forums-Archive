---
title: "More boot options added after system update"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by dean_brfc on 2007-05-31
I've just updated my system via the update manager and it asked me to restart, and when I did I was presented with several more Ubuntu versions than normal (I dual boot with XP). Usually I have four options, this time I think I had six. I only had a quick glance at the screen but I think the kernel numbers differed.

Is this due to the update? Is it safe to remove the older ones from the boot option menu, and if so, how would I go about doing this?

---

### Post by Sparkster185 on 2007-05-31
Each time you upgrade the kernel, you get two new options added to the boot menu (one for ubuntu, one for recovery mode).  They are just so if the update broke anything you can roll back and use the older/working version.

You can delete them if you edit your grub table (search for how to do so), but there's no real reason to.

---

### Post by Cypher on 2007-05-31
Yes, those are the new Kernel and it's Recovery variant that were added. It's the Kernel installation that required the restart. Usually application installation will not requite a system restart.

If you've booted into the latest Kernel, you can tell by looking at the prefix after 2.6.20-XX, and everything is continuing to work like it always has, then you can certainly remove the older Kernels.

But I would give it some time before removing the Kernel and if you only have 2 Kernel options, it might be good to just keep the older one JUST in case. If you have more than 2 Kernels, you can delete the oldest safely..

---

### Post by lamalex on 2007-05-31
this is normal, when it installs a new kernel it adds a new entry to menu.lst, it's safe but more or less pointless to remove unless you remove the whole old kernel. the menu.lst is located in /boot/grub/menu.lst. edit that file to erase those entries from your bootloader screen.

---

### Post by dstew on 2007-05-31
The older kernels can be removed with Synaptic. If you remove them that way, Synaptic will automatically remove them from your grub menu as well. However, it is usually good practice to keep the next-to-newest kernel on board, just in case some bug appears in the newest kernel. But if you have three kernels, get rid of the oldest one.

---

### Post by lazyart on 2007-05-31
You've got the new kernel.  Leave the old entries there for now until you're satisfied that all is well.

The new kernel made a mess of my desktop system so I commented out the references to the new kernel and boot into -15.  Admittedly I have declined the same update on my laptop.  Instead of dodging it I need to address it (it's a video driver issue I believe) but I'm rebuilding my system this weekend (P4 2.0 to AMD64 3700) so I'll tackle it then.

---

### Post by Inxsible on 2007-05-31
Yes, this is because of the update. The latest updates included kernel updates from -15 to -16.
 
I would advise against removing the older kernel since many ppl have had problems with the new kernel. Keep it around as long as you are not sure if the new one works.
 
To uninstall a kernel, simply go to Synaptic Package Manager and search for the kernel that you want to remove and make the necessary changes. Or course you cannot be logged in via that kernel, or it would bomb !
 
Removing it from Synaptic will also remove the grub menu entry for that particular kernel.

---

### Post by Inxsible on 2007-05-31
Got beat by a longshot !

---

### Post by Inxsible on 2007-05-31
> **Iamalex said:**
> this is normal, when it installs a new kernel it adds a new entry to menu.lst, it's safe but more or less pointless to remove unless you remove the whole old kernel. the menu.lst is located in /boot/grub/menu.lst. edit that file to erase those entries from your bootloader screen.
 
I actually acted quite hastily and removed my -15 entries from the menu.lst, but never removed the old kernel. Now I see a phantom CD-ROM 1 drive in my nautilus. Rest everything works fine.
 
My question is, can I copy paste the -16 entries again in the menu.lst, change the -16 to -15 and log in back to the -15 kernel ?
 
Will that work ? When I deleted the entries from the menu.lst, i noticed that all the rest was same for the -16 and -15 entries except of course the kernel number

---

### Post by dean_brfc on 2007-05-31
Thanks for the quick replies everyone. I'll leave everything as it is for now then, at least it was meant to happen, that was my main worry. :)

---

