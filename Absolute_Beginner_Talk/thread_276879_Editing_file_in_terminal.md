---
title: "Editing file in terminal"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by dberg on 2006-10-13
My visual display failed to open.  All I have is the terminal. I know which file is causing the problem, is there a way to open and edit that file using the terminal?

sudo gedit    will not work.

Thanks

---

### Post by meng on 2006-10-13
Yes, gedit is a GNOME application, so it won't work if you just have a console. I recommend using nano, as it is fairly intuitive for a text-based text editor.
sudo nano (filename)

---

### Post by taurus on 2006-10-13
```
sudo nano <filename>
```
If you need to reconfigure your X, run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Crashmaxx on 2006-10-13
Try sudo nano <filename>, its a text only text editor.

---

### Post by meng on 2006-10-13
And the verdict is unanimous!

---

### Post by aysiu on 2006-10-13
```
sudo nano -B *filename*
```

---

### Post by hajk on 2006-10-13
> **meng said:**
> Yes, gedit is a GNOME application, so it won't work if you just have a console. I recommend using nano, as it is fairly intuitive for a text-based text editor.
sudo nano (filename)

I would recommend using the -w option when using nano, 
```
sudo nano -w <filename>
```
which prevents long lines from being split accidentally. This is a useful guard when editing various conf-files (like /boot/grub/menu.lst)

---

### Post by meng on 2006-10-13
aysiu, thanks for pointing out the -B switch (it creates a backup file!) I didn't know about that one before.

---

### Post by dberg on 2006-10-13
Thanks for the quick replies, nano worked great. All fixed.

---

### Post by aysiu on 2006-10-13
> **meng said:**
> aysiu, thanks for pointing out the -B switch (it creates a backup file!) I didn't know about that one before.
I got that from somebody else (forget which thread), and I've kept to it ever since.

---

### Post by taurus on 2006-10-13
> **meng said:**
> And the verdict is unanimous!
Personally, I use vi (or vim) but that's me...

---

### Post by meng on 2006-10-13
> **taurus said:**
> Personally, I use vi (or vim) but that's me...
I prefer vi also, but it's clear (to me anyway) from reading the OP that nano is closer to the bill for this task.

---

### Post by forger on 2006-10-13
um why everyone suggested sudo?!
you don't need to be a superuser (to sudo) if it's in your home or something, which the user never stated where the file is, but I suppose you could give the alternative solution without sudo

---

### Post by meng on 2006-10-13
Good question, but I guess everyone assumed from the problem that it had to do with the /etc/X11/xorg.conf file, which requires superuser privileges for editing. Many other config files do also. It is unlikely that a file in the user's home directory would stop the X server from starting ...

---

### Post by aysiu on 2006-10-13
> **forger said:**
> um why everyone suggested sudo?!
you don't need to be a superuser (to sudo) if it's in your home or something, which the user never stated where the file is, but I suppose you could give the alternative solution without sudo
Because the OP wrote this: [quote=dberg]All I have is the terminal. I know which file is causing the problem, is there a way to open and edit that file using the terminal?

sudo gedit will not work.[/quote] Any file causing X to crash is usually a root-owned file.

The OP alsp tried *sudo gedit*, which would indicate a need for *sudo*.

---

### Post by forger on 2006-10-13
hm, ok I definitely didn't know that :)

---

