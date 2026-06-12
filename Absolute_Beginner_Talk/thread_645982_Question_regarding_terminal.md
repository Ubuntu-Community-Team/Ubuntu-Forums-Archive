---
title: "Question regarding terminal"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by sapu on 2007-12-20
I want to use *cp* in the terminal.
I ran into a problem with my computer, and I want to copy a file into /usr/bin/ to fix it. (dpkg failure)

I grabbed dpkg off the LiveCD, put it on a flash drive, and then restarted the computer and placed it on my desktop (Not LiveCD) from the flash drive. I can't drag-and-drop being it says I do not have permission. So the next best thing I could think of was to *sudo cp*

I have no idea how I would do this. I don't know how to use *cd*

---

### Post by jken146 on 2007-12-20
There is a **man**ual page for every command.  Type ```
man cp
``` for example.

cp commands are of the form ```
cp <path to file> <path to destination>
```

If you want to drag and drop, hit Alt+F2 and type **gksu nautilus** -- this will let you be root with the file browser.

---

### Post by Existentialist on 2007-12-20
The files in /usr/bin are owned by root so you dont have permission to copy the file as a user.  You are correct that you would use cp.  To copy a file from the desktop you would run:

>cp /home/user/Desktop/filename  /usr/bin/

---

### Post by SOULRiDER on 2007-12-20
To copy into /usr/bin you will have to use sudo.
What is it that youre trying to do though, maybe theres an alternative, somethign safer than modifying files in /usr/

---

### Post by sapu on 2007-12-20
Will either of these methods overwrite the old dpkg?

> **SOULRiDER said:**
> To copy into /usr/bin you will have to use sudo.
What is it that youre trying to do though, maybe theres an alternative, somethign safer than modifying files in /usr/
If I damage the system I have no problem with reinstalling.
But only if I damage the system.

---

