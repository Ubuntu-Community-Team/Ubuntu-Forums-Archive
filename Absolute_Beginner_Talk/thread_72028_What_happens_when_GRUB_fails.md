---
title: "What happens when GRUB fails?"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by thtan on 2005-10-05
I was a total newbie when i installed Ubuntu. I had WinXP installed on my primary HD (c:\) by default. I dedicated a whole secondary HD (d:\) for Ubuntu. When the installation finished, GRUB was working fine, and i could select which os to boot when the system start up.

But recently, my secondary hd (d:\) failed! And only then did i notice that GRUB wasn't able to boot up my system anymore without it. With my d:\ unplug from the system, the start up screen will give me sth like 

GRUB ERROR 21

What can i do to rescue my system? Thanks.

---

### Post by lisje on 2005-10-05
just repair you windows, it will put your original masterbootrecord back... 
then you can at least boot your windows again

---

### Post by fourchannel on 2005-10-05
i had to do this once.

i booted from the winxp cd, and entered 'Recovery Console' mode.

once you are in.

launch  'mbrfix'  i believe that's what it's called. and it will restore your Master Boot Record.

---

### Post by matthewv on 2005-10-05
[QUOTE=fourchannel]i had to do this once.

i booted from the winxp cd, and entered 'Recovery Console' mode.

once you are in.

launch  'mbrfix'  i believe that's what it's called. and it will restore your Master Boot Record.[/QUOTE]

I think its actually FIXMBR....

---

