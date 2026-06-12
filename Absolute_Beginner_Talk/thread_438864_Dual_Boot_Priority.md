---
title: "Dual Boot Priority"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Snoo on 2007-05-10
Hi
I'm running Win XP and Ubuntu Edgy.

Can anybody tell me how to change the boot up so windows is the default OS and not Edgy?

Thanks.

---

### Post by Tomosaur on 2007-05-10
You can do it by the following method:

Hit alt+f2, and type:
```

gksudo gedit /boot/grub/menu.lst

```

When the text file opens up, there is a line a few lines from the top which says 'default 0'. Change the zero to whichever line it is you want to boot. Line 0 is the FIRST line in the menu, line 2 is 1, etc. Remember that the 'other operating systems' line IS included in the count. Once you're done, save and reboot, it should be automatically into whichever line you wanted.

Alternatively, check the link in my sig for a GUI method to do it.

---

### Post by Tux Aubrey on 2007-05-10
Two ways to make sure you have the "right" number for the "default" line grub's menu.lst:

1. Reboot and count the number of times you have to press the down arrow key to get to the Windows XP boot option on the grub menu screen.

2. Open menu.lst and scroll down until you find the line 

## ## End Default Options ##

There will then be groups of lines with the first line of each group starting with "title"

Count the number of lines starting with "title" until you reach the group that refers to Microsoft Windows XP.

That number **minus 1** is the number you want for the "default". (ie. if Vista is in the sixth group the number you will want is 5"


And welcome to the forums.

---

