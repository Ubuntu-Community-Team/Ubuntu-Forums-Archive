---
title: "Ubuntu wont load anymore, gets stuck on loading screen..."
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by tengu on 2006-08-11
hello, I'm completely new to Ubuntu, and linux in general, and I hope someone can help me. I have windows xp installed on my comp, and was dual booting linux until yesterday. Grub loads just fine, allowing me to select my operating system. But when the loading screen comes up, where it says UBUNTU and the loading bar, it says loading drivers' and then doesnt go anywhere from there. I dont know what the problem is, or even where to begin, so I home someone will be able to assist me. thank you.

---

### Post by nalmeth on 2006-08-11
When GRUB is loading, hit ESC to show the grub menu.
Pick recovery mode, which will have a very verbose loading screen. You should be able to track down whats going wrong. Post the output here if you're unsure whats up, and hopefully someone will point you in the right direction.

---

### Post by tengu on 2006-08-13
Thanks, i tried that, and this is what i got


Uncompressing Linux... Ok, booting the kernel.
Alert! /dev/hda2 does not exist. Dropping to a shell!

/bin/sh: cant access tty; job control turned off.

no idea where to go from there, appreciate any help. thanks in advance:)

---

### Post by petri on 2006-08-13
It seems like the partition (hda2) doesn't exist. And that is the partition where Linux (Ubuntu) probably is installed. Have you chanced something inside you pc? Maybe cable or something else isn't quite right?

If not, boot with LiveCD and via System - Administration - Discs look up what you have, I mean the harddisks. Mount everything and look what's inside, write it down and here too, I'll try to help :)

---

