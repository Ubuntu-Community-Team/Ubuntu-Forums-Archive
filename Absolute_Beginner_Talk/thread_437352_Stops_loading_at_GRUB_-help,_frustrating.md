---
title: "Stops loading at GRUB -help, frustrating"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Brip on 2007-05-08
Installed Ubuntu 7.04 using wubi last week and was working fine (dual booting with WinXP). Yesterday tried adjusted the menu.lst file to make the splash screen load up (big mistake!).
Now when I boot up, choose Ubuntu, it loads to a GRUB prompt and stops.
I found some help and can manually finish booting Ubuntu by doing the following, each line at a time:
[FONT="Courier New"]find --set-root /wubi/linux
kernel /wubi/linux find=/wubi/linux quiet ro
initrd /wubi/initrd.gz
boot[/FONT]

So, how do I get this to do it automatically again? I'm assuming it's something to do with menu.lst? the menu.lst file is still there where it should be. Do I need to recreate that file? How?

Besides this loving fast Ubuntu after sloow WinXP, but this booting issue is a pain.

---

### Post by cypherzero on 2007-05-08
Just enter what you have in menu.lst
Prepend it with 'title <whatever>'
And don't append 'boot' to it.

---

