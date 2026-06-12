---
title: "multiple OS with Grub"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2006-12-03
I currently have Ubuntu dual-booting with Windows 2000.
No problems.

I want to add SUSE 10.1 as another OS. When I got to the partitioning part of the install of SUSE, I see that the Grub menu no longer has the Ubuntu (recovery mode) and Ubuntu (memtest) as options.

What do I have to do to get those 2 options along with the SUSE options to all show up in Grub menu?

Thanks.

---

### Post by ReaderRat on 2006-12-03
[[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Voxxi on 2006-12-03
What SuSE did when you installed it, is installed its own GRUB settings. You might be able to get your original menu settings added to your SuSE one.

**Finding the old GRUB settings**

1) Try looking in /boot/grub on your Ubuntu partition for a file called menu.lst. Unless you installed GRUB to another location when you installed Ubuntu, it should be there.

2) Open it with your text editor.

3) Find where it gives the menu options, they should look *something* like this :

```

title		Ubuntu (Edgy) General
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Microsoft Windows XP Professional
root		(hd0,3)
savedefault
makeactive
chainloader	+1

title		Ubuntu, (Edgy) Sid
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Those are what mine look like, so yours might be a bit different.

4) Copy these options to the clipboard.

Ok, you've located the Ubuntu menu.lst, lets find the SuSE one.

**Finding the new GRUB settings**

1) The SuSE grub settings should be located in the same place. I don't have much experience with SuSE, so I could be wrong. If it isn't in /boot/GRUB, check any other folders in /boot.

2) Open it up in your favourite text editor. Menu.lst might only be writable by root, so you may need to use sudo to edit it.

**Adding the new settings to the  SuSE list.**

1) Copy all the text from the old menu.lst (Ubuntu) to the bottom of the new (SuSE) one, and save it.

2) Restart your computer.

The new settings should now be in the GRUB boot menu!

---

### Post by ieee488 on 2006-12-03
SUSE did have the Ubuntu kernel choice just not the other two.
Don't understand why SUSE couldn't just add to menu.lst


Will read that HOWTO when I'm at work tomorrow with nothing to do. ;) 

Thanks.

---

### Post by lucky_chouhan on 2006-12-04
Acronis OS Selector

---

