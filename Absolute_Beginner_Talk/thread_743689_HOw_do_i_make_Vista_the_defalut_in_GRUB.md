---
title: "HOw do i make Vista the defalut in GRUB"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Brii on 2008-04-02
not that i want to 

it because that other people who use this computer dont know as much as i do

---

### Post by Mogurijin on 2008-04-02
In the Terminal type:

```
sudo gedit /boot/grub/menu.lst
```

Then there is a line that talks about a default entry. Look around and read the comments. I'm on a Windows system or else I'd look it up and tell you =[.

EDIT: Also, try a forum search, there are plenty of threads on this.

---

### Post by wormser on 2008-04-02
You need to edit /boot/grub/menu.lst and change the default boot number.  First back it up.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

```
gksudo gedit /boot/grub/menu.lst
```

Search for the line "default		0" and change the number to the count it takes to get to XP.  At the bottom of menu.lst you will see you operating systems.  Start at the top and at zero to get the correct number.  Usually XP is the 4 entry, so the number will be 3.

---

### Post by louieb on 2008-04-02
Its a common question your not the only one that wants to make the other OS the default.  Couple of ways to do it. Heres how I do it.   [Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm#xp1st")

---

### Post by jflaker on 2008-04-02
once you are in the file, you have two choices.......MOVING the boot entry of your choice at the bottom of the file to the FIRST position, which is 0 (ZERO) or changing the DEFAULT number to the entry of your choice.

The count is 0 based, so start counting from 0, 1, 2, 3 etc.........

If you change the order of the boot entries at the bottom, Vista will always be the first entry (at the top).  If you change the "default" number, the highlighted entry will not be at the top, but at the position in the loader menu..........so vista may be the 4th entry and highlighted.

AS WITH ANY CHANGES:  MAKE A COPY FIRST just in case you mess it up, you can go back to the original.

---

