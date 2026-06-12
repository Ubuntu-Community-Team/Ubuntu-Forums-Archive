---
title: "Question about Feisty splash screen"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-08-06
I've just got Feisty loaded and running (at last).

I previously used Dapper for a few months and I liked the Ubuntu screen on start up as it showed what was happening in scrolling lines of text as well as the progress bar.

Feisty only shows the progress bar.

Is there any way of also showing the scrolling text lines as well.

Thanks,
David

---

### Post by Rocket2DMn on 2007-08-06
Yes.  You will need to edit your menu.lst file for GRUB.  We'll make a backup first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
For the kernel you boot from, remove the term "quiet" from the kernel line, but leave "splash".  Now when you boot from that kernel you should have the splash screen with the text at the bottom telling you what's happening.

---

### Post by David Floyd on 2007-08-06
> **Rocket2DMn said:**
> Yes.  You will need to edit your menu.lst file for GRUB.  We'll make a backup first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
For the kernel you boot from, remove the term "quiet" from the kernel line, but leave "splash".  Now when you boot from that kernel you should have the splash screen with the text at the bottom telling you what's happening.

Thanks very much, that was what I was looking for :)  (except that I don't like blue text on black background) :( 

David

---

### Post by Rocket2DMn on 2007-08-06
If you remove the "splash" as well it will give you straight text - white on black.  I gave that a try, too, but I preferred to keep the splash with the text at the bottom.  Removing "splash" gives more information, but I didn't like it as much.  Feel free to try it out, you might prefer it.

---

