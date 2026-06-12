---
title: "How to list directory files in terminal?"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by WynD on 2006-01-16
Hi

I've just installed Linux for the first time and I used that automatix program to download some programs. After it finish installing i restarted my computer and then the x server failed to start.. automatix warned me if this happens I'll have to use "sudo cp /etc/x11/xorg.conf_backu . . . . something something" but I forgot the backup file so now I need to find that file.

Thanks for any help.

---

### Post by Inarius03 on 2006-01-16
ls or ls -l

---

### Post by WynD on 2006-01-16
and how do i list the files in a specific directory?

like in /etc/x11/

srry i'm still a newbie at these stuff.

---

### Post by Inarius03 on 2006-01-16
example of /etc/x11/:

change to the directory by "cd /etc/x11/"

then "ls" or "ls -l" to list the files and stuff

There could be a way to change directory and list the contents at the same time, but I don't know.

---

### Post by WynD on 2006-01-16
TY
I got my computer back :)

---

### Post by Inarius03 on 2006-01-16
No problem. Glad I could help!

---

### Post by Iowan on 2006-01-16
[QUOTE=Inarius03]

There could be a way to change directory and list the contents at the same time, but I don't know.[/QUOTE]
example:
cd /etc/X11;ls

---

### Post by nusigmaforce on 2006-01-16
Thanks for that last bit.

---

### Post by GreyFox503 on 2006-01-16
Couldn't resist, simply:

```
ls /etc/X11/
``` 
If you want to know more about a certain command like *ls*, then you can try:

```
ls --help
``` 
or

```
man ls
```

---

