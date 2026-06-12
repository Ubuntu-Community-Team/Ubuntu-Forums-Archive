---
title: "not getting very far"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by JamesDalley on 2006-07-20
I boot from the cd and select start or install. It then says something like loading linux or kernel. Then all goes fuzzy:(  looks like the next menu appears but its just to fuzzy to see. Any clues?

---

### Post by nalmeth on 2006-07-20
What kind of video hardware do you have?

---

### Post by nalmeth on 2006-07-20
I just re-read your post

So it loads the kernel, (remember anything about GRUB loading) and then goes to a really fuzzy menu? Is it like the [usplash loading screen]("http://www.irmak.org/themoon/ubuntu-boot-splash2.jpg")?

When you load the LiveCD, find boot options, and put this in:
[SIZE=-1]live-expert vga=771

You will probably want the vesa driver to begin with, if things didn't work right with the default.

If you can't figure out the boot options, just let the computer sit, perhaps the loading screen is just not a good resoultion. Let it finish and get to the display 
[/SIZE]

---

### Post by monkieie on 2006-07-20
a word of warning here. I don't know whether or not it may be relevant to you, but I was having problems at first because I ran the PC via a video switch. The bummer was that while I was waiting for the CD to boot (it was an older PC) I switched over the monitor to my main PC. This resulted in the monitor not being recognized at all (either from the live CD or once installed).

If you should have such a switch, either leave the monitor on or connect the cables directly (better).

If you don't have such a switch, forget that I ever opened my trap.

---

### Post by OU812 on 2006-07-20
Maybe a bad burn. I had trouble with my first ubuntu cd - tried to burn it in *** linux using *** to burn it (no names, please). And the cd wouldn't get past the kernel thing. So I booted windows and burned it with nero. That worked. My guess is you may have a bad burn.

john

---

### Post by az on 2006-07-20
> **JamesDalley said:**
> I boot from the cd and select start or install. It then says something like loading linux or kernel. Then all goes fuzzy:(  looks like the next menu appears but its just to fuzzy to see. Any clues?

Look for the boot parameters in the help menu.  Look for "framebuffer".  I forget which prompts are available...  But they are mentioned in the help (F1, F2, F3 and so on...)

---

