---
title: "[SOLVED] Macbook caps lock light"
date: 2008-12-05
forum: Apple Hardware Users
---

### Post by vakyoomluigi on 2008-12-05
I've gotten everything working with ubuntu on my macbook, but one little thing still doesn't work: the tiny green light on the caps lock key.  I know it sounds minor, but it's starting to bother me.  How do I fix this?

---

### Post by manuG on 2008-12-05
Hi,

You need to uninstall mouseemu. 

[HTML]apt-get --purge remove mouseemu [/HTML]

and then reboot.

---

### Post by hyperboloid on 2008-12-05
> **manuG said:**
> 
You need to uninstall mouseemu. 

[HTML]apt-get --purge remove mouseemu [/HTML]

and then reboot.

I see the same issue with the caps lock LED on a Macbook Pro 4,1 (Penryn) under Intrepid. For the record: Removing mouseemu does not do the trick for me. Not that this is important...

---

### Post by vakyoomluigi on 2008-12-09
Yay! It worked :)

---

### Post by beauman on 2008-12-11
> **hyperboloid said:**
> I see the same issue with the caps lock LED on a Macbook Pro 4,1 (Penryn) under Intrepid. For the record: Removing mouseemu does not do the trick for me. Not that this is important...


ok, so for vakyoomluigi it worked and for hyperboloid it didn't work?


I did write something about it in the wiki yesterday, and I need people to test it: [https://wiki.ubuntu.com/MacBook/SantaRosa#Middle&Right%20Click%20with%20Left&Right%20Cmd%20Keys]("https://wiki.ubuntu.com/MacBook/SantaRosa#Middle&Right%20Click%20with%20Left&Right%20Cmd%20Keys")

hyperboloid, can you have a look at the wiki and see, if it really does not
fix the LED issue? did you reboot? thanx!

---

### Post by hyperboloid on 2008-12-11
> **beauman said:**
>  
hyperboloid, can you have a look at the wiki and see, if it really does not
fix the LED issue? did you reboot? thanx!

Beauman, yes I confirm that removing mouseemu does NOT fix the caps lock LED on a MBP 4,1 (Penryn). It does fix F11 key, but has no effect on the LED. Rebooting does not help. 

Must be something else going on...

---

### Post by beauman on 2008-12-11
Ok, the wiki is for MB 4,1 not MBP 4,1. So it's a different hardware.
It's still hard to believe. Do you do any other tweaking with the
keyboard with pommed or xmodmap?

---

### Post by hyperboloid on 2008-12-11
> **beauman said:**
> Ok, the wiki is for MB 4,1 not MBP 4,1. So it's a different hardware.
It's still hard to believe. Do you do any other tweaking with the
keyboard with pommed or xmodmap?

Pommed is not installed.

I am indeed remapping the caps lock key to emulate Mouse button 2, using xmodmap. And when I remove that remapping, my caps lock LED functions normally again! 

Good call - that was the problem. So the instruction to remove mouseemu works for the MBP 4,1 as well. This is settled. Thanks, Beauman.

---

### Post by cyberdork33 on 2008-12-12
please mark this thread as solved from the thread tools menu at the top of the page.

---

