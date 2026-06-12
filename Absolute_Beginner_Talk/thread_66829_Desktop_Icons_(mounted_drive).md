---
title: "Desktop Icons (mounted drive)"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-09-18
hello, I managed to mount my 2nd Fat32 HD at /media/windows, the problem is it is showed on my desktop and it's quite annoying. is there anyway to remove that? and how to rename it? the current drive name is "windows"

---

### Post by macgyver2 on 2005-09-18
[QUOTE=jeffreyvergara.NET]hello, I managed to mount my 2nd Fat32 HD at /media/windows, the problem is it is showed on my desktop and it's quite annoying. is there anyway to remove that?[/QUOTE]
I'm assuming you're using Gnome...yes there is a way to remove that.

Go to Applications --> System Tools --> Configuration Editor, then choose Apps, then Nautilus, then Desktop, and uncheck the volumes_visible box.  The icons on your desktop for mounted stuff should go away (and won't appear in the future).

---

### Post by mtron on 2005-09-18
I'm not quite sure but this might also remove the fancy drive icons for mounted usb devices, what are quite handy for me, so i would suggest that you mount your harddrive not under /media/whatever, but under /mnt/whatever

Can someone check this? i do not have an usb device to try it.

---

### Post by mtron on 2005-09-18
double post 

BTW: where can i delete it?

---

### Post by jeffreyvergara.NET on 2005-09-18
[QUOTE=mtron]I'm not quite sure but this might also remove the fancy drive icons for mounted usb devices, what are quite handy for me, so i would suggest that you mount your harddrive not under /media/whatever, but under /mnt/whatever

Can someone check this? i do not have an usb device to try it.[/QUOTE]
 yes, it willl also remove any mounted usb devices. I like it though... my desktop have a Computer and Home icons, and whenever I mount USB devices, it places on the Top of the first icon.

I have mounted my FAT32 HD before also in, /media/windows, but it's name was 40GB Hard Disk 40 GB Media (something like that)

---

### Post by Zonkle on 2005-12-10
[QUOTE=jeffreyvergara.NET]yes, it willl also remove any mounted usb devices. I like it though... my desktop have a Computer and Home icons, and whenever I mount USB devices, it places on the Top of the first icon.

I have mounted my FAT32 HD before also in, /media/windows, but it's name was 40GB Hard Disk 40 GB Media (something like that)[/QUOTE]
If you solve this problem please tell us .... because I'm having the same problem ... when I mount the FAT32 parts it shows on my desktop ... I only want the USB one ..

I have three FAT32 parts called "windows1", "windows2", and "windows3". In the "Places" menu they are not sorted! .. they are showed like from up to down in the order "windows3" - "windows1" - "windows2" ! not 1 2 3! Why ? And how can I sort the menu ?

Also on the desktop they doesn't show in order .. but I used the Clean up by name. But I didn't find the same option for the Menus.

Thanks.

---

