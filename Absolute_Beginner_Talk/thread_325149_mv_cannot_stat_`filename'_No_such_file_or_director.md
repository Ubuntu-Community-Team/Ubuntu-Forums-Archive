---
title: "mv: cannot stat `filename': No such file or directory"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by lilmienboy on 2006-12-25
For some reason i can't move the splash screen file to /boot/grub/images. I downloaded into
my desktop, i can see it but i can't move it into my /boot/grub/images. i triede doing this with different files but i still get the same error.  this is what i get:

cheng@cheng-laptop:~$ sudo mv boot.xpm.gz /boot/grub/images
mv: cannot stat `boot.xpm.gz': No such file or directory

i even tried moving it into other directories and still no luck. is there any other ways. thanks

---

### Post by wounded on 2006-12-25
cd into the Desktop first and then move it or use the command 

sudo mv ~/Desktop/boot.xpm.gz /boot/grub/images

from your home directory. You said it downloaded to your desktop but from the bit you pasted it looks like you are in your home folder.

---

### Post by lilmienboy on 2007-01-01
damn i felt dumb, thanks for the help,

---

