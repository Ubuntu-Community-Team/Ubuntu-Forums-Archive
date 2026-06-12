---
title: "update = twin system"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by racevskis on 2007-05-28
i updated my files as suggested by update manager and now when i start up or reboot i have two versions of fiesty operating system and two safe mode options ..............can this be changed........thanks

---

### Post by taurus on 2007-05-28
One is the latest kernel and the second entry is your previous kernel.  You still have only one Ubuntu but two different versions of kernel.

---

### Post by bobplano on 2007-05-28
i assume that there was a new kernel released. they have the older kernel stay on your grub menu in case the new one doesn't work. just edit you menu.lst and remove the entry. im not sure if you have to uninstall it or not, or how much room it takes up. just back up the file and change it though and the other fiesty should go away.

---

### Post by starcraft.man on 2007-05-28
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries") you go. Read this and you'll learn how to edit GRUB menu list. I linked to the section about entries, you probably wanna start at the top though.

You can open up the menu list and then just hide the old version (.20.15) by putting # (called commenting out) the lines that represent the entry. That should do it.

You want to use the kernel that ends with 16, unless you have a problem with it. 

Be careful, and please back up the list before you do it (I think they detail the cp command in the guide).

That should be it :).

Edit to bob: No, don't usually have to uninstall them, they don't take up that much space I don't think.

---

### Post by mcduck on 2007-05-28
It's pretty useless to just remove the entries in Grub, as you won't then be able to use the old kernel but it's still wasting your disk space..

Just uninstall the old kernel version with Synaptic, and the Grub entries will disappear automatically.

(I just removed the old kernel packages, freeing 251MB. Not much, but if you always just comment the old kernel out you'll sooner or later end with gigabytes of useless packages..)

---

