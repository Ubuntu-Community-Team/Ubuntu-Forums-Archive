---
title: "Grub shows up 2 ubuntu, Why?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by W0lf on 2007-06-28
Well I'm Dual Booting XP and Ubuntu.  I just got to sort out how to set XP as default.

usually in grub I could find four options.

1 Ubuntu
2 Ubuntu(recovery mode)
3 Memtest(or something similar)

4 Windows XP Home

The last action I did before I noticed a problem was changing my root password using the terminal(found some advice on the internet as I am an absolute Ubuntu newbie).

And now grub looks like this...

1 Ubuntu
2 Ubuntu(recovery mode)
3 Ubuntu
4 Ubuntu(recovery mode)
5 Memtest(or something similar)

6 Windows XP Home

Note: numbers don't appear in front of the names but I just put some in to show You all what I'm about.

Why is that?  What can I do to change this?

Please help.

---

### Post by cogadh on 2007-06-28
Your kernel likely got updated, that creates separate entries for each available kernel.

---

### Post by myoungf1 on 2007-06-28
More than likely you have two kernels installed now via updates.  The top most Ubuntu is the most current kernel installed.  I used Startup Manager to limit the number of kernels chosen to 1.  Not sure how to change without Startup manager but hopefully someone here in the forums knows how.  Here is the link to download Startup Manager.  It can do some cool things with Usplash screens and the look of Grub as well so check it out.  [http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

---

### Post by Celegorm on 2007-06-28
Open up a terminal window (application -> accesories -> terminal) and type ```
sudo nano /boot/grub/menu.lst
``` Enter your password when it asks. Near the beginning of the file should be a line that looks something like ```
default      0
``` though the number may not be 0. Change that number to 6 (I'm guessing this is the right number from the list of boot option you posted) and press ctrl-x to exit. The number tells the boot manager which option to use as default. If 6 isn't right, count the number of options in the menu, starting from zero, and including any lines such as "Other operating systems:" until you get to the windows entry, and that will be the number you need.

---

### Post by W0lf on 2007-06-28
Thanks, myoungf1.
If I have any problems later I'll private message You here on the forums if I may.  Shouldn't have a problem with that startup manager.  Gotta learn a little more about Ubuntu, but for now I love it, done a lil' tweaks and so far it's sweet.

EDIT:

Hey guys, thanks for all the help, but the easiest method was the Startup Manager(even though i've edited menu.lst before, I wanted to remove one kernel from the list so it's back to normal. 
THANKS A LOT.

---

### Post by Bensky on 2007-06-28
> **Celegorm said:**
> Open up a terminal window (application -> accesories -> terminal) and type ```
sudo nano /boot/grub/menu.lst
``` Enter your password when it asks. Near the beginning of the file should be a line that looks something like ```
default      0
``` though the number may not be 0. Change that number to 6 (I'm guessing this is the right number from the list of boot option you posted) and press ctrl-x to exit. The number tells the boot manager which option to use as default. If 6 isn't right, count the number of options in the menu, starting from zero, and including any lines such as "Other operating systems:" until you get to the windows entry, and that will be the number you need.

Yeah, if 6 does not work, try 5, since the counting might go like this: 0, 1, 2, 3, 4, 5.

---

### Post by Inxsible on 2007-06-28
> **Bensky said:**
> Yeah, if 6 does not work, try 5, since the counting might go like this: 0, 1, 2, 3, 4, 5.
 
 
You are right, the counting does start from 0. You also have to count the title for 'Other Operating Systems'

---

### Post by myoungf1 on 2007-06-29
> **W0lf said:**
> Thanks, myoungf1.
If I have any problems later I'll private message You here on the forums if I may.  Shouldn't have a problem with that startup manager.  Gotta learn a little more about Ubuntu, but for now I love it, done a lil' tweaks and so far it's sweet.

EDIT:

Hey guys, thanks for all the help, but the easiest method was the Startup Manager(even though i've edited menu.lst before, I wanted to remove one kernel from the list so it's back to normal. 
THANKS A LOT.

Hey glad to help out.

---

