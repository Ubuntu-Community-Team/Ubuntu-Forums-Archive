---
title: "Grub showing multiple ubuntus"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Steel Bovine on 2007-03-01
I am dual-booting Ubuntu Edgy and Windows XP.  I don't have a "problem" so much as an "issue," in the Grub boot manager I see Ubuntu, Ubuntu mem test, Ubuntu, Ubuntu mem test, and Windows XP.  I don't understand why it is duplicating.  Really I just want to select between Ubuntu and XP (and what would be /really/ nice is if it would just load whatever OS I was last using by default unless I hold a button to select).

Ideas?

---

### Post by nereid on 2007-03-01
For every differernt kernel you have installed will be a pair of entries created. Just remove the older kernel and on you go.

You can also hide GRUB (you'll still see a countdown). Just add this to your /boot/grub/menu.lst

```

hiddenmenu

```

---

### Post by maniacmusician on 2007-03-01
> **nereid said:**
> For every differernt kernel you have installed will be a pair of entries created. Just remove the older kernel and on you go.

You can also hide GRUB (you'll still see a countdown). Just add this to your /boot/grub/menu.lst

```

hiddenmenu

```
I don't think he wants that. If I'm reading correctly, he wants a choice between WinXP and Ubuntu

---

### Post by benfindlay on 2007-03-01
If I understand you correctly, the multiple entries in your GRUB list are due to the fact that yu updated the kernel. The old kernel is kept in the list so you can boot it in case of problems when you upgrade. Means your "old" and working setup is preserved in case of incompatibilities.

Think it's more of a problem on less mainstream and older machines. Have an old laptop that wont work with any kernel newer than the 1 built into 5.10. Took me ages to figure out that that was the problem. Needless to say, I just reinstalled and locked the versions in Synaptic and all was well!

Also, you can hide the GRUB menu as suggested, or set it to a shorter timeout, or just leave the list as is. My PC wont show the list unless I press a key to display it, and I only have an interval of a couple of seconds after turning on to do that! As far as I am aware it will not load the last OS for you, but you can set it to boot whichever you want by default!

Hope this helps!

---

### Post by Steel Bovine on 2007-03-01
Thanks, removing the old one worked.  I now only have "Ubuntu" "Ubuntu mem test" and XP.  I could live without being able to select the memory test.

Deviating from my original topic, though, is my other request possible?  If I'm in Windows, and I need to restart (because I installed a program or new hardware) I want to go back into Windows nearly all the time.  But since I only use Windows for gaming, I don't want Windows to always be the default.  -- Essentially I'd like the boot manager to be hidden and have the default set to whatever the last operating system I used.  Possible?

---

### Post by janz84 on 2007-03-01
change all instances of the "default" entry in your menu.lst to "savedefault."

---

### Post by undertakingyou on 2007-03-01
> **janz84 said:**
> change all instances of the "default" entry in your menu.lst to "savedefault."

Just wondering, should it be savedefault or just saved?  The entry in the menu looks like this:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify[COLOR="Red"] 'saved' [/COLOR]instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

As long as the later boot entries say savedefault as one of their lines it should go to that if you put saved.

---

### Post by Steel Bovine on 2007-03-01
> **janz84 said:**
> change all instances of the "default" entry in your menu.lst to "savedefault."

Thank you!  This is the best community ever.

---

### Post by tworthen on 2007-03-01
> **Steel Bovine said:**
> I am dual-booting Ubuntu Edgy and Windows XP.  I don't have a "problem" so much as an "issue," in the Grub boot manager I see Ubuntu, Ubuntu mem test, Ubuntu, Ubuntu mem test, and Windows XP.  I don't understand why it is duplicating.  Really I just want to select between Ubuntu and XP (and what would be /really/ nice is if it would just load whatever OS I was last using by default unless I hold a button to select).

Ideas?

I have the same issue, this happens every time I use the updates feature (the white star on a orange background at the top of the screen). My solution is to keep an original copy of the /boot/grub/menu.lst and then replace the modified menu.lst after I do an update. Its a kluge but it works. When I submitted my question about this I got a number of "you're doing something wrong" replies.

---

### Post by Tomosaur on 2007-03-01
By default grub is set to show all available kernels. You can reduce it so it shows only the latest one. To do this, hit alt+f2 and type:
```

gksudo gedit /boot/grub/menu.lst

```

Then hit ctrl+f and type 'howmany' (without the quotes). The highlighted line should say 'howmany=all'. Change it to 'howmany=1'. Save and exit. Next time you reboot you should only have one kernel listed. If you update your kernel, only the newest version will be shown.

Alternatively, check the link in my sig.

---

