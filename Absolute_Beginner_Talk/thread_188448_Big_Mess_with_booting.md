---
title: "Big Mess with booting"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-06-04
OKay i have installed Ubuntu on a computer a dual-boot with XP. It takes me to the GRUB menu and i can selct the OS, but if i select windows the computer shuts off after the inital Windows splash screen. The same thing happens in Ubuntu with the loading bar half-filled. the whole system crashes. 

Since windows is a priotity for me, I would like to get rid of the Ubunutu installation for now, but how do i do this. I have done it via a windows partition managewr before but since i cant get to it...

---

### Post by daschl on 2006-06-04
[QUOTE=neelabhro]
Since windows is a priotity for me, I would like to get rid of the Ubunutu installation for now, but how do i do this.[/QUOTE]

boot the windows xp installation disk, and find the rescue-console. there you can find a tool "fixmbr".. that will fix your master boot record and you should be able to boot windows again. 

but your problem doesn't sound like it is a grub problem. maybe you can give us more detailed informations about your problem!

---

