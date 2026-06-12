---
title: "Lilo Issues"
date: 2006-06-10
forum: Apple PPC Users
---

### Post by rupy on 2006-06-10
When my lilo boots up it just spits out something like this:
L9A 9A 9A 9A 9A 9A 9A 9A 9A 9A 9A 9A etc...

I have used the live cd to chroot into my linux install (/dev/sda3) and checked & changed the lilo.conf file and re-ran /sbin/lilo but nothing seems to help.

(I am running a Macbook pro and am trying to get triple booting going).

---

### Post by rupy on 2006-06-12
I managed to fix this eventually by doing some general fiddling. (eg: mounting the EFI partition {/dev/sda1})

Basically it seemed as if Lilo had overwritten boot records.

---

### Post by colinhayes on 2006-06-12
[QUOTE=rupy]I managed to fix this eventually by doing some general fiddling. (eg: mounting the EFI partition {/dev/sda1})

Basically it seemed as if Lilo had overwritten boot records.[/QUOTE]

just a note, at this point if you need lilo help it would probably be best to go to the x86 forum... I don't think you'll find many people over here with as much experience with lilo as you would over there.  Yaboot is probably the reigning bootloader 'round these parts.

---

### Post by Ptero-4 on 2006-06-14
colin. I think that since lilo/elilo is the bootloader used in x86 Macs, it's pretty common in this parts along with crapboot.

---

### Post by colinhayes on 2006-06-14
[QUOTE=Ptero-4]colin. I think that since lilo/elilo is the bootloader used in x86 Macs, it's pretty common in this parts along with crapboot.[/QUOTE]

are there really a lot of people around now that have mactel's and are boot linux on them?  either way, I would think that the mac forum would be a lot newer to lilo and in general there'd be much more knowledge of it over in the x86 forum.

---

