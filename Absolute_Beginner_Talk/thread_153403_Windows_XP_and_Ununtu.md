---
title: "Windows XP and Ununtu"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Recusant on 2006-03-31
I have XP installed on my laptop and I recently installed Ubuntu.  When it asked me if I wanted to delete all the Windows stuff of my HD, I said no, and it says that I have a few gigs taken up by Windows on my HD so I KNOW it's still there.  The only problem is that Ubuntu loads up automatically when I start my laptop instead of giving me a choice about which OS I wanna' load.  How exactly do I fix this?  Layman-speak, please.  Thanks in advance.

EDIT:  Oops, looks like I spelled Ubuntu wrong...

---

### Post by trent dillman on 2006-03-31
Applications > accessories > terminal

```
sudo gedit /boot/grub/menu.lst
```

add a # in front of hiddenmenu, change timeout to 10, and make sure windows is at the end of the file like this:

```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Mustard on 2006-03-31
Might I suggest that before you start mucking around with your original menu.lst, that you make a backup first.

To make a backup..
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

#This is basically saying, as a superuser (sudo)
#copy the file menu.lst in the /boot/grub directory
#to a file called menu.lst_backup in the /boot/grub directory
```

This is at least going to give you a working backup file should things get really mucked up.

---

