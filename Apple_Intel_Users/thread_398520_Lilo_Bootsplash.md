---
title: "Lilo Bootsplash?"
date: 2007-04-01
forum: Apple Intel Users
---

### Post by Chrisj303 on 2007-04-01
Hi there!,

I am running a Macbook with a tripleboot setup (OSX/UBUNTU/XP). I had to use LILO because of keyboard issues with GRUB. Now, i read that it is possible to edit the way that LILO looks during bootup - but i read somewhere last night that the use of a LILO menu / bootsplash will crash ubuntu.
After a bit more investigation with google, i couldn't find a single reference to using a LILO bootsplash with Ubuntu...

Could anyone confirm that you can or can't do this? I'm a proper noob with ubuntu, and i don't want to screw it up if i can help it.

And if i do screw it up, how would i replace the LILO.conf file (with my back-up), once i booted off the live CD and chrooted into my ubuntu install.?

Thanks in advance for any replies!,

chrisj303

---

### Post by Chrisj303 on 2007-04-01
*EDIT* I've worked it out : i had to add the line install=bmp to the lilo.conf file...

BUT i'm having the EXACTLY the same issue as i did  with GRUB - the keyboard only works 20% of the time! AAaarrghh!

chrisj303

---

### Post by oskarloko on 2007-04-01
.... I think the keyboard issue is because the apple keyboard / touchpad uses USB internal connection.. ( maybe I'm wrong ) and bootloader doesn't work well with strange keys on strange BIOS ( EFI )

Sure, an classical BIOS with a PS/2 always works fine...

---

