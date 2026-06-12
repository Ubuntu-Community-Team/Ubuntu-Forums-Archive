---
title: "Boot up Message Please Explain"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-11-04
Hi,

Ubuntu Edgy has been working fine. Then this morning I booted up and got a message along the lines of:

dev/hda1 has mounted 30 times now, checking intergrity

Then there was a % symbol which gradually went up to 100% then it booted up. I had my breath held for a minute.

Anything to worry about or is this a normal periodic check? 

Tweed

---

### Post by llamakc on 2006-11-04
Nothing to worry about and yes, it is a periodic check.

---

### Post by Ocxic on 2006-11-04
this is normal, ubuntu will checvk the integrity of the drive after a drive has been mounted 30 times. you can change this default by editing your "/boot/grub/menu.lst" or turn it off altogether.

---

### Post by Tweedicus on 2006-11-04
Thanks for that - should come with a health warning though.

---

