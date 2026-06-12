---
title: "Tri-booting Feisty, Vista, &amp; Windows Server 2003"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Goodson1974 on 2007-09-07
Hi
 
Before i try and set up my laptop, i was wondering if it's possible to have Vista, Windows Server 2003, and Feisty Fawn installed on the same machine and for all three to be available from the Grub menu?
 
I've searched the forum but can't seem to find the answer (although it's probably right in front of me!!)
 
Cheers

---

### Post by BrendanM on 2007-09-07
You're going to need to edit the grub menu.lst file to add the other OSes. I know Vista uses a different bootloader than XP/Server2k3, so you might have to have it set up where grub loads either Ubuntu or the Vista bootloader, and then from the Vista bootloader you can select Vista/2k3.

I found this link which might be helpful: [http://www.linuxforums.org/forum/installation/10193-need-add-new-os-entry-grub-boot-menu.html](http://www.linuxforums.org/forum/installation/10193-need-add-new-os-entry-grub-boot-menu.html)

Out of curiousity, why would you run a server OS on a laptop?

---

### Post by Goodson1974 on 2007-09-07
One of my mates is wanting to play around with Server 2003, but also wants to keep Vista on there, and i've convinced him to try Feisty as well.
 
Oh and thanks for the pointers!

---

### Post by viciouslime on 2007-09-07
If you just make feisty the last one you install, it will set grub up for you automatically :)

---

### Post by Goodson1974 on 2007-09-07
Hi Viciouslime
 
That's how i set it up originally, but there was no sign of Server 2003  in Grub.
 
Just Feisty and Vista.

---

