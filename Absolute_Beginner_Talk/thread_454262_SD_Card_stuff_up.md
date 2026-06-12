---
title: "SD Card stuff up"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Muntted on 2007-05-25
Ok.
I am trying to get amarok to work with my nokia N73 and its memory card.
In the process of trying this I right clicked on the memory card on the desktop clicked properties then edited some of its mounting properties.

Now it is not mounting - says something about the mountpoint cannot contain certain characters.

Any suggestions on how to fix this and what the correct settings would be to be able to read, write and execute from this SD card?

Cheers
Muntted

---

### Post by tgalati4 on 2007-05-25
You might have to reformat the card from within the phone.  Most phones have locking characteristics that prevent you from doing anything neat with the phone.  The providers want you to purchase their music over the air using their overpriced data plans.

It's possible that the FAT got scrambled (therefore unrecognizable characters).  You can try to run sudo fsck on it and see what it says.

Drag and drop files sometimes works, but be sure to leave the phone plugged in a long time because file transfers can take a long time and Nautilus will show that files have transfered when they really haven't.

When you delete files, they get put in .Trash (on the phone), but then you have to manually empty the trash with a sudo rm -r .Trash (while at the root of the phone directory).  I haven't figured out how to change this behavior or tell Nautilus not to use .Trash at all.

If you can read and write files to the phone then you are head of the curve.

Good luck.

---

### Post by Inxsible on 2007-05-25
Hey Muntted,
 
Could you tell me what packages you installed to get your SD Card working?
 
Also, if you have a 5-in-1 reader, do your Memory Stick and xD cards work too?

---

### Post by Muntted on 2007-05-25
> **tgalati4 said:**
> You might have to reformat the card from within the phone.  Most phones have locking characteristics that prevent you from doing anything neat with the phone.  The providers want you to purchase their music over the air using their overpriced data plans.

It's possible that the FAT got scrambled (therefore unrecognizable characters).  You can try to run sudo fsck on it and see what it says.

Drag and drop files sometimes works, but be sure to leave the phone plugged in a long time because file transfers can take a long time and Nautilus will show that files have transfered when they really haven't.

When you delete files, they get put in .Trash (on the phone), but then you have to manually empty the trash with a sudo rm -r .Trash (while at the root of the phone directory).  I haven't figured out how to change this behavior or tell Nautilus not to use .Trash at all.

If you can read and write files to the phone then you are head of the curve.

Good luck.

The memory card still works on the phone fine. Its just when I changed the mount settings in that properties panel it will not show up. I think I tried to mount it to "Nokia Card" which may be a no no.

> **Inxsible said:**
> Hey Muntted,
 
Could you tell me what packages you installed to get your SD Card working?
 
Also, if you have a 5-in-1 reader, do your Memory Stick and xD cards work too?

It started working of its own accord. I run 7.10 with everything updated.

---

