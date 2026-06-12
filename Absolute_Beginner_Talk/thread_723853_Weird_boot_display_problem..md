---
title: "Weird boot display problem."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by alphaxxn on 2008-03-13
Hi everyone. I have tried searching about this problem to no real applicable avail. Thanks for your time in advance.

I have ran all sorts of distros on all sorts of rigs, and this problem is a new one to me. After the  Kernel Mapping - xxxxxxxx terminal post on initial bootup right after GRUB is done with it's job, the display completely turns off and does not review any post terminal stuff. As soon as xwindows is done loading into the user login it starts displaying again.

Is this a new 7.10 feature? I am new to this version of this distro, so that's what I was thinking at first because it seems almost like a feature than anything else.

If so, is there a way to turn this feature off? I prefer being able to see whats going on, and if it's not a feature at all any ideas on why this is happening?

Thanks everyone.

Cheers.

---

### Post by bazzawill on 2008-03-14
Is this to do with the boot splash screen and the quiet options ubuntu uses on boot when grub loads (press esc to load the menu if necessary) with ubuntu (not recovery) highlighted press e to edit highlight the last line which should be just quiet and press d to delete then highlight the second line press e to edit and backspace out quiet and splash see if that fixes your problem if so you can permanently edit your menu.lst file in boot/grub

---

### Post by alphaxxn on 2008-03-14
> **bazzawill said:**
> Is this to do with the boot splash screen and the quiet options ubuntu uses on boot when grub loads (press esc to load the menu if necessary) with ubuntu (not recovery) highlighted press e to edit highlight the last line which should be just quiet and press d to delete then highlight the second line press e to edit and backspace out quiet and splash see if that fixes your problem if so you can permanently edit your menu.lst file in boot/grub


Tried that to no effect.

Like I said, it's really strange to me only because the monitor itself starts blinking at me to let me know that its not receiving ANY ouput from the videocard. 

Thanks for trying, but have any other ideas?

---

### Post by alphaxxn on 2008-03-14
Any thoughts yet guys?


Thanks.

---

