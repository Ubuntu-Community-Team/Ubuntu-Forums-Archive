---
title: "Help copying files"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-06-17
Ok, I wanted to install some Microsoft games using WINE, but it said that it couldn't find pidgen.dll . 
I found out that I could fix this my copying my mfc42.dll file from Windows to ./wine/drive_C/system32 .  Now, I need some help doing this.  First, using the GUI I copied and pasted the file to my /home/username folder.  Then, in the terminal, I tried this:

```
sudo mv /home/username/mfc42.dll .wine/drive_C/system32/mfc42.dll
```

But it said that "No such file or directory existed".  So, how do I copt the file from /home/username to .wine/drive_C/system32 ?

Thanks.

---

### Post by Clay_Banger on 2007-06-17
> **Yes said:**
> Ok, I wanted to install some Microsoft games using WINE, but it said that it couldn't find pidgen.dll . 
I found out that I could fix this my copying my mfc42.dll file from Windows to ./wine/drive_C/system32 .  Now, I need some help doing this.  First, using the GUI I copied and pasted the file to my /home/username folder.  Then, in the terminal, I tried this:

```
sudo mv /home/username/mfc42.dll .wine/drive_C/system32/mfc42.dll
```

But it said that "No such file or directory existed".  So, how do I copt the file from /home/username to .wine/drive_C/system32 ?

Thanks.
```
sudo mv /home/username/mfc42.dll ~/.wine/drive_C/system32/mfc42.dll
```

---

### Post by steveneddy on 2007-06-17
The ~/ tells it to look in the "Home" folder.

The file name .wine is a hidden file denoted by the . in front of the name of the file.

Open your home folder and hit CTRL+h to show the hidden files.

[[IMG]http://img520.imageshack.us/img520/1544/postiig9bm6.gif[/IMG]](http://imageshack.us)

---

