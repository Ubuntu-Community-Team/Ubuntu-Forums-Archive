---
title: "rEFIt Wont Boot Windows/Ubuntu"
date: 2011-06-29
forum: Apple Hardware Users
---

### Post by Brando569 on 2011-06-29
My friend has an older Macbook Pro (circa 2006) and she installed Ubuntu 11.04 on it but the Appleloader wouldn't boot it directly (to boot to ubuntu I had to use super grub disk 2 to load grub2). I never got it to work correctly. 

She just updated rEFIt and it displays all the icons for windows and linux now, but she can't boot either of them, it just gives her a black screen with a blinking cursor up in the left-hand corner.

I suggested the easiest way to fix it would be to wipe everything and start over, but she doesn't want to. I barely know anything about macs and all the triple boot guides I've found are for fresh installs. Can anyone give me any suggestions?

---

### Post by Lars Noodén on 2011-06-29
Have you tried running the partitioning tool (second in bottom row) and synchronizing the partition tables?

---

### Post by Brando569 on 2011-06-29
Yep, it said they were in sync. It showed the GPT and the MBR, I read somewhere that it was bad to have both of them, or was that just the MBR boot partition?

---

### Post by handy on 2011-06-29
Have you had a good look here for a solution:

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

I've always found the answers to my rEFIt problems there.

I'm not trying to fob you off, I'm just speaking from experience.

---

### Post by Brando569 on 2011-06-29
I've looked through there too, and it didn't seem to provide much help. There's very little configuration that can be done with the config file and to install it all you do is drop it in a folder. 

There's no place to actually look at the configuration for the boot options (that I know of).

---

