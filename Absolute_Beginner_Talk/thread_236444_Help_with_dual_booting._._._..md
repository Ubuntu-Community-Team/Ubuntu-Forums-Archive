---
title: "Help with dual booting. . . ."
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by JohnJackett on 2006-08-14
I've just upgraded my pc,  and I installed Ubuntu 6.06.  

It works wonderfully!!!

Do to school,  (And my daughter's games)  I need to dual boot with Windows XP.

What do I do? 

I know to resize the partition,  and how to install Windows. . . 

I'm totally lost with the dual boot stuff.  How do I set it up to dual boot?

-John

---

### Post by Tomosaur on 2006-08-14
Erk.
You should really have installed Windows first. If you install it now, you will lose Grub, and won't be able to access Ubuntu. Windows also dislikes being on any partition other than the 1st, which can be problematic. I would suggest you reformat, install Windows, then install Ubuntu - since it's a new PC, I assume you won't have anything you can't afford to lose on it yet.

---

### Post by JohnJackett on 2006-08-14
Thanks a lot!!

i'll format,  and reinstall,  Windows 1st.


-John

---

### Post by tylerjames on 2006-08-15
ugh.... 

please tell me this isn't the only solution!
i attempted to install windows first last night... then as i was using the dapper installer to resize my windows partition (so that i could stick ubuntu in there) it messed up, corrupted my windows install, and i didn't have anything.... so this time i installed ubuntu first and then windows..... 

that worked... except (as mentioned above) i now have no grub menu and am not really sure how to get it back.... windows would be much nicer if it just learned to coexist!!

any ideas?

---

### Post by Tomosaur on 2006-08-15
It's not the only solution, but it is the easiest :P

You can re-install Grub from the LiveCD, there's a how-to on here somewhere, so I'd just pop a few words into the search box, but it's just that the installer doesn't specifically tell you when/where it's installing Grub, so it get's confusing.

---

### Post by tylerjames on 2006-08-15
haha.. thanks.. i'm looking forward to this :---) 

this whole problem started because i tried to install fedora core 5 because i'm doing some work with a group of people who want to use it (for some reason)..... what a mistake

---

### Post by kiwi_bloke on 2006-08-15
The HOWTO you want is [here]("http://www.ubuntuforums.org/showthread.php?t=224351"). Take it step by step.

---

