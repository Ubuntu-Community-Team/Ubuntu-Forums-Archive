---
title: "Disk format utility"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by kcampbell26 on 2006-03-06
My disk format utility has suddenly decided to quit.  The error message says "cannot initialize any device".  Oddly enough tho, I can suddenly read and write to a floppy disk as long as it has been previously formatted (which I can no longer do) I have never been able to mount a floppy with ubuntu, so this was quite a surprise.  Any suggestions on how to get the format utility back online?  I have noticed that I no longer see the Nautilus icon on startup.

---

### Post by Pragmatist on 2006-03-08
try ```
gfloppy
```

---

### Post by kcampbell26 on 2006-03-09
Already have....it renders the same error message

---

### Post by Pragmatist on 2006-03-09
What is the output of: ```
ls -l /dev/fd0 /media
```
What is the output of: ```
cat /etc/fstab
```
What message do you get if you type: ```
sudo mount /dev/fd0 /media/floppy
```

---

### Post by kcampbell26 on 2006-03-09
first response is  "not a directory"
Second is too lenghty, but mainly says user/noauto
third "cant find"

---

### Post by AndrewCaul on 2006-03-09
[QUOTE=kcampbell26]Second is too lenghty, but mainly says user/noauto[/QUOTE]
Can you give us the entire output?

---

### Post by kcampbell26 on 2006-03-09
Like I said, too lengthy......does it help to know that the nautilus icon does not show up on the panel when logging in?  It used to be there, and when this happened, I noticed it was replaced by the applications menue editor icon.

---

### Post by Pragmatist on 2006-03-09
> Like I said, too lengthy  If you want help, you need to take the small amount of trouble to give us the information we're requesting.

Also, if you have no /media directory you have a huge problem.  I doubt your missing it.  Try this again and actually cut/paste the info from your terminal:
```
sudo ls -l /
```
```
sudo ls -l /media
```
```
sudo ls -l /dev/fd*
```
```
sudo cat /etc/fstab
```
```
sudo mount
```
```
sudo lshal |grep floppy
```

---

### Post by kcampbell26 on 2006-03-10
Here are the results:

---

### Post by kcampbell26 on 2006-03-10
I see that didn't work.......

---

### Post by Pragmatist on 2006-03-10
Can you open the file with ```
gedit output
```  If so, you can cut and paste from there into your post here.

---

