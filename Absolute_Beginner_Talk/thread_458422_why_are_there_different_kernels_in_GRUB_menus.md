---
title: "why are there different kernels in GRUB menus?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-29
On PC#2 I have a dual boot; PC#1 is just ubuntu, so I don't get the GRUB menu. But why does PC#2 give me 4 different kernel options  two sets of  (two with the same number, where one is also marked recovery). What are they all for? And -ifthey bare useful - why don't I get them on PC#1? Alternativel, can I do away with them from PC#2 if they are not useful? Are they taking up lots of space?

---

### Post by Inxsible on 2007-05-29
I think you recently updated the machine which included kernel updates from -15 to -16. Thats why you see 4 different entries.
 
Do not delete the -15 entries yet, as many ppl have had weird issues with the -16 kernel. Keep it around until everything is settled :)

---

### Post by ginestre on 2007-05-30
Thanks.

---

### Post by evny on 2007-05-30
Thanks.  I was just wondering the same thing and found this post in a search.  I just recently updated to Feisty and now I've got six options.  It doesn't bother me but if I update a couple more times the list will get too long for to fit on the screen.  I guess at that point, I will have to edit GRUB(?)

---

### Post by Seisen on 2007-05-30
> **evny said:**
> Thanks.  I was just wondering the same thing and found this post in a search.  I just recently updated to Feisty and now I've got six options.  It doesn't bother me but if I update a couple more times the list will get too long for to fit on the screen.  I guess at that point, I will have to edit GRUB(?)

You should be able to delete at least the last set of kernel options without having any problems. That way you still have a backup kernel to use in case you run into problems.

---

### Post by quinnten83 on 2007-05-30
How do you delete them?

---

### Post by Inxsible on 2007-05-30
```
gksudo gedit /boot/grub/menu.lst
```

Remove the ones you dont want and save

---

### Post by dstew on 2007-05-30
Actually, the best way to remove the older kernels is with Synaptic. It will automatically remove them from the grub menu.lst file.

---

### Post by evny on 2007-05-30
Thanks for the quick answers!

---

### Post by Inxsible on 2007-05-30
> **dstew said:**
> Actually, the best way to remove the older kernels is with Synaptic. It will automatically remove them from the grub menu.lst file.
 
Yes, but the new kernel -16 is giving problems to a lot many folks. So it is better to keep the old kernel around until you are sure everything will work :)
 
editing the menu.lst is just to reduce the number of kernel options shown. It definitely doesn't uninstall the kernel

---

