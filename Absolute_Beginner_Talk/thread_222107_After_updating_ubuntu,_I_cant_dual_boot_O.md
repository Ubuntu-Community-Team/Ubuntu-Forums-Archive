---
title: "After updating ubuntu, I cant dual boot :O"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-24
Today when i started up ubuntu, it told me it wanted to update ubuntu, so I let it update. Then it told me to restart, so I did so. So when I got to the screen, were I normally would choose if I want to enter Windows or Ubuntu, I could only choose ubuntu. So know I cant enter Windows. How can I fix this?

---

### Post by philippe_carlo on 2006-07-24
Add the following BELOW the line saying
"### END DEBIAN AUTOMAGIC KERNELS LIST"
in /boot/grub/menu.lst

```

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Adding it below that line will keep it from being removed upon the next update.

---

### Post by jincast90 on 2006-07-24
Ok this is really weird. I have used this command:
/boot/grub/menu.lst

several times without any problem, but this time I typed it in the terminal, it told me this:

bash: /boot/grub/menu.lst: Permission denied

Now whats this about?

Please help :(

---

### Post by SilverBear on 2006-07-24
> Ok this is really weird. I have used this command:
/boot/grub/menu.lst

several times without any problem, but this time I typed it in the terminal, it told me this:

bash: /boot/grub/menu.lst: Permission denied

Now whats this about?

You're not the root so you need superuser status to edit a file owned by root. type:

gksudo gedit /boot/grub/menu.lst

...and you will have temporary permission to edit & save the file.

all the best,
SilverBear

---

