---
title: "ln -s SNAFU..."
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by eilu on 2007-05-24
Well, this is a bit confusing, but here goes:
Early on I wanted my root windows to look like my normal windows, so I put in:
```
sudo ln -s /home/eilu/.themes /root/.themes
sudo ln -s /home/eilu/.icons /root/.icons
sudo ln -s /home/eilu/.fonts /root/.fonts
```

Then just now I decided I didn't like it, so I typed:
```
sudo unlink /root/.themes
sudo unlink /root/.icons
```

Which strangely made my root windows have default theme (human) and my custom theme border which just looks weird.

So now I want to restore my original symlinks (so my root windows follow my theme) but when I retype the commands it returns:
```
~$ sudo ln -s /home/eilu/.themes /root/.themes
ln: creating symbolic link `/root/.themes/.themes' to `/home/eilu/.themes': File exists
~$ sudo ln -s /home/eilu/.icons /root/.icons
ln: creating symbolic link `/root/.icons/.icons' to `/home/eilu/.icons': File exists
~$ sudo ln -s /home/eilu/.fonts /root/.fonts
ln: creating symbolic link `/root/.fonts/.fonts' to `/home/eilu/.fonts': File exists
```
BUT my root windows (i.e., Synaptic) still doesn't follow my default theme. What have I done?? What am I doing wrong? How do I resolve this?

---

### Post by psusi on 2007-05-24
What does sudo ls -al /root/.themes say?  It looks like /root/.themes is a directory instead of a file.

---

### Post by eilu on 2007-05-24
```
total 8
drwxr-xr-x  2 root root 4096 2007-05-25 07:27 .
drwxr-xr-x 20 root root 4096 2007-05-25 08:25 ..
lrwxrwxrwx  1 root root   18 2007-05-25 07:27 .themes -> /home/eilu/.themes
```

Yes, it is a directory. I think the ln -s tells it that root's themes are your themes (or something like that)

---

### Post by psusi on 2007-05-25
Yea, I think you got the parameters backwards.

---

### Post by kevdog on 2007-05-25
The original ln -s command should have been:

```

sudo ln -s  /root/.themes /home/eilu/.themes
sudo ln -s  /root/.icons /home/eilu/.icons
sudo ln -s  /root/.fonts /home/eilu/.fonts

```

---

### Post by Bachstelze on 2007-05-25
> **kevdog said:**
> The original ln -s command should have been:

```

sudo ln -s  /root/.themes /home/eilu/.themes
sudo ln -s  /root/.icons /home/eilu/.icons
sudo ln -s  /root/.fonts /home/eilu/.fonts

```

Wrong. ln basically works like cp, source file first.

---

### Post by l3f3vr3 on 2007-05-25
ln command structre is the same as cp 
```

ln -s source destination

```


EDIT:I guess I was too slow at typing!!

---

