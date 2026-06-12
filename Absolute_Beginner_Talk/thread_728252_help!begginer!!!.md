---
title: "help!begginer!!!"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by xcloud on 2008-03-18
i just install ubuntu and  i change resolution and after logging off,when i logging in there is a black screen and commands saying:
"*starting anac(h)ronisticcron anacron
 *starting deferred execution scheduler atd
 *starting periodic command schduler crond
 *checking battery state...
*Running local boot scripts (/etc/rc.local)"
    What can i do??????please help,thx.

---

### Post by insineratehymn on 2008-03-18
That sounds... normal.

Does that ever stop?
What version of Ubuntu are you running?
What kind of computer did you install it on?
Did you download it or get a CD mailed to you?

Gotta give us a little more information before we can help you, because like I said...
What you just posted looks completely normal.

---

### Post by xcloud on 2008-03-18
no it doesn't stops 
Ubuntu 7.10
AMD athlon64 x2 dual core 4600+,1gb ram
i downloaded it

---

### Post by igknighted on 2008-03-18
Sounds like you selected a resolution that your monitor cannot display (or your graphics card with current driver).  Hit ctrl+alt+F1 to get to a terminal prompt and login.  Run the command 'sudo dpkg-reconfigure -phigh xserver-xorg', enter your password again, and select a lower resolution.  Then install the drivers for your graphics card (what is it? we may be able to help here too) and Ubuntu should select your best resolution.

---

### Post by Therion on 2008-03-18
Sounds like the OP may have the boot-splash blues.  Removing **quiet** and **splash** from menu.lst normally solves that problem...

Boot up your PC.
When you see GRUB hit the ESCape key.
Keep your selection on the first line of the menu and hit "E" to enter Edit mode.
Using the arrow keys, go to the second line of text and and hit "E" again to edit this line.
Delete the words **splash** and **quiet**.
Hit “Enter”, then "B" to continue booting.
Once you're in Ubuntu, open up the Terminal and enter:```
gksudo gedit /boot/grub/menu.lst
```
Find and delete the words **quiet** and **splash** from the line that starts with Kernel one more time.
Save the file, Exit… Aaaand you’re done.

---

### Post by xcloud on 2008-03-20
I'm doing the 2 options you gave me but when gets up the login,i putting the user name,and then at password everything i'm doing the keyboard is dead!!!!!only the enter key is working!

---

### Post by insineratehymn on 2008-03-22
Are you sure the keyboard is dead?

It doesn't echo anything you are typing by default; so what you are typing is not going to be shown, it is going to remain hidden but it is there, you just can't see it.

---

