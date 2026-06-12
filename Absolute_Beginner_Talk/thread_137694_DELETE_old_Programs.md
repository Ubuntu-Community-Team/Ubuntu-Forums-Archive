---
title: "DELETE old Programs"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-28
Hi all

I would like to clean up my disk of old not used procedures.
Is there a way to list all installed programs and delete the ones not used or are out of date? Example( old tar's files, old Ubuntu OS's, etc.)

Thanks for any help

---

### Post by christhemonkey on 2006-02-28
Something like orphaned files in synaptic?
(go create new filter and select orphaned packages, or you can download the deborphan package which does the same sort of thing, although this is only for your .deb's)

---

### Post by kent41 on 2006-02-28
[QUOTE=christhemonkey]Something like orphaned files in synaptic?
(go create new filter and select orphaned packages, or you can download the deborphan package which does the same sort of thing, although this is only for your .deb's)[/QUOTE]

 Thanks I will give them a try

---

### Post by ncappel1 on 2006-02-28
If you open up Synaptic package manager, there are buttons in the lower left. If you click on the "installed" one, you get a list of all the pacages on your computer. if the list is too long, you can use the "search" button to find specific programs then right click on them and select remove.

The equivolent action through the terminal is apt-get remove [program name]

Maybe what you are looking for is Synaptic-->settings-->preferences-->files. mark the button that deletes the packages after they have installed, then clear the cache. you'll be set to go!

---

### Post by kent41 on 2006-02-28
[QUOTE=ncappel1]If you open up Synaptic package manager, there are buttons in the lower left. If you click on the "installed" one, you get a list of all the pacages on your computer. if the list is too long, you can use the "search" button to find specific programs then right click on them and select remove.

The equivolent action through the terminal is apt-get remove [program name]

Maybe what you are looking for is Synaptic-->settings-->preferences-->files. mark the button that deletes the packages after they have installed, then clear the cache. you'll be set to go![/QUOTE]

If I look in Synaptic I see Clamav.0.88 as obsolete but .88 is what I am running. can I remove IT?

---

