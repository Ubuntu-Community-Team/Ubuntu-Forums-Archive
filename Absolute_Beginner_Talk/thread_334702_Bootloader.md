---
title: "Bootloader"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by abedam on 2007-01-09
Hello,

Im trying to edit my boot options to load windows first, but my keyboard seem to be disabled - i can't navigate or edit or do anything - it just automatically logs me into ubuntu. I tried to look for a bootloader in ubuntu, but there's none in systems tools -> boot as the manual suggests. Where can i download a good bootloader that i can use?

---

### Post by meng on 2007-01-09
Are you seeing the grub menu at all? Does pressing ESC help? What sort of keyboard is this? Can you post the contents of your menu.lst here please:
cat /boot/grub/menu.lst

---

### Post by abedam on 2007-01-09
Thanks for getting back, - i can see the GRUB menu, just can't do anything with it. Haven't tried pressing ESC yet, will do that and post the contents here.

---

### Post by abedam on 2007-01-09
> **meng said:**
>  Does pressing ESC help?


Just out of curiousity, what will ESC do? {i'm not near the 'ubuntu' computer now}.

---

### Post by Duck2006 on 2007-01-09
Are you using a USB keyboard?

esc will bring up the the menu if it is hidden.

---

### Post by meng on 2007-01-09
Ditto duck2006 comment on the function os ESC. Hopefully, your problem is just due to the timeout set too fast on your grub menu.

---

