---
title: "Need to change Radeon to fglrx in terminal"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-29
What do I type in terminal in order to change Radeon to fglrx?

---

### Post by Albi on 2007-03-29
It's more complicated than that.

Run sudo dpkg-reconfigure xserver-xorg

Select fglrx as ur driver in the first section

The rest should be straightforward, just choose "Simple" when it asks u at the end.  Any questions post them here.

(Yes, I know this isn't very user-friendly, there are efforts to integrate this better)

---

### Post by kittyhawk63 on 2007-03-29
> **Albi said:**
> It's more complicated than that.
Run sudo dpkg-reconfigure xserver-xorg
Select fglrx as ur driver in the first section
The rest should be straightforward, just choose "Simple" when it asks u at the end.  Any questions post them here.
(Yes, I know this isn't very user-friendly, there are efforts to integrate this better)

Thank you. I just asked this question on another thread I'm running. 
kh

---

