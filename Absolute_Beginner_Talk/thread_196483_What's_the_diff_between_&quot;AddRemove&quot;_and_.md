---
title: "What's the diff between &quot;Add/Remove&quot; and &quot;Synaptic Package Manger&quot;?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by xp_newbie on 2006-06-14
I just installed Ubuntu for the first time on my Lenovo 3000 N100 laptop.

I managed to make it work like a charm - including the 1280x800 resolution and sound (thanks to this wonderful forum).

My version is Ubuntu 6.06 LTS (Linux kernel 2.6.15-23-386).

I noticed two ways to install "things" (aside for the update function that currently checks for updates on a daily basis): "Add/Remove" via the "Applications" menu and "Synaptic Package Manger" via the "System | Administration" menu.

What is the difference between the two?

Are there packages in one that are not available in the other?
Or are these two different applications doing exactly the same thing?

For example, upon selecting "Synaptic Package Manger", I am prompted for the root password. "Add/Remove" on the other hand doesn't prompt (yet). Does this mean any user can use "Add/Remove" to install applications?

Thanks,
Alex

---

### Post by mostwanted on 2006-06-14
Add/remove only lists predefined programs (which can consist of several packages) which are part of Ubuntu's main repository. Synaptic and other standard APT tools lists packages made up from whatever repos you have enabled (mine has ~ 19 000 packages at the moment).

You'll notice that you need to input passwords in Add/remove as well if you try to install anything.

---

### Post by xp_newbie on 2006-06-14
Wow, thanks for the quick reply. Do I understand correctly from your message that anything that can be found in "Add/Remove" is by definition contained in Synaptic, but **not **the other way around?

---

### Post by mostwanted on 2006-06-14
Exactly.

---

