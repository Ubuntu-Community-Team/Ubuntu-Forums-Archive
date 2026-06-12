---
title: "Text-only console font"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Rednarb on 2007-10-11
I'm building a text-only Ubuntu install and would like to change the font/resolution of the text-only console. I've done it in RedHat but can't figure it out for Ubuntu. Any pointers?

aTdHvAaNnKcSe!

Eric

---

### Post by steve.horsley on 2007-10-11
I believe you add a clause like
vga=832
at the end of the kernel line in /boot/grub/menu.lst. Beware, I don't know what the number are (google for them) and although they're 3 digit numbers, I only guessed at 823 above.

---

### Post by Rednarb on 2007-10-12
> **steve.horsley said:**
> I believe you add a clause like
vga=832
at the end of the kernel line in /boot/grub/menu.lst. Beware, I don't know what the number are (google for them) and although they're 3 digit numbers, I only guessed at 823 above.

Awesome!

Found details on the different resolutions at [http://ruslug.rutgers.edu/~mcgrof/grub-images/configs/linux/menu.lst](http://ruslug.rutgers.edu/~mcgrof/grub-images/configs/linux/menu.lst)

Thanks so much for the help!

Eric

---

