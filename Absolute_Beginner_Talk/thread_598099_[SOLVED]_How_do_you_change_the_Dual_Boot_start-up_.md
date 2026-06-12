---
title: "[SOLVED] How do you change the Dual Boot start-up list?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by XNYE on 2007-10-31
How does one change the list order in boot list?  Right now it's in the order of ubuntu, ubunt-safe, mem-test, then xp pro.

I would like XP Pro to be the first in the list then ubuntu... then the rest.

If my question isn't clear, which may certainly be the case, let me know.

Thanks

---

### Post by mikewhatever on 2007-10-31
In fact, you do not need to change the order of the entries, but simple the operating system that boots by default.
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

If you are confused with that, post the output of the following command
> cat /boot/grub/menu.lst

---

### Post by macogw on 2007-10-31
It would be a bad idea to put XP at the top of the list in menu.lst (inside the Debian automagic thing) because that'd make XP get overwritten (read: disappear) when you get a kernel upgrade.  The best thing to do is run:
```
gksu gedit /boot/grub/menu.lst
```
and change the part where it says
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0
so that the last line says 3 instead of 0 (ubuntu is 0, ubuntu recovery is 1, memtest is 2, and xp is 3), then also change 
> # should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
to true so that when you get an Ubuntu kernel update, it'll automatically change the 3 to 5 (since Ubuntu will add another regular and another recovery entry ahead of it).  

When you are done, save it and run ```
sudo update-grub
```

XP will still be at the bottom, but it will boot by default.

---

### Post by logos34 on 2007-10-31
Copy and paste it just above this line:

**## ## End Default Options ##**

(if you put it inside the 'automagic' section it will be deleted at next kernel update)

Or you could set windows as default boot:

> default 4

It will boot first by default but remain at bottom of menu

---

### Post by macogw on 2007-10-31
> **logos34 said:**
> Copy and paste it just above this line:

**## ## End Default Options ##**

(if you put it inside the 'automagic' section it will be deleted at next kernel update)

Just about "End Default Options" *is* inside the "automagic" section, so this is a bad idea because it will delete Windows from the list.
> 
Or you could set windows as default boot:



It will boot first by default but remain at bottom of menu

Default starts numbering at 0, so XP is 3.

---

### Post by logos34 on 2007-10-31
> **macogw said:**
> Just about "End Default Options" *is* inside the "automagic" section, so this is a bad idea because it will delete Windows from the list.

right, my mistake, I meant this line:

### BEGIN AUTOMAGIC KERNELS LIST


> Default starts numbering at 0, so XP is 3.

You're forgetting this line:
[B]
title		Other operating systems:[/B]

It counts all 'title' lines (without #'s), so it should be '4'.

---

### Post by macogw on 2007-10-31
> **logos34 said:**
> right, my mistake, I meant this line:

### BEGIN AUTOMAGIC KERNELS LIST




You're forgetting this line:
[B]
title		Other operating systems:[/B]

It counts all 'title' lines (without #'s), so it should be '4'.
O_o that's positively silly!  Why would they do that?  That's a good way to be confusing :(

---

### Post by XNYE on 2007-10-31
> **macogw said:**
> It would be a bad idea to put XP at the top of the list in menu.lst (inside the Debian automagic thing) because that'd make XP get overwritten (read: disappear) when you get a kernel upgrade.  The best thing to do is run:
```
gksu gedit /boot/grub/menu.lst
```
and change the part where it says

so that the last line says 3 instead of 0 (ubuntu is 0, ubuntu recovery is 1, memtest is 2, and xp is 3), then also change 

to true so that when you get an Ubuntu kernel update, it'll automatically change the 3 to 5 (since Ubuntu will add another regular and another recovery entry ahead of it).  

When you are done, save it and run ```
sudo update-grub
```

XP will still be at the bottom, but it will boot by default.


What do you mean "It'll automatically change the 3 to 5?  ( I guess I'm confused after the last few posts ).. Do you mean 4 to 6?(it'll change the default to 4[which is XP] to 6, after the update?)

---

### Post by XNYE on 2007-10-31
> **logos34 said:**
> Copy and paste it just above this line:

**## ## End Default Options ##**

(if you put it inside the 'automagic' section it will be deleted at next kernel update)

Or you could set windows as default boot:



It will boot first by default but remain at bottom of menu

Copy and paste what?

---

### Post by XNYE on 2007-10-31
So far I changed the default from '0' to '4' then set the other parameter from 'false' to 'true.'  Lastly I did the 'sudo update-grub.'  

That should do it right?? It worked... have I done everything properly so that when I get a kernel update.. everything works out?

Thanks for the help guys.

---

### Post by macogw on 2007-10-31
Yeah that should work, and yes I guess it's that it'd change 4 to 6

---

### Post by anaconda on 2007-10-31
yep that is it.. 

But you wouldn't have needed to do the "sudo update-grub" 
It wasn't necessary.  It is usually done only after kernel update, And even then it is done automagically. 

Wonder when recommending the sudo update-grup started? I have seen the same in several threads now.

---

### Post by macogw on 2007-10-31
Some of the automagic change things require it (like changing what the default kernel boot options should be and applying them to all kernels listed), but I don't know specifically which ones, so I just suggest it to be safe.  It doesn't hurt anything to run it.

---

### Post by XNYE on 2007-10-31
Thanks a lot for the help guys.. I'll mark this as solved.

I hope to make the default boot Ubuntu once I get all the apps I need to use, to work properly.

---

