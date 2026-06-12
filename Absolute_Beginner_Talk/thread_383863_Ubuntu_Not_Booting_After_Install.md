---
title: "Ubuntu Not Booting After Install"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by MOkAONE on 2007-03-13
im new to ubuntu and linux all together... i just fished installing Ubuntu on my desktop, everything went fine during installation. i even checked the cd for errors before installing. after installing and after removing the cd like it asked, it doesnt seem to boot. i get stuck at "grub loading, please wait..."

i didnt a little search and found a thread this the following link.. [http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)

sounds like no. 2 "Grub loading, please wait..."  on the solution is sais to change the BIOS for it not to boot from floppy (cd-rom in this case). i changed it so that it skips all others and boots straight from the hdd, but still having the same problem. theres also another solution, but i have no idea wat that means.. can someone clear things up. wat does *"Although the current grub ebuild filters out -fstack-protector, it can't hurt to recompile grub with clean CFLAGS if nothing else helps."* mean?


btw... if i leave the computer for long enough, it eventually goes to a blank page with the little blinking line. which is the same thing as before, it just doesnt show all that previous stuff like "grub loading" and watnot.

---

### Post by confused57 on 2007-03-13
Maybe this will help:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5)

Here's some excellent info on using Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by moshuptrail on 2007-03-13
Tell us more about your PC.  Brand, model, BIOS version.
Don't worry about that comment.  Grub either works, or doesn't.  And rarely the latter.

You might try re-installing.  I've seen cases where it seemed to install, but something goes funky in formatting the HD and the Ub. partitions are not properly initialized.

---

### Post by MOkAONE on 2007-03-13
ill check out those two links in a bit.

i built my pc... im running an athlon 64 3700, Abit NF8 mobo. and i havent updated or tried to update the bios so watever version came by default is running. 

i thought about just triying to reinstalling, but figured if post and wait to see wat people suggest and hopefully it saves me the trouble of spending time installing it again.

---

### Post by MOkAONE on 2007-03-13
i just tried reinstalling ubuntu and still having the same problem.

---

### Post by MOkAONE on 2007-03-13
ohhh... wow, almost an hour after rebooting. it went from "please wait" to the Ubuntu loading screen. the bar is there, but it doesnt seem to be "loading"

---

