---
title: "un-installing windows xp off of ubuntu?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by matious on 2007-06-04
while installing ubuntu i set my ubuntu partition to roughly 30 gigs or so, off of my 80 gig internal hardrive, thinking i would be able to dual-boot xp and ubuntu immediatly.

but now, i cant access xp, and when i check how much space i have available its only 26 or so gigs. So what im asking is can i get rid of that big empty 50 gig partition that was meant for xp so i can use that memory?

unfortunatly i missplaced my windows xp disk, that is why im wondering if i could uninstall xp off of ubuntu.

can anyone give me a tutorial on how to do this perhaps?

thanks in advance!

---

### Post by oilchangeguy on 2007-06-04
you should be able to resize the partition, by using gparted from the live cd.

---

### Post by pkarjala on 2007-06-04
When Ubuntu installs, it should have done so in a manner that doesn't affect your Windows XP install.  Watch for a boot menu when you're starting your computer, and you may still be able to access Windows XP.

If you're worried about "uninstalling" Windows XP, don't worry.  You don't need to uninstall it.  Just write over the data where XP used to be, and it will no longer be usable or take up space.  You can expand your Hard Drive partition to take up this space if you wish.

---

### Post by Bohlio on 2007-06-04
If you are automatically booting into ubuntu and cant find a way to get into windows, I think theres some setting in Grub that bypasses the boot options screen, and i think the menu is accessable by hitting ESC, I dont know when though...

---

### Post by matious on 2007-06-04
okay, i restarted my computer, and no xp option was giving, and when i pressed escape i was only giving a list of ubuntu kernals.

i put in the live cd, but dont see anything "gparted"?

would i be better off re-installing linux and having it use 100% of the disc space?

---

### Post by XxTaylorxLovelyxX on 2007-06-04
Dude what are you doing removing windows for.

---

### Post by matious on 2007-06-04
i can always install it again later cant i?

i don't really see the neccesity in it, many of the programs i was using on windows are readily available on ubuntu anyway.

gaim, firefox, gimp etc

the only thing id be really missing is itunes.

---

### Post by gashcr on 2007-06-04
try amarok ;)

---

### Post by matious on 2007-06-04
i have, i really didnt like the interface at all.

i got songbird, wich is almost identical to itunes so thats working nicely for me.

anywho, anyone know how i can do this partition stuff?

is there any program or something that can make it more user freindly or a step by step terminal way perhaps?

---

### Post by tbasherizer on 2007-06-04
In your ubuntu installation, go to Applications>Add/Remove

Search for Gparted

install that.

Then go to System>Administration>Gnome Partition Editor

Partition away!

PS. I use Banshee as my music player.

---

