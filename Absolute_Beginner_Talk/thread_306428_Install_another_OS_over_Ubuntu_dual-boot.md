---
title: "Install another OS over Ubuntu dual-boot"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by mevets on 2006-11-25
I was wondering if I installed another OS over Ubuntu's partition whether GRUB would then be screwed over.

Any ideas?

---

### Post by moffa on 2006-11-25
If you are talking about Windows, it will erase grub.
You can always use a recovery cd and reinstall it, but it may cause problems with Windows' boot loader

---

### Post by mevets on 2006-11-25
It was actually going to be Edubuntu, but since you mention Windows. Do you know if Vista will mess up GRUB as well. I ask this because isn't just supposed to unload an image?

---

### Post by seshomaru samma on 2006-11-25
Windows whether Vista or XP or 2003 or whatever will rewrite the MBR which means it will kill GRUB. You can reinstall Grub easily afterwards but you will have to edit your grub menu file in order to boot into Windows. You will find many posts about reinstalling Grub and editing it in this forum.
If you install another Linux , it will rewrite Grub and will insclude both OS , so if you install Fedora alongside Ubuntu , the Fedora Grub menu will show both Linux options. Should be the same with Edubuntu.
 But why would you want to dual boot Edubuntu and Ubuntu? They are basically the same , Edubntu has few extra packages which you can install with aptitude.

---

### Post by Bartender on 2006-11-25
Is the Edubuntu desktop available in repositories?  I was gonna suggest to the OP that he just install the "Edubuntu-desktop" package then use sessions to go back and forth, but not sure it's available.  If it is, that would probly work better than wiping Ubuntu - you could try out Edubuntu without losing your Ubuntu install.
Of course, that assumes you have broadband...

---

### Post by CaveRat on 2006-11-25
Yup! Do a search in Synaptic Package Manager for Edubuntu and just install the desktop environment and whatever else you want. Then at login click on sessions and choose which environment you want to boot to.

---

