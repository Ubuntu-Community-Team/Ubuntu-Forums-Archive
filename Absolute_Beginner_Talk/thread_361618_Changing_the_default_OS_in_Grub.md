---
title: "Changing the default OS in Grub"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Jimpdx on 2007-02-14
Hello, all.  For my wife's benefit, I would like to change the default OS back to XP.  I found some documentation on this, but I'm not sure about WHERE I'm supposed to perform this task.  Terminal?  From Grub?  If it's inside Grub, do I use the "edit" or "command line" to initiate?  I know these are basic questions, but I'm a little out of my depth on this one.

Thanks!

---

### Post by taurus on 2007-02-14
You need to edit /boot/grub/menu.lst and change the **default **from 0 to 3 (assuming your XP is the 4th entry in there).

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Maestro23 on 2007-02-14
> **Jimpdx said:**
> Hello, all.  For my wife's benefit, I would like to change the default OS back to XP.  I found some documentation on this, but I'm not sure about WHERE I'm supposed to perform this task.  Terminal?  From Grub?  If it's inside Grub, do I use the "edit" or "command line" to initiate?  I know these are basic questions, but I'm a little out of my depth on this one.

Thanks!

Need to open a terminal.

You have to edit your [COLOR="Red"]/boot/grub/menu.lst[/COLOR] (lowercase L).

Using a text editor (gedit, vi, nano, mousepad, vim, etc..)

I use nano a lot. So for me it would be:

sudo nano -B /boot/grub/menu.lst (-B) makes a backup copy of the file before editing.

Can you post the link to the documentation you are taking about?

*Edit: Taurus already got you..

---

### Post by Patrick K on 2007-02-14
Just to add to this. The numbering starts a "0", so the first entry is "0". The divider that says 'other operating systems" counts as one of the entries, so is numbered, also.

---

### Post by Jimpdx on 2007-02-14
Here's the link:  help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html


The lower-case L info was helpful---I thought it was a "one".  I tried doing this, but I'm not certain what number is correct to replace Zero.  Can I just use "X_sequence", or is that just a generic designation?

---

### Post by meng on 2007-02-14
Each grub boot entry has a stanza in menu.lst, the first one is number 0, the second one is number 1, etc. This has already been pointed out in the replies - read carefully!

---

### Post by Jimpdx on 2007-02-14
Situation resolved!  Thank you all for the assistance.  Sorry that the link didn't appear as html--I'll look into that.  I would not have guessed that the "Other OS" line counted as an entry.  Thank you for that tidbit.

---

