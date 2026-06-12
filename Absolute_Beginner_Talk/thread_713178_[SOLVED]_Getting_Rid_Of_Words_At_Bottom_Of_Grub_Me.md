---
title: "[SOLVED] Getting Rid Of Words At Bottom Of Grub Menu?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-02
Hello all.  I have a question I could not find an answer for in the Search section.

I have my grub screen set up the way I like it, with an image that works well for my system.  The only thing is, the words at the bottom of the selection box just get in the way.  You know, the words that start out with " Use the [up] and [down] keys to select which entry is highlighted. ~~~~~~~~ (and ends with) ~~~~ or 'c' for a command line.

Would anyone know of a way for me to remove those instructions?  I've looked in the menu.lst file, but I do not see them there, or I could just comment them out.

Any ideas??

FwF

---

### Post by justleen on 2008-03-02
```

leen@just-ux:/boot/grub$ grep keys *
Binary file stage2 matches
leen@just-ux:/boot/grub$ strings stage2 |grep keys
    Use the %c and %c keys to select which entry is highlighted.

```

its in /boot/grub/stage2. This is a binary file though! You could edit it with a  editor orso, but i'd strongly advise you not to alter this, unles you know what your doing (or, unless you know how to restore everything if it goes wrong..)


its on these lines:
    > 386 ^@^MPress `ESC' to enter the menu... %d   ^@
    387     Use the %c and %c keys to select which entry is highlighted.
    388 ^@    Press enter to boot the selected OS or 'p' to enter a
    389     password to unlock the next set of features.^@    Press enter to boot the selected OS, 'e' to edit the
    390     commands before booting, or 'c' for a command-line.^@    Press 'b' to boot, 'e' to edit the selected command in the
    391     boot sequence, 'c' for a command-line, 'o' to open a new line
    392     after ('O' for before) the selected line, 'd' to remove the
    393     selected line, or escape to go back to the main menu.^@


---

### Post by FreewareFan on 2008-03-02
Well, I've done quite a bit of hex editing within the Windows environment, so I think I'll give this a shot.  Should be just a matter of replacing the characters with place holders with a value of 20.   I'll post back the results, if I can still boot into Ubuntu that is...  

Many thanks for the fast reply!!

FwF

---

### Post by FreewareFan on 2008-03-02
UPDATE: Hey, it worked very well.  I now have a nice clean grub screen to boot from, without all that extra verbage on the bottom.  

Many thanks for pointing me in the right direction!

FwF

---

