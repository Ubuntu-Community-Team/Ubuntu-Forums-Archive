---
title: "How to delete from flash card?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-05-15
I'm running Feisty and have a flash card, in a card reader, in a USB port.

What I would like to do is to remove photos from the flash card but I have been unable to find an option to do this.

Under 'Permissions' I am shown as the owner, with permission to read, write and execute but nothing I have tried so far will let me 'Move to trash'.

If someone can give me some pointers here I would really appreciate it.

---

### Post by jhenager on 2007-05-15
Have you tried doing this from terminal?
e.g. 
jeff@jeff-desktop:/media/flash$  sudo rm *.jpg

---

### Post by rich.bradshaw on 2007-05-15
How's it formatted, should be no different to any other drive. Just drag it to trash.

---

### Post by L Campbell on 2007-05-15
> **rich.bradshaw said:**
> How's it formatted, should be no different to any other drive. Just drag it to trash.

Thanks for your interest but when I try this I get, "Cannot move items to trash, do you want to delete them immediately?"

I clicked 'delete' and got, "Unable to move to trash:  Read only file system."

---

### Post by jhenager on 2007-05-15
It might help if you post the results from:

fdisk -l

(lower case L)

---

### Post by L Campbell on 2007-05-15
> **jhenager said:**
> It might help if you post the results from:

fdisk -l

(lower case L)

OK, thanks.

qwer@qwer-desktop:~$ fdisk -l

Disk /dev/sda: 998 MB, 998768640 bytes
20 heads, 51 sectors/track, 1912 cylinders
Units = cylinders of 1020 * 512 = 522240 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1913      975295+   6  FAT16
qwer@qwer-desktop:~$

---

