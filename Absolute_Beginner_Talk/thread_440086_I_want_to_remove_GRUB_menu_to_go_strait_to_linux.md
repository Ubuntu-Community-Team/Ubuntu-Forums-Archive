---
title: "I want to remove GRUB menu to go strait to linux"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by lebe0024 on 2007-05-11
I have two harddrives, one windows one ubuntu.  When I intalled ubuntu, it detected my windows harddrive and now I have a grub boot menu.  I want it to go strait to ubuntu, ie no menu.  How do I do this?

---

### Post by Bachstelze on 2007-05-11
You cannot get rid of GRUB entirely but you can set the timeout to e.g. 1 second to achieve etty much the same thing.

---

### Post by Kobalt on 2007-05-11
Hmm I'm not sure that's possible and not a good idea either : how would you select the recovery mode or the Memory test for instance ? 
You can reduce the time it lets you select on which OS you want to boot though : open the menu.lst file and adjust the timeout value (in secconds) 
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by lebe0024 on 2007-05-11
Okay, how about if I just remove the windows menu item?  Do I just remove the entry from the menu.lst?

---

### Post by Bachstelze on 2007-05-11
Yes

---

### Post by Najand on 2007-05-11
As others have already mentioned, try to edit /boot/grub/menu.lst by:
```

gksu gedit /boot/grub/menu.lst

```
And change timeout and hidden parts like the following:

> [COLOR="DimGray"]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).[/COLOR]
[COLOR="Blue"]timeout         1[/COLOR]

[COLOR="DimGray"]## hiddenmenu
# Hides the menu by default (press ESC to see the menu)[/COLOR]
[COLOR="Blue"]hiddenmenu[/COLOR]
It will hide your Windows Partiotiona and it is as fast as you don't even find enough time to select it.

---

### Post by Medieval_Creations on 2007-05-11
> **lebe0024 said:**
> Okay, how about if I just remove the windows menu item?  Do I just remove the entry from the menu.lst?

I wouldn't suggest removing it completely from the menu.lst, but instead just comment it out.
Just put a # in front of each line in the Winbloze section.  Id show you an examples of exactly what it looks like, but I have a winbloze free household.

That way you can always uncomment it and reboot into windows if needed.

Just out of curiosity, if you don't plan on ever booting into Winbloze again, why not just do a clean install with Linux only?

---

### Post by lebe0024 on 2007-05-11
It is a clean install on one hard-drive.  I got a new harddrive and installed only ubuntu on it.  I kept my windows drive in there for now until I get completely migrated over, then I'll just take out that drive.  Right now I use my motherboard bios's boot selector to select which drive to boot from (and thus which OS).

---

### Post by drowner on 2007-05-11
I personally dont think there is any need to get rid of grub.

Grub will take out the same amount of space, whether it has the windows section or not

If you dont like waiting for it, set the timeout to 0.

If you dont want windows at all, then just hose the windows partition, then you can edit your grub ;)

While your windows partition is there, you may as well have SOME way to access it, should you ever want to

---

