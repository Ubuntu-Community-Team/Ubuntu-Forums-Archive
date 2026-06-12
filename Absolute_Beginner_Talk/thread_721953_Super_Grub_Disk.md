---
title: "Super Grub Disk"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Tachions on 2008-03-11
hey guys, I used super grub disk about 2 weeks ago to access my Ubuntu machine, when i was having a problem of booting into Ubuntu after installing Windows Xp onto my machine after installing Ubuntu 1st! (didnt want windows but certain apps i needed only run on M$)

The grub disk worked great and got me back into my linux partition, but now I cant get into my windows partition, that wouldnt be such a big deal if I didnt need it for certain things, so any ideas, is it my boot manager? or something else? let me know please!!! you think super grub disk can resolve this issue 2?!? let me know


Tachions

---

### Post by glennric on 2008-03-11
Is there an option on your grub menu when you boot to boot to windows?  If not you will need to edit the file /boot/grub/menu.list and add
```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
You will have to change (hd0,0) to point to the partition that windows is installed on.

---

### Post by Tachions on 2008-03-19
where do i input this code?!? 

in the terminal or when i run the grub disk again?!? thanks for your help

---

### Post by ramjet_1953 on 2008-03-19
Like Glennric said, you need to edit the file :

[COLOR="Blue"]/boot/grub/menu.list[/COLOR]

And add what he listed to this file.

Note:  You need to do this in [COLOR="Red"]sudo[/COLOR] mode, as you are editing a system file.

Also, I would recommend that you backup the existing file first.

Regards,
Roger :cool:

---

### Post by Shazaam on 2008-03-19
Use this if you want.......
```
gksudo gedit /boot/grub/menu.lst
```
This code will open menu.lst for editing. As stated before, make a backup before editing.

---

### Post by Xiong Chiamiov on 2008-03-19
> **Shazaam said:**
> As stated before, make a backup before editing.

...which you can do by
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

```

---

### Post by Tachions on 2008-03-19
how do i figure out quickly which partition my windows is installed on?!? thanks

---

### Post by Sef on 2008-03-19
Open the terminal and type or copy this code:

```
sudo fdisk -l
``` Small L

---

