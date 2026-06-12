---
title: "Editing System Files"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by menawollas on 2005-09-07
I am just playing around with my grub options, and want to edit menu.lst. 

However, if i use the file browser to get there, I open it under my own permussions in the text editor, so it is read only.

I know I could open a root console, cd /boot/grub and open it in vi - but mt vi skills are very very rusty...

How do I open such a file in the text editor using sudo ???

Thanks

---

### Post by Gunder on 2005-09-07
You can use gedit
 
```

sudo gedit nameofthefile

```

---

### Post by Wolki on 2005-09-07
[QUOTE=Gunder]You can use gedit
 
```

sudo gedit nameofthefile

```[/QUOTE]

gedit is a fine solution, for command line stuff you don't have to use vi though (few people like to do that). nano is a command line editor that's really easy to use, and for small changes it's faster than gedit. Use what you like best :)

---

### Post by menawollas on 2005-09-07
thanx

---

