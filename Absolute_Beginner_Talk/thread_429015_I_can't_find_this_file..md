---
title: "I can't find this file."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-30
I'm trying to locate a file through Nautilus. I am fixing a bug that is found in the driver for the ATI Radeon 9200/9250 video card.

The statement says:
[I][B]This downloads three files and unpacks the sources into the directory xserver-xorg-driver-ati-version

[/B][/I]I've looked and looked and can't find "xserver". If I can find it, I can find the rest. I would appreciate it if someone can help.
kh

---

### Post by Seisen on 2007-04-30
Check in this directory
```
/etc/X11
```

---

### Post by kittyhawk63 on 2007-04-30
Not there.
I've tried finding it through the search line in Nautilus. Does it work like the search in Windows Explorer? Will it find both folders and files?

I typed in "xserver" (no quotes) and it Nautilus never found it. It was supposed to have been made, however, automatically.

---

### Post by wormser on 2007-04-30
Here are some other ways to find files.

```
find / -name 'mypage.htm'
```

The / can be any directory path

Another way:
```
locate filename
```

You need to update the DB before using this command: 
**sudo updatedb**

And Another is the **whereis** command.

---

### Post by NilsE on 2007-04-30
Try the search under Places and include "include hidden files" as an option.

Nautilus search is not as effective.

---

### Post by kittyhawk63 on 2007-04-30
Thanks guys.
I will sure try out these suggestions.
kh

---

### Post by TwistesdTexan on 2007-04-30
Don't forget that the directory is case sensitive and that means a loose translation of that directory is _X[U]_[/U]Eleven

---

### Post by zvacet on 2007-05-01
```
whereis file_name
```

---

