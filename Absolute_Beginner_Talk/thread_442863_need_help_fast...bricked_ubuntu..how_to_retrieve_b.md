---
title: "need help fast...bricked ubuntu..how to retrieve backup"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by locustfist on 2007-05-13
i am trying to get dual monitors going and i dropped some stuff into 'xorg.conf' and it bricked....how do i retrieve  and replace the backup i made 'xorg.confbackup'  ?

---

### Post by [S|G] on 2007-05-13
Did you save the backup in the same directory as your old xorg.conf? If you did, just do this:
```
sudo cp /etc/X11/xorg.confbackup /etc/X11/xorg.conf
```
That should do the trick. If for some reason you cannot restore your backup, you can reset your xorg:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by locustfist on 2007-05-13
do i type that into the command prompt?

---

### Post by [S|G] on 2007-05-13
Yes :)

---

### Post by locustfist on 2007-05-13
the command line says 'grub>' 

is that what it should say?
i punched both of those lines in, neither worked

---

### Post by [S|G] on 2007-05-13
You have to boot into ubuntu first. You'll probably get a prompt asking for your login and password, and you should enter that normally. Then you'll get to the terminal.

You should type that once you are logged in, and not at grub's prompt.

---

### Post by tgalati4 on 2007-05-13
In grub:

>root (hd0,0)
>kernel /boot/kernel(tab)
>initrd /boot/initrd(tab)
>boot

---

### Post by locustfist on 2007-05-13
can't boot into ubuntu...the xorg error has to do with the display and it can't boot into the GUI

---

### Post by bobplano on 2007-05-13
once you get to the command line and it says username or something type that in then your password and then you have a command line where you can reconfigure your xorg or restore a backup. if it isn't getting past grub thats something else

---

### Post by [S|G] on 2007-05-13
You don't need to boot into the GUI. Just start Ubuntu normally and you'll end in a command line terminal asking for your login (not the GUI). Put your username and password there. Then you'll be logged in the terminal. Then try the first command. If there is no error, try to start the GUI by typing "startx". If there is an error, try the second command and then try "startx"

---

### Post by Tenicus on 2007-05-13
When you get the error after trying to boot into ubuntu simply hit CTRL+ALT+F1

---

### Post by locustfist on 2007-05-13
i think that did the trick

thanks

---

