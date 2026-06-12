---
title: "NewBie : How Can I Modify GRUB?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by 7mm on 2007-01-25
Hi There, I'm Basic'ly Windows User Using KUBUNTU 6.10 With WindowsXP As MultiBoot. Grub Is Installed By Default & Need To change Given Time (10 Sec.) & SplashScreen Too. Please Help!

---

### Post by deadgobby on 2007-01-25
open up the terminal and

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

    * Find this line 

...
timeout     3
...

    * Replace with the following line 

timeout     X_seconds

    * Save the edited file 

I can't think on top of my head to speed up Ubie boot time. A mere 45 to 55 secound is really not that long.

Gobby

---

### Post by 7mm on 2007-01-25
Thank You "deadgobby" For Very Useful Info. Will Work On That. Can You Help Me Changing / Modifying GRUB SplashScreen?

---

### Post by Lowtech on 2007-01-25
I added a link below to the guide I used to add a GRUB splash screen.  I just picked one that another user had already made just to see if I could do it.  

Good luck.

[http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash](http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash)

---

### Post by Tomosaur on 2007-01-25
Check the link in my sig :)

---

### Post by 7mm on 2007-01-25
> **Lowtech said:**
> I added a link below to the guide I used to add a GRUB splash screen.  I just picked one that another user had already made just to see if I could do it.  

Good luck.

[http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash](http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash)

Thank You For The Link, Mate. Such Detailed Information.:guitar:

---

