---
title: "Windows first in grub"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Bartender on 2006-10-01
I apologize.  Know this has been covered but can't find.  How do you tweak grub so Windows is default OS?

---

### Post by xtacocorex on 2006-10-01
```
sudo nano -B /boot/grub/menu.lst
```
There is an option to set the default boot option and the numbers start at zero.  Change that to the number that Windows option is and then you're set.

---

### Post by PPAAUULL on 2006-10-01
I think there is a Script called GRUB Ed that can do that all for you. Let me try to find it.

---

### Post by steve.horsley on 2006-10-01
I'm sure you really don't want to to that. ;)

But if you do, 
**gksudo gedit /boot/grub/menu.lst**
and either move the windows stanza to it is before the automagic section so that windows is the first OS listed. Or change the line that says "default 0" and change the 0 to the option number that windows appears at on the boot screen.

Edit: Hey! Whan I started typing that reply, there were no replies in the thread.

---

### Post by PPAAUULL on 2006-10-01
I found the link for you. Here [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

### Post by Malac on 2006-10-01
Find the lines
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0
```
in /boot/grub/menu.lst
and change the number after "default" to the number windows is at starting at 0.
e.g. with this as a grub menu windows would be "**default       3**"

[B]Ubuntu/Linux, kernel 2.6.15-27-686
Ubuntu/Linux, kernel 2.6.15-27-686 (recovery mode)
 Ubuntu/Linux, kernel memtest86+
[/B]** Microsoft Windows XP Professional**

---

### Post by Bartender on 2006-10-01
Wow, thanks everyone.  That was quick.  I knew if I got any responses at all someone would razz me about putting Windows first.  It's not for me!  For a friend I'm trying to convert.  :D

---

### Post by Bigbluecat on 2006-10-01
One point to note - if you leave the windows entry after the automagic entries it's number will change after kernel updates.

So it may be entry three now but after a kernel upgrade it may become entry 5. In this case the default would no longer work.

There are two ways to tackle this.

1. Move the windows entry above the automagic section and change to default number appropriately.

2.Set the updatedefaultentry in menu.lst to true. This will automatically track your default entry

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

If it's for a first time user and friend I'd recommend taking one of these approachs or they are liable to accept a kernel update and lose windows.

---

### Post by Bartender on 2006-10-02
Thanks, Blue -
That's exactly what would happen - he'd upgrade to Eft, Windows would "disappear", and there'd be more gray hairs before we figured it out...

---

