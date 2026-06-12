---
title: "Menu.lst jacked up!"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-06-30
Howdy,

My menu.lst somehow became extremely jacked up from kernel upgrades and self-modifying to change the order.  All of the backups of the menu.lst are also jacked.  Is there anyway to recreate the grub by a command?

Thanks for your help,
Will

---

### Post by JayTee on 2007-06-30
Can you post the "jacked up" menu.lst? That would make it a bit easier to help you figure out what's wrong and how to fix it.

---

### Post by willz06jw on 2007-06-30
I was asking not how to fix the existing menu.lst, but if there was a command to create a new one.  But, here is the existing menu.lst file if it will help.

Thanks
Willz06jw

---

### Post by davidjmayo on 2007-06-30
I have seen this before and I think it's what you need. Be warned I have not tried it myself as I haven't had a grub problem (yet)

> 
reinstall grub / lilo
--------------------------
Code:

sudo apt-get remove grub --purge
sudo apt-get install grub

---

### Post by JayTee on 2007-07-01
You can download the Super Grub Disk and run that to repair your GRUB or you can replace your menu.lst file with this one which is an edit of yours. Yours had so many duplicate entries in it.

---

### Post by Tomosaur on 2007-07-01
No no no no, do not reinsall grub. Use the following command:

```

sudo update-grub
```

---

### Post by willz06jw on 2007-07-02
Whew, glad I waited on that!  Thanks everyone for all of your help

Will

---

### Post by davidjmayo on 2007-07-02
Tomosaur

just curious (I said I never used it before) please can you tell me why it's a no no no no?

BTW I won't post it as a reply again.

Will, I didn't know. Glad you didn't do it

---

### Post by willz06jw on 2007-07-07
No problem, thanks for you reply!  Any help is better than no help.

---

