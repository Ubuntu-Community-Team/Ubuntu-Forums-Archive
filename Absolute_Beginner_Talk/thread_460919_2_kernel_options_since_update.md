---
title: "2 kernel options since update"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by stefaan.dutry on 2007-06-01
Since the latest update i now have 2 linux kernel options.

My question is, will i have to comment or delete the lines in the grub, or will they be removed after a certain period of time?

Thx for the help in advance

---

### Post by Tux Aubrey on 2007-06-01
Grub keeps a few older kernels available on the menu just in case they are needed (eg. if an updated kernel borks your system).  The limit is set in the file /boot/grub/menu.lst (but I can't remember what the default is).  You can change it - but best to leave a couple just in case.

---

### Post by stefaan.dutry on 2007-06-01
Problem is i still have windows as my default starting system and then i'd have to add 2 to the number of the default startup object, or i'd have to move my windows reference to the very top of the page.
Therefore i now had memory test as startup :)

If i want Windows to be the first in the list then i only need to move the code in the grub file to the top, right? (and then set default to 0)

Thx for the help.

---

### Post by mcduck on 2007-06-01
> **stefaan.dutry said:**
> Problem is i still have windows as my default starting system and then i'd have to add 2 to the number of the default startup object, or i'd have to move my windows reference to the very top of the page.
Therefore i now had memory test as startup :)

If i want Windows to be the first in the list then i only need to move the code in the grub file to the top, right? (and then set default to 0)

Thx for the help.

There's also option (under dewfault options) to update the default boot value when kernel update recreates the menu.lst file. I can't check the exact line now as I'm at work now, but if you read through the menu.lst you'll find it.

Also, if you decide to just move the wndows entry, make sure you keep it outside the area in the file marked as 'AUTOMAGICK KERNEL LIST' or whatever it was called, otherwise your windows entry gets erased with the next kernel update ;)

To get rid of the old kernel entries it's best to just uninstall the old kernel versions (you can do that with Synaptic). Without entry in Grub they are pretty much just wasting your disk space, and although one kernel is not that big, if you keep all old kernels and modules after couple of updates you'll have gigabytes of useless junk..

---

### Post by stefaan.dutry on 2007-06-01
> **mcduck said:**
> There's also option (under dewfault options) to update the default boot value when kernel update recreates the menu.lst file. I can't check the exact line now as I'm at work now, but if you read through the menu.lst you'll find it.

I will try that.  I'll get back to this post when I have, since i'm not at home right now, i suggest not waiting for it :p

---

### Post by Tux Aubrey on 2007-06-01
Here's how to edit menu.lst to move the windows boot option to the top of the list and have it as default:

open terminal and copy this:
```

gksudo gedit /boot/grub/menu.lst
```

*(this starts gedit in graphical mode with admin rights - menu.lst is read-only otherwise)*

enter your password when asked.

**SAVE the file as a backup - say "menu.bak"**

Scroll down and find the lines near the bottom of the file that look something like this:

> title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Move all those lines to BEFORE the line in the file that says: 

> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


Save the file as menu.lst (overwrite the original)

Just check that near the top of the file is a line that says:

> default		0

(That's the one that determines which option is the default - you having just ensured that Windows will be "0" option by putting it first.)

Close gedit and your machine should boot to windows unless you select Ubuntu.

Of course, you will have to redo all this when you decide to use Ubuntu as your main OS.;)

---

### Post by stefaan.dutry on 2007-06-04
Thank you. 

[LIST]
[*]I've moved the windows starting option to before the automagic part. 
[*]I've put the default value back to 0.
[/LIST]

Now I don't have to worry for future updates and i can keep more than 1 kernel version on my coputer

---

### Post by mcduck on 2007-06-05
> **stefaan.dutry said:**
> Thank you. 

[LIST]
[*]I've moved the windows starting option to before the automagic part. 
[*]I've put the default value back to 0.
[/LIST]

Now I don't have to worry for future updates and i can keep more than 1 kernel version on my coputer

The other way would have been leaving the windows entry where it is, and then changing this setting in the menu.lst to true:
```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
```

---

### Post by stefaan.dutry on 2007-06-05
> **mcduck said:**
> The other way would have been leaving the windows entry where it is, and then changing this setting in the menu.lst to true:


Although that would have worked, I prefer the way it is now.

Now i only need to move down 1 selection to get into ubuntu's latest kernel, as where otherwise i would have to move a considerable amount of times up to get into it.

So, therefore the solution I used seems better to me. ;)

But thanks anyway.:D

---

