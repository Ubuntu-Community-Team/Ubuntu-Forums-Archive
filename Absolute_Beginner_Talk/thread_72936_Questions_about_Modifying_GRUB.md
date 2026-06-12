---
title: "Questions about Modifying GRUB"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by Goober on 2005-10-07
I have some questions about GRUB.  

1 - Is it possible to edit GRUB, and to change the names of what you have installed?  For instance, insteal of "Ubuntu, kernel 2.6. . . . ", I would like for it to simply say "Ubuntu 5.10 Breezy Badger" or something.  Can I do that?

2 - Can I get rid of old Ubuntu kernels?  I still have one old, outdated Kernel from both Breezy and Hoary floating around in my GRUB, and obviously I only use the most current one, how do I get rid of the old kernels, or can I?

3 - Can I change the boot priority?  I am trying to convince my parents to try Ubuntu, but they want GRUB to automatically boot into XP, instead of Ubuntu.  Can I do this?

Thanks for the help in advance.

---

### Post by aysiu on 2005-10-07
[QUOTE=Goober]I have some questions about GRUB.  

1 - Is it possible to edit GRUB, and to change the names of what you have installed?  For instance, insteal of "Ubuntu, kernel 2.6. . . . ", I would like for it to simply say "Ubuntu 5.10 Breezy Badger" or something.  Can I do that?[/quote] Yes. Modifying the title doesn't affect its booting up.

> 
2 - Can I get rid of old Ubuntu kernels?  I still have one old, outdated Kernel from both Breezy and Hoary floating around in my GRUB, and obviously I only use the most current one, how do I get rid of the old kernels, or can I? I would comment these out (put a # sign in front of the line) rather than deleting them. That way, in case you need them later, you can just uncomment them.

> 
3 - Can I change the boot priority?  I am trying to convince my parents to try Ubuntu, but they want GRUB to automatically boot into XP, instead of Ubuntu.  Can I do this? See the line that says *default 0*? That means the first entry is the default entry. *default 1* means the second entry is the default. And so on. Pick whichever number is XP to be the default.

---

### Post by zerhacke on 2005-10-07
[QUOTE=Goober]1 - Is it possible to edit GRUB, and to change the names of what you have installed?  For instance, insteal of "Ubuntu, kernel 2.6. . . . ", I would like for it to simply say "Ubuntu 5.10 Breezy Badger" or something.  Can I do that?[/QUOTE]

That's exactly the first thing I do on a new Ubuntu install's GRUB menu.lst.  It can be done by doing as the above poster outlined.  I'm just seconding his opinion.

> 3 - Can I change the boot priority?  I am trying to convince my parents to try Ubuntu, but they want GRUB to automatically boot into XP, instead of Ubuntu.  Can I do this?

Yes, again seconding an opinion.  My machine is set up to boot XP by default due to a wife who hates anything non-Microsoft.  I'm working on her, guys.

---

### Post by Goober on 2005-10-07
Erm, ok, but how do I modify GRUB?  At the beginning, when GRUB boots, or through Ubuntu, or . . . ?

It seems that for all you learn about Linux, there is always more to learn . . .

---

### Post by darkmatter on 2005-10-07
[QUOTE=Goober]Erm, ok, but how do I modify GRUB?  At the beginning, when GRUB boots, or through Ubuntu, or . . . ?

It seems that for all you learn about Linux, there is always more to learn . . .[/QUOTE]

From within Ubuntu. To modify GRUB, you need to edit /boot/grub/menu.lst. This can be done from a terminal with
```
sudo gedit /boot/grub/menu.lst
```

You can make the modification previously mentiond to the file, then save the changes. On the next boot, the changes will take effect.

Make sure you create a backup of menu.lst before you do any editing!

---

### Post by Goober on 2005-10-07
Gingers, it would be simply and easy . . . 

Thanks a lot, you guys, I can finally rename things so i can understand what they are, rather then having some funny Kernel name staring me in the face.

One last question, can I delete old Kernels?  I notice I have 2 Kernels of Hoary and Breezy, obviously the most current one, and a couple old ones, can I delete, like, just highlight and press "Delete" the old ones?

Thanks again, I'm going to restart now, time to pray I didn't mess up.

---

### Post by matthewv on 2005-10-08
[QUOTE=Goober]One last question, can I delete old Kernels?  I notice I have 2 Kernels of Hoary and Breezy, obviously the most current one, and a couple old ones, can I delete, like, just highlight and press "Delete" the old ones?
[/QUOTE]

Instead of highlighting and deleting, put a # in front of the lines that refer to that kernel. The kernel will disappear from the boot menu, and can be added again (just in case) by removing the #'s from the front of the lines

---

### Post by Goober on 2005-10-08
Ah, I see.

I succesfully got it working the way I want to.  Thanks a lot everybody for your kind and prompt help!

---

