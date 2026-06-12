---
title: "Grub Automagic Options Editing Rule?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by thedarky on 2007-10-24
Howdy,  may I please have a little help understanding how to set a default option in Grub?

The option I want to set is between the ###automagic kernels list comment markers and I'm not quite sure whether the instructions mean to leave the single # in front of the value that I'm changing - or not.

The instructions read:

> ## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

Does this mean do not uncomment the default options? OR do not uncomment any line except the default options?

On balance, I read it as an instruction to leave all #s in place, even the default option lines.

I'd be happy to experiment with anything EXCEPT booting :-)

---

### Post by thedarky on 2007-10-24
Ah well, I found the time and gave myself a Grub 101 from [**The Grub Page**]("http://http://users.bigpond.net.au/hermanzone/p15.htm")

Solved and thanks Herman.   A person doesn't  touch any #s inside the Automagic zone.

---

