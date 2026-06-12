---
title: "remove stuff from grub"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by twist2b on 2008-04-12
I have like 20 lists even though i only have 3 OS
how do i delete the un-important stuff. Theres a way by getting the Grub cd but i dont want to burn onto a cd.

---

### Post by Capricori on 2008-04-12
By 20 lists, you mean 20 entries in the GRUB? Or 20 copies of menu.lst?

---

### Post by vgrisham on 2008-04-12
> **twist2b said:**
> I have like 20 lists even though i only have 3 OS
how do i delete the un-important stuff. Theres a way by getting the Grub cd but i dont want to burn onto a cd.

To clarify, do you mean you have a lot of items on your boot menu (such as previous kernels)?

If so, pop open a terminal and code: 
>  cd /boot/grub

Then backup your list by coding:
> sudo cp menu.list menu.bak

Finally, open your list for editing as follows:
> gksudo gedit menu.lst

Once there, carefully select and delete the previous blocks of text pertaining to previous kernels that you no longer wish to have available from grub. For instance, my my list looks like this:
> ## ## End Default Options ##

title        Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b228bd36-1063-4dd6-a66f-94500a79ae12 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b228bd36-1063-4dd6-a66f-94500a79ae12 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=b228bd36-1063-4dd6-a66f-94500a79ae12 ro quiet splash
initrd        /boot/initrd.img-2.6.24-15-generic
quiet

title        Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=b228bd36-1063-4dd6-a66f-94500a79ae12 ro single
initrd        /boot/initrd.img-2.6.24-15-generic

title        Ubuntu hardy (development branch), memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


In my case, I'm going to delete these lines because I no longer care to access the 24-15 kernel: 
> 

title        Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=b228bd36-1063-4dd6-a66f-94500a79ae12 ro quiet splash
initrd        /boot/initrd.img-2.6.24-15-generic
quiet

title        Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=b228bd36-1063-4dd6-a66f-94500a79ae12 ro single
initrd        /boot/initrd.img-2.6.24-15-generic


Do not delete the memtest block of text that pertains to memtest. 

Be careful. 

I hope that helps.

Vaughn

---

### Post by Cubby on 2008-04-12
> **vgrisham said:**
> To clarify, do you mean you have a lot of items on your boot menu (such as previous kernels)?


I've never learned to do it as Vaughn suggests, but I have removed old kernels by going to my package manager and doing a search for the old kernel which should show which ones are currently installed.  I have two kernels installed at the moment, as I recently did an update.

linux-image-2.6.20-15-generic was the original kernel and I can easily remove it by marking it for complete removal (which I have done in the past with no problems),  as my new kernel is linux-image-2.6.20-16-generic.  At the moment, I am keeping both kernels (both have safe-mode choices at Grub boot menu) for a couple of weeks to see how the new kernel acts, which is what is at the top of the grub boot menu and installs by default.  At the bottom of my Grub menu is Windows 2000 Professional.

Maybe you can let us know what those entries are at your Grub boot menu before you proceed.  That is an awful lot of entries!

Regards

---

### Post by R6V2 on 2008-04-12
Use this to access your GRUB:   sudo gedit /boot/grub/menu.lst

Well, I didn't really want the MemTest, so I removed it anyway...this is my log:


title		Linux Ubuntu 8.04 BETA
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5947cbd8-244b-4c50-b4ce-cad4c65b9748 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Linux Ubuntu 8.04 BETA Recovery Mode
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5947cbd8-244b-4c50-b4ce-cad4c65b9748 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Why exactly shouldn't I of removed the mem test?

---

### Post by drs305 on 2008-04-12
If you are editing menu.lst, there is a line "# howmany=all". You can replace the "all" with the number of kernels the menu will keep. Note that even though the line begins with a # symbol, this is not a comment in menu.lst - it will be read. 

So you can change "# howmany=all" to "# howmany=2" and it will display only the two most recent kernels. 

Note that this change will only take affect when the kernel updates, which may be a while (days/weeks/months). So you might want to make the changes as suggested in the previous post and then change the howmany from all to a specific number. Future updates won't keep expanding the number of options you see in the menu but will instead knock off the oldest one and replace it with the newer one (assuming you already have the max number of kernels displayed).  Also note this doesn't remove kernels from your computer, it only limits the number you see displayed in the grub menu.

---

### Post by twist2b on 2008-04-12
thanks, worked perfect. Yea I didnt know you could edit grub within Ubuntu. Thats pritty cool!

---

### Post by vgrisham on 2008-04-13
> **drs305 said:**
> If you are editing menu.lst, there is a line "# howmany=all". You can replace the "all" with the number of kernels the menu will keep. Note that even though the line begins with a # symbol, this is not a comment in menu.lst - it will be read. 

So you can change "# howmany=all" to "# howmany=2" and it will display only the two most recent kernels. 

Note that this change will only take affect when the kernel updates, which may be a while (days/weeks/months). So you might want to make the changes as suggested in the previous post and then change the howmany from all to a specific number. Future updates won't keep expanding the number of options you see in the menu but will instead knock off the oldest one and replace it with the newer one (assuming you already have the max number of kernels displayed).  Also note this doesn't remove kernels from your computer, it only limits the number you see displayed in the grub menu.

That's cool, I hadn't noticed that line. Thanks.

---

