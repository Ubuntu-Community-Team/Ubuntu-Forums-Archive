---
title: "Old Ubuntu Versions"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-12-15
When I start my computer, I have the option of starting with Breezy, Hedgehog, or Windows.  I want to get rid of Hedgehog though, so I only have Breezy and Windows.  How can I do this?

Thank you.

---

### Post by Qrk on 2005-12-15
Do you still have Hoary installed? If not, you can just delete the entry corresponding to Hoary in /boot/grub/menu.lst

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by brentoboy on 2005-12-15
after you change /boot/grub/menu.lst make sure and run

sudo update-grub

to post your changes to the actual bootloader.  the menu.lst is a working copy of the real config file.

---

### Post by az on 2005-12-16
[QUOTE=brentoboy]after you change /boot/grub/menu.lst make sure and run

sudo update-grub

to post your changes to the actual bootloader.  the menu.lst is a working copy of the real config file.[/QUOTE]

No.  Lilo works that way, not grub.  Grub's menu list is the actual file.  Update-grub makes changes to that file.

Did you install hoary and then upgrade to breezy and both are displayed in your grub menu or did you install both side by side?

Because you should remove the older linux-image package using synaptic - that will make changes to grub after it removes the image.  If you do not remove that image, the next time you get a kernel update, your grub will be rewritten and the old kernel image will show.

If the hoary install is on another partition, removeing it's stanzas from grub menu.list will prevent it from showing up any more.  You should also reclaim the disk space by putting that partition to use, I guess.

---

### Post by amcavoy on 2005-12-16
I can't find that in Synaptic.  Any idea what to search?  I typed in hoary and hedgehog, but nothing came up.

Thanks for all the help :smile:

---

### Post by jan de beuker on 2005-12-16
when you are using 3 operating systems you most likely have them on different     partions on your harddisk. 
so when you run breezy and try to search for hoary you never find it because it is on a different partion.
 format the partion where hoary is on and it is gone

---

### Post by az on 2005-12-16
[QUOTE=amcavoy]I can't find that in Synaptic.  Any idea what to search?  I typed in hoary and hedgehog, but nothing came up.

Thanks for all the help :smile:[/QUOTE]
Which versions of linux-image do you have installed?

Remove the older ones (2.6.10... )  (2.6.8 are Warty, 2.6.10 are Hoary, 2.6.12 are breezy...)

---

