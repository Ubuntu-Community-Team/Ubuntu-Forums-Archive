---
title: "Grub"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by darekdavis on 2007-05-07
I just recently installed Ubuntu and it is really great. I have very little knowledge of linux systems but hopefully with some playing around I'll get things figured out. Anyhow the question I have is if there is a way to go back to the windows xp bootloader instead of the grub loader, or is it possible to make windows xp the default selection within grub. The wife is complaining about the loader so I was hoping to put that fire out quickly. :) I know I can fix the mbr with the ultimate bootdisk, but I don't know how to get back into Ubuntu once I do that. Thanks for any help you can offer me.

Darek

---

### Post by xyz on 2007-05-07
Hi Derek,

First please post the output of the following command line:
```
 cat /boot/grub/menu.lst

```

---

### Post by mikewhatever on 2007-05-07
Yes, that is very easy to do. Fist back up your grub menu in case something goes wrong
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
Now, look here [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

I would also suggest hiding the menu entirely. You can still get it up by hitting Esc button, if needed. Here is how to hide it 
[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)

---

### Post by Tomosaur on 2007-05-07
Yup, it's easy. Check the link in my sig for a GUI method to do it, or follow mikewhatever's link to see how to do it via the command line.

---

