---
title: "[SOLVED] (Gusty) When I turn on my computer, the &amp;quot;select kernel&amp;quot; window appears"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-24
Well, happens that each time I turn on my computer, a "select kernel" window appears (to select options like booting on safe mode) and then, when I select the normal one, boots into gusty. I before had Feisty and this didn't happen. What can it be?

---

### Post by n3tfury on 2007-10-24
fresh install or upgrade?  i think if you upgrade you'll see that.  it's normal on my box.

---

### Post by NilsE on 2007-10-24
There are options you can set in the /boot/grub/menu.lst to change how it displays


default		0   --  selects the first entry in the list at the bottom of the file. 1 for the 2nd etc.


timeout		3  -- The number of seconds the boot menu will display before processing the default


hiddenmenu -- if this is commented with a # in front of it remove the # and you will only see the message that it is booting and that you can hit esc to see the menu

I suspect that hiddenmenu is commented out if you see it each time.

---

### Post by Fixman on 2007-10-26
Thanks a lot, NilsE, it worked

---

