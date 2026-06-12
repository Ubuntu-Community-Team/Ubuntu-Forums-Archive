---
title: "Hiding GRUB"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by SilverGoldBronze on 2008-04-01
This is annoying.

I want to hide the GRUB loader so that it boots Windows by default unless I press ESC, so I opened menu.lst in the /boot/grub folder, and I changed the parts of "Default     0" to "Default       4" and "#hiddenmenu" to "hiddenmenu".

I calmly proceeded to save the document, when it told me I did not have the required permissions to save the document.

That's where the trouble started.

I shutdown Ubuntu, booted XP, went online, and found out that I would have to input the following commands into the Terminal:

[I]cd /boot/grub
sudo chmod +w menu.lst
[/I]


The problem there is that it won't work, or, if I try it without the "sudo" part, it tells me I don't have the required permissions to change the file permissions.

Help me, please.

---

### Post by joshrobinson on 2008-04-01
```
sudo gedit /boot/grub/menu.lst
```

should give you permissions to make your changes

---

