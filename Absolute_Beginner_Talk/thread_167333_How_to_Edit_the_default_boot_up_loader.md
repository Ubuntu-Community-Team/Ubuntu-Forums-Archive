---
title: "How to Edit the default boot up loader???"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by minhaz4u on 2006-04-28
Im bored of the old Ubuntu boot up loader...Is there any way to edit and make a custom loader??? 
Any help would really b appreciated ;)

---

### Post by rado_london on 2006-04-28
Well the config file for the GRUB is  /boot/grub/menu.lst.
To edit it enter the following in the terminal
```
sudo gedit /boot/grub/menu.lst
```

There are some nice options but GRUB isnt very customizable. if you do a search on the forum you can even find how to create custom splash screen.

Good luck

---

