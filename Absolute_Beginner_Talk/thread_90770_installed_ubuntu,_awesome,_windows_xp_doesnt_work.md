---
title: "*installed ubuntu, awesome, windows xp doesnt work*"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by kruz on 2005-11-15
okay guys
im not a complete noob
but not fimilar with grub
ubuntu boots fine
yet i think there is something wrong
i boot to grub loader then windows xp
i get

NTLDR is missing
mount my hd in /dev/hda3

and i see my ntldr boot.ini etc in my c folder
i dont want to fixmbr and have grub be gone cuz i love grub

but i still have the problem of no XP
could it possibly be that my xp partition USED to be on /dev/hda1?
now its 3?
i cant even get to boot.ini to choose to boot from certain partitions from the boot.ini
thats the only error i get

i think it might be the windows attrib points
because i copied NTLDR from  anothers windows xp system

any ideas guys?
thanx

---

### Post by aysiu on 2005-11-15
[QUOTE=kruz]NTLDR is missing[/quote] This appears to be a Windows issue, and [Microsoft has some advice to fix it](http://support.microsoft.com/default.aspx?scid=kb;en-us;318728&Product=win2000#2)

---

### Post by kruz on 2005-11-16
thank you so much for ur response

however
i manually changed them in linux
and copied them from another machine

do you think that even in fat32
the file permissions could throw it off
and is there some program to edit windows file permissions?
in linux

thanx again for ur help
also i dont have a floppy drive, but i believe this boot disk should do

---

### Post by steve.horsley on 2005-11-17
You copied XP from one partition to a different one? I suspect that the windows loader is trying to look in the original place on the original partition for ntldr, whcih isn't there any more. Sorry, I have no idea how to fix it if that's the case. You might get lucky if you copy it back to its original. But your best bet might be to reinstall windows and then reinstall Ubuntu.

---

### Post by lerrup on 2005-11-17
are you sure that you put NTLDR in the right place?

---

### Post by kruz on 2005-11-17
i think steve is on
because no i didnt move it

but when i fdisk mbr
before i installed ubuntu it made my windows go to partition 3
or at least named it partition 3
and yes i tihnk ur right
its looking on partition one

how do i get ntldr to look somewhere else?

---

