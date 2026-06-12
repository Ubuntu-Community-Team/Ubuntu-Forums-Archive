---
title: "Vista drives not attached when gusty installed need help with menu.lst"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Rexor on 2007-12-19
When I installed Ubuntu I disconnected my RAID0 vista drives so that there was no "mistakes" made to them. I have Ubuntu up and running just fine with all the drivers needed. So I decided that I would hook my drives back up and see If I could get into Vista. I read [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first). I think that the drives must of been connected for that to work, because "Vista" is not an option.

Can someone point me to or walk me through editing menu.lst so that I can boot my vista drives?

Thanks

---

### Post by LaRoza on 2007-12-19
```

title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
chainloader     +1


```

This will work if Vista is on the second SATA drive, or a slave drive, and on the first partition.

Alter it if the above isn't true.

(Add it to the end of menu.lst)

---

### Post by Rexor on 2007-12-19
> **LaRoza said:**
> ```

title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
chainloader     +1


```

This will work if Vista is on the second SATA drive, or a slave drive, and on the first partition.

Alter it if the above isn't true.

(Add it to the end of menu.lst)

That worked. I am in Vista now. The only problem is I did not see GRUB give me a boot option, it just loaded up Vista. How can I get back to Ubuntu to fix this?

---

### Post by LaRoza on 2007-12-19
> **Rexor said:**
> That worked. I am in Vista now. The only problem is I did not see GRUB give me a boot option, it just loaded up Vista. How can I get back to Ubuntu to fix this?

At the top of "menu.lst" there is a hidden menu option, comment it out (Put a "#" in front of it and a space)

And set "timeout" to 10 for 10 seconds.

```

timeout 10

```

---

### Post by Rexor on 2007-12-19
Lol kinda a catch 22 here bud If I could boot into ubuntu and edit that file I wouldn't need to change it ;)

---

### Post by LaRoza on 2007-12-19
> **Rexor said:**
> Lol kinda a catch 22 here bud If I could boot into ubuntu and edit that file I wouldn't need to change it ;)

Do you see the grup menu? Press esc (fast most likely) before Windows loads.

If that doesn't work, use the live cd.

---

### Post by Rexor on 2007-12-19
Well I went ahead and got myself into a hole now. I do have GRUB set to 10sec. I set that when I was trying to edit it for vista. I discontented my Vista drives again and the GRUB cam right up. I figured I needed to get rid of the bootloader in Vista so I DL'd BCD and removed it:mad: Then moved my boot order in the bios to the ubuntu drive. I can get back into unbuntu now but Vista is hosed :( Do you do Vista support too? :)


EDIT: fixed. Used windows vista to "repair" and I now can see GRUB and boot in to either Ubuntu or Vista.

---

### Post by LaRoza on 2007-12-19
> **Rexor said:**
> Well I went ahead and got myself into a hole now. I do have GRUB set to 10sec. I set that when I was trying to edit it for vista. I discontented my Vista drives again and the GRUB cam right up. I figured I needed to get rid of the bootloader in Vista so I DL'd BCD and removed it:mad: Then moved my boot order in the bios to the ubuntu drive. I can get back into unbuntu now but Vista is hosed :( Do you do Vista support too? :)


EDIT: fixed. Used windows vista to "repair" and I now can see GRUB and boot in to either Ubuntu or Vista.

If you needed to fix the Vista MBR, use the Super Grub Disk, which will restore it with no problem.

I see you fixed the issue, but just to let you know, you didn't need to get rid of the boot loader, in fact, it wouldn't work without it.

---

### Post by Rexor on 2007-12-19
> **LaRoza said:**
> If you needed to fix the Vista MBR, use the Super Grub Disk, which will restore it with no problem.

I see you fixed the issue, but just to let you know, you didn't need to get rid of the boot loader, in fact, it wouldn't work without it.

Thanks it all seems to be working.....For the moment.

---

