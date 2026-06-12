---
title: "older versions in grub?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by mech7 on 2006-07-11
Is there anyway i can remove these ? there are now 3 in there :-k

---

### Post by Average_Joe on 2006-07-11
1) open Terminal
2) type there --> sudo gedit /boot/grub/menu.lst
3) In the text file, scroll down near the bottom and find the 'Titles' section
4) Examine the very first of these listed in this section.  Don't remove that one.
5) edit and or remove the appropriate lines for the other ones you don't want, below that first entry which you should not remove

Editing in this case means removing about three or four lines for each undesired entry.

---

### Post by mech7 on 2006-07-11
ok and wont there be any left overs from files? i thought i read somewhere i need to uninstall the older versions or something ?

---

### Post by halfvolle melk on 2006-07-11
Do you need the disk space? If not, let it be. If your 'default' kernel gets messed up somehow, you'll have an older one to fall back to. Many experienced linux users (which I'm not) have said it to be a life saver at times.

---

### Post by mcduck on 2006-07-12
It doesn't really make sense to just remove the lines from grub and still leave all those old kernel versions on your system (if they are not in grub menu, you can't boot them anyway). Besides, removing the old versions with Synaptic is faster and easier, and removes the grub entries as well :)

---

### Post by richbarna on 2006-07-12
> **Average_Joe said:**
> 1) open Terminal
2) type there --> sudo gedit /boot/grub/menu.lst
3) In the text file, scroll down near the bottom and find the 'Titles' section
4) Examine the very first of these listed in this section.  Don't remove that one.
5) edit and or remove the appropriate lines for the other ones you don't want, below that first entry which you should not remove

Editing in this case means removing about three or four lines for each undesired entry.

>  2) type there --> [COLOR=Red]gk[/COLOR]sudo gedit /boot/grub/menu.lst 

It's a graphical program. It's safer :)
[http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

---

### Post by falcon15500 on 2006-07-12
If you go into synaptic or SmartPM (whichever you use) and elect to remove the old kernel image and the old restricted modules entry - your grub menu.lst will be updated too.

falc

---

