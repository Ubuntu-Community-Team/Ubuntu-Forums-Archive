---
title: "Dual Boot Problems."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Judgegeo on 2007-10-30
So, i decided i would do a clean install of Ubuntu.. By deleteing the swap and Ubuntu partitions from my HDD, leaving on the Vista (and vista recovery) partitions.. This where my trouble started.

Grub attempts to run and returns an error. I can no longer boot into windows. 

Any help would be appreciated.

Cheers.

---

### Post by maybeway36 on 2007-10-30
If you have a floppy drive, find a DOS floppy (or type "dos" at the Knoppix boot prompt). Then type
```
fdisk /mbr
```
There goes GRUB. From the command prompt on the Windows XP CD, you can use
```
fixmbr
```

---

### Post by Judgegeo on 2007-10-30
Im running vista, on a laptop so no floppy or cd. I have the ubuntu live CD and thats it..

---

### Post by maybeway36 on 2007-10-30
```
dd if=/dev/zero of=/dev/hda bs=446 count=1
```
This should work.

---

### Post by Judgegeo on 2007-10-30
This did nothing, still get the error. Error 22 or 23, i forgets which. 

Quick responses would be great!

---

### Post by logos34 on 2007-10-30
why don't you just reinstall ubuntu right now?  You need a bootloader, and it's the only solution if you don't have a vista dvd with which to restore the vista boot manager.

---

### Post by Judgegeo on 2007-10-30
But if you resize vista partition using ubuntu, doesnt it annoy windows?

---

### Post by logos34 on 2007-10-30
> **Judgegeo said:**
> But if you resize vista partition using ubuntu, doesnt it annoy windows?

oh, if you want to resize vista, then yes I might be better to do it using vista's own disk management tool rather than gparted.  No experience with vista so can't say for sure.  But you still have to get into vista, so you'll have to reinstall ubuntu to get the grub bootloader back, boot into vista and shrink it, then reinstall ubuntu again taking up the new freed up space.  (or if expanding vista, then obviously you'll have to reinstall ubuntu on a smaller space).

---

### Post by Judgegeo on 2007-10-30
Is there no way i can just remove grub?

---

### Post by logos34 on 2007-10-30
grub has two parts: a tiny (512 bytes) stage1 on the master boot record, which is the first thing that the bios accesses after POST.  Stage1 then looks for stage2 on the linux root (or /boot) partition, which in turn finds the menu listing the partitions and kernels.  But you erased ubuntu so that's all gone.  Grub stage1 overwrote the vista boot manager, so removing grub stage1 won't bring back vista loader.  Your only recourse in the present situation is as I suggested above.  (OTOH, if you could download Super Grub disk on another machine and burn it to cd, you could try to use that to boot vista.  Or find a copy of the vista dvd and enter the repair environment to restore the bootloader).

---

### Post by Judgegeo on 2007-10-30
I tried to change partition of vista, but in the gnome partition program it wont let me. Its locked. So i have no idea what i am to do now. I have a recovery DVD. But last time i ran it it just formats hdd. Why couldnt i burn super grub disk from live cd?


EDIT:

[IMG]http://i9.photobucket.com/albums/a52/Judgegeo/Screenshot.png[/IMG]

Can i not just restore these somehow?

---

### Post by logos34 on 2007-10-30
the lock means it's mounted--unmount first.

add: can't burn a cd while your using live cd!  (or do you have a second cdwriter?) Besides, you have to download it first and save iso to hard drive, then burn it.

---

### Post by Judgegeo on 2007-10-30
Ok thanks, I have unmounted and am resizing partition and have allocated 20 out of 120GB to ubuntu+swap. Can you explain what i need to do once i have reinstalled ubuntu?

Thanks for the help!

---

### Post by logos34 on 2007-10-30
> **Judgegeo said:**
>  Can you explain what i need to do once i have reinstalled ubuntu?


Hopefully it will detect vista and add a menu entry.  Boot into vista first and make sure everything is ok,  It may autorun a check of filesys (I know xp does).  If no entry, boot into ubuntu and add an entry to bottom of /boot/grub/menu.lst

---

