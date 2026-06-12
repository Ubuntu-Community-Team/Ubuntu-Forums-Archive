---
title: "Triple Boot- Windows gone!"
date: 2008-03-22
forum: Apple Intel Users
---

### Post by ThatGuyThere on 2008-03-22
Sorry for the vague title;
I was installing a triple-boot on my system, following all of the instructions. Now, my windows XP doesn't appear in rEFIt. However, when I go to Ubuntu, it gives me a menu that looks something like this. I can boot up Ubuntu, but I have questions about windows... 

```
___________________________________
Ubuntu 7.10 kernel 2.6.22-14-generic
Ubuntu 7.10 kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10 memtest86+
Other operating systems:
Microsoft windows XP professional
___________________________________
Use the [UP] and [DOWN] keys to select which entry is highlighted. 
Press enter to boot the selected OS, 'e' to edit the
 commands before booting, or 'c' for a command line. 
```

When I go to Microsoft Windows XP Professional and hit e, I get
```
___________________________________
root (hd0,3)
savedefault
chainloader +1
___________________________________
Use the [UP] and [DOWN] keys to select which entry is highlighted. 
Press 'b' to boot, 'e' to edit the selected command in the
 boot sequence, 'c' for a command line, 'o' to open a new line after
 ('O' for before) the selected line, 'd' to remove the 
selected line, or escape to go back to the main menu. 

```

Can I get windows to work from there? I don't care if I can't get there thru rEFIt, as long as I can boot it.

---

### Post by dacorr on 2008-03-22
windows is on the third partition according to the code, have you tried chainloader +2?

---

### Post by ThatGuyThere on 2008-03-22
Would I get to chainloader +2 by going to Microsoft Windows XP Professional, Hitting E, Selecting Chainloader, hitting e, and modifying it somehow? This is the first time i've seen this prompt, and I'm actually intimidated by this screen >.<

---

### Post by ThatGuyThere on 2008-03-22
OK, so I tried going to the
__________________________________
 root (hd0,3)
savedefault
chainloader +1
___________________________________
Use the [UP] and [DOWN] keys to select which entry is highlighted. 
Press 'b' to boot, 'e' to edit the selected command in the
 boot sequence, 'c' for a command line, 'o' to open a new line after
 ('O' for before) the selected line, 'd' to remove the 
selected line, or escape to go back to the main menu.

Menu, and hit e on chainloader +1. I changed the 1 to 2, and hit enter. I hit B, but all it does is shows... 

GRUB loading up (stage2)..

and goes back to that menu. Could you post specific instructions? I'm a pretty big nub at this.

---

### Post by cyberdork33 on 2008-03-23
It sounds like you installed grub to the windows partition somehow. I think you need to boot from the windows install cd into recovery mode, then use the FIXBOOT command to repair the windows partition. You may have to reinstall grub to the correct place after you do that as well, but try the windows fix first and see what happens.

---

