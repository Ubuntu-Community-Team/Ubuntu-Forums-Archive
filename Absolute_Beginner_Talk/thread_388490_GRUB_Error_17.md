---
title: "GRUB Error 17"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by eddyj on 2007-03-19
Well, recently I was playing around with linux and I had installed ubuntu on a second harddrive that I have, while keeping windows xp on my main harddrive.  Everything was fine with it while ubuntu was installed, but after some playing around I decided to reformat the harddrive with ubuntu on it and go back to using it for storage.

Now I have a problem while booting up.  After all the regular booting stuff it says:

GRUB Loading stage1.5


GRUB loading, please wait...
Error 17

After this it just sits there and this happens everytime I boot up my system.  I'm not really versed in this kind of stuff so hopefully someone can help me out.  I also still have the Live CD for ubuntu if that will help.

---

### Post by cyberdork33 on 2007-03-19
grub uses config files from the linux install... since you deleted that partition, grub cannot start your computer anymore. If you are looking to make a windows only machine again, then you probably need to boot your windows cd and start the recovery console. From there you can fix the MBR (Which is where grub is installed) using the fixmbr command. I am sure if you google "fixmbr" you will find instructions. sorry to see you go!

---

### Post by Monk-e on 2007-03-19
I have a cd that has FreeDos which is basically a DOS clone so I think the following might help you.

If you have a windows startup disk or floppy somewhere boot into it. Then type "fdisk /mbr", no quotes. This clears grub from the mbr (among other things I guess). It always works for me. Hope this helps a bit.

---

