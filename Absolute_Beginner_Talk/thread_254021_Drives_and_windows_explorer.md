---
title: "Drives and windows explorer"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-09-09
What is the equivalent of "C" drive as in MS Windows please?  
Also is there an equivalent of Windows Explorer?

---

### Post by dbd on 2006-09-09
I suppose the equivalent of a "C" drive is your root partition, the partition mounted at / 

There are many file managers that do the same job as windows explorer, for example: Nautilus for Ubuntu, Konqueror for Kubuntu, Thunar for Xubuntu. Probably best to use the one default for your particular version, but you are free to use any other if you prefer it.

Not sure if this is relevant to what you were asking, but there is more info on Linux filesystems here:
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

---

### Post by jorn on 2006-09-09
Windows will automatically call the drive where it installs itself as C:
In Linux you install on a disk of your choise.
The first disk is called hda the second hdb or sda (sata).
The different partions are are called 1,2 and so on, example : dha1
There are different kinds of filebrowsers, by default ubuntu comes with "Nautilus".

---

### Post by a.v.l on 2006-09-09
Excellent, thanks.  One more question, where is "My Documents" please](*,)

---

### Post by jorn on 2006-09-09
In you home folder. Is on the top at the filebrowser "nautilus".

---

### Post by a.v.l on 2006-09-09
> **jorn said:**
> In you home folder. Is on the top at the filebrowser "nautilus".

I'm trying out KDE and can't find my documents in the home folder, any ideas?

---

### Post by jorn on 2006-09-09
Open konquerer, click the first blue button, it looks like a house.

---

### Post by paddy1978 on 2006-09-09
Sounds like you might be getting confused by the terminology. You won't find "My documents" in your home folder because a user's home folder in linux is sort of the **equivalent** to "my documents" in windows.

So, if your username was fred, in linux you'd probably store your personal files in: /home/fred/ - in windows it would be something like C:\Docs & settings\fred\My documents\

You can always use the ~ symbol as a shortcut to your home directory - so if in Konqueror, which is the KDE file manager as mentioned above, you type ~ in the location bar it will take you to where you should store person files (which will be /home/<your username>).

Hope this makes sense!

---

### Post by dbd on 2006-09-09
Your home folder IS the equivalent of My Documents. My Documents is not something in your home folder.

---

### Post by a.v.l on 2006-09-09
Thanks again, things are begining to make a little more sense now.

---

