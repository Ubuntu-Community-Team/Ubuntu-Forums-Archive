---
title: "Installing video card driver"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Hamaliel on 2006-12-01
ok, so i downloaded the driver off of ATI's website (i've got a radeon x1300 pro) and when i try to run the downloaded file (filename ati-driver-installer-8.31.5-x86.x86_64(2).run) i get a message popping up that says: gedit has not been able to detect the character coding.  Please check that you are not trying to open a binary file.  Select a character coding from the menu and try again.

any ideas?

---

### Post by Bachstelze on 2006-12-01
Tu run the package, you need to do

```
sh /pat/fo/file.run
```

---

### Post by Hamaliel on 2006-12-01
i really hate to sound like the biggest noob ever....but how do i do that? ](*,)

---

### Post by Bachstelze on 2006-12-01
In a [terminal](http://psychocats.net/ubuntu/terminal) :)

---

### Post by Hamaliel on 2006-12-01
woohoo! I got it to work!

didn't realize i had to run:

>   /usr/X11R6/bin/aticonfig --initial

now, can you tell me the why part to all of this?

---

### Post by Bachstelze on 2006-12-01
Why what ? I don't have an ATi myself but I assume the program you ran configured the Xserver to use the correct drivers.

---

