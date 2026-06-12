---
title: "Grub problem.. Says it can't find my ubuntu partition."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-09-13
So I am running grub from the command line, I was told that i need to say:

sudo grub.. okay
root(hd0,1)      ... fine
setup(hd0)        ... ERROR!!

The error I get at the setup line is:
"Error 17: Cannot mount selected partition"
But sda2 IS my ubuntu / partition!!

Why doesn't grub see this! I am having a much worse problem but it seems if i can figure out why its doing this, i might fix it!

---

### Post by systemintheglitch on 2007-09-14
Any takers?>

I feal like I just ruined my new laptop!

---

### Post by systemintheglitch on 2007-09-14
eh.

i guesse this isn't the problem..

Allthough it's wierd.


grub thinks that my sda2 is called (hd0,2)

shouldn't it be (hd0,1)???
It bugs out if i tell it (hd0,1) but totally goes along fine if i specify hd0,2, and it grabs my menu.lst from sda2!!

man.. Grub is a pain.

---

### Post by louieb on 2007-09-14
Check the /boot/grub.device.map file. I'd think sda2 would be (hd0,1) too.  but looks like you have the exception that proves the rule. :confused:

---

