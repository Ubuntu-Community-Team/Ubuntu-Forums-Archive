---
title: "Kernels 2.6.20.15 and 2.6.22 installed but function incorrectly"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by seethreepeeo on 2008-02-20
I have this weird problem im facing. Firstly, some background info. Im running XP on my PC, I got VMWare workstation installed and put Ubuntu (Feisty Fawn) on it. This has a kernel version 2.6.20.15.

I wanted to upgrade to 2.6.22. So I download the kernel source, do the make config, make bzImage, make modules and make modules_install.

At the end of make bzImage, the vmlinuz and initrd.img files got created, which I then moved into the /boot folder along with the bzImage file found in usr/src/linux-2.6.22/arch/i386. I then modified the menu.lst file in /boot/grub and added another option as follows:
title Ubuntu kernel 2.6.22
root (hd0,0)
root /boot/vmlinuz ro root=UUID=<UUID here> quiet splash
initrd /boot/inird.img
savedefault

Now the weird part is, when I reboot, the splash screen shows "Ubuntu kernel 2.6.22" (as it is supposed to), and choosing it and booting works fine. But, running "uname -r" is supposed to tell me "2.6.22" instead it still tells me "2.6.20.15-generic"

what do you suppose is going on???

---

### Post by Arthur Archnix on 2008-02-20
Is that an actual cut and paste of your menu.lst?
> root /boot/vmlinuz ro root=UUID=<UUID here> quiet splash
initrd /boot/inird.img
If so it doesn't look right. You've got a typo in initrd, which says inird, but more importantly you seem to be missing the full names. Just for reference, I'm running kernel 2.6.22-14 and it looks like this
> kernel   /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd    /boot/initrd.img-2.6.22-14-generic
I'd look in your boot directory for the full check those against what you have.

---

### Post by seethreepeeo on 2008-02-20
Oh thats just a typo when I typed it right now. Its not a copy-paste. Ok so let me try a copy paste this time:

title Ubuntu, kernel 2.6.22
root (hd0,0)
kernel /boot/vmlinuz ro root=UUID=c06bef11-d7d3-4f05-bec0-6ed9b738b627 quiet splash
initrd /boot/initrd.img
savedefault

---

### Post by Arthur Archnix on 2008-02-20
and what is the output of this command?
```
cd /boot && ls
```

---

### Post by seethreepeeo on 2008-02-20
output screenshot attached.

---

### Post by Arthur Archnix on 2008-02-20
Hmm... everything looks fine to my untrained eye. The only thing I can suggest is that uname doesn't get its information from the kernel, but from the file name? You can test this by adding the kernel version to the end of you initrd and vmlinuz files, then making the appropriate changes in menu.lst

Sorry, but that is all I have. :popcorn:

---

### Post by seethreepeeo on 2008-02-25
ok, i did find out that creating a new initrd file might help. it does seem to help. i used mkinitrd, created initrd.img, changed the menu.lst file, but it doesnt work still. i have attached the screen shot of the startup screen after i choose the new kernel in the splash screen.

does this make sense to you?

---

