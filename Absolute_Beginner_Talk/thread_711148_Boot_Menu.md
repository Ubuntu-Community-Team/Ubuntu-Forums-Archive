---
title: "Boot Menu"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by NautTboy on 2008-02-29
I previously had Vista and XP installed on separate partition.  I'd uninstalled vista with :\boot\bootsect.exe /nt52 ALL /force command and it got rid of the vista boot menu which it is how i wanted.

Now, after installed Ubuntu.  I got a menue that includes
Ubuntu
Vista 
Other operating system.

Instead of selecting Vista and boot to Vista and other to boot into XP, Vista boot up to XP and Other operating system boot up to nothing(error).

I could just use the vista menu to logon to XP, but kinda annoying.  Can I edit it in menu.lst?  Like rename Vista to XP and delete the other OS option?

I guess I could try it when i get home, but nice to know ahead of time.

---

### Post by Duck2006 on 2008-02-29
Yes you can, in the trminal to edit your menu.lst you type

gksudo gedit /boot/grub/menu.lst

and you can change what you want ie

title vista

to

title xp

---

### Post by NautTboy on 2008-02-29
Thanks for the quick reply.

Now, i have to wait for the other thread to be answered.

---

