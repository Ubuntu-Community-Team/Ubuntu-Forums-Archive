---
title: "Archive type not supported error for rar files"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-08-11
When I try to open rar files made by winrar, I get a error message that says "Archive type not supported". I downloaded RAR which is same makers of winrar, do you guys think it will work fine with rar files made by winrar, if so how do you install it. The file name is rarlinux-3.4.1.tar.gz

---

### Post by AndyAWS on 2005-08-11
The proper way would be to search for **unrar** in synaptic and install the official ubuntu package.

Or from a terminal:

```
sudo apt-get install unrar
```

---

### Post by poofyhairguy on 2005-08-12
Actually you need unrar, not rar.

---

### Post by AndyAWS on 2005-08-12
[QUOTE=poofyhairguy]Actually you need unrar, not rar.[/QUOTE]

Right...fixed. ](*,)

---

### Post by Tristan9669 on 2005-08-12
thanks

---

### Post by Linux_Noobie on 2005-08-22
[QUOTE=Tristan9669]thanks[/QUOTE]
 Wait....I dont get it (i need to unrar something..) how do i do it?

---

### Post by Tristan9669 on 2005-08-22
paste this in the terminal
```
sudo apt-get install unrar
```

---

### Post by atilasendil on 2005-09-01
[QUOTE=Linux_Noobie]Wait....I dont get it (i need to unrar something..) how do i do it?[/QUOTE]

even after installing unrar I could not open the file with "File Roller" so I tried :

unrar x file_name.rar

and I have all the contents in the folder now :-)

(I keep writing real noob things in the forums hoping I might help someone as noob as me someday)

---

### Post by Wolki on 2005-09-01
This is a bug in Gnome 2.10. File-roller will only be able to open rar files if you have the rar package (shareware) installed, unrar (freeware but not opensource) is not enough. It is already fixed in Breezy.

So, on Hoary, do sudo apt-get install rar (or install rar with synaptic). I think you need the multiverse repository enabled, see Wiki/Ubuntuguide. Don't forget to uninstall it after 30 days/pay the license fee :)

---

### Post by jc87 on 2005-09-12
By the way i installed unrar , but always i do unrar -x filename.rar it starts to unrar but fails .

What may be the problem in this case?

---

### Post by Wolki on 2005-09-12
[QUOTE=jc87]By the way i installed unrar , but always i do unrar -x filename.rar it starts to unrar but fails .

What may be the problem in this case?[/QUOTE]

Whay error do you get?

Check also that you have the correct unrar installed, the Free version sadly can't extract everything; get rar-nonfree for newer rars.

Is the archive maybe corrupt?

---

### Post by jc87 on 2005-09-13
Extracting from /home/jc87/Desktop/filename.rar

Extracting filename.srt                                        Failed
1 Failed

The original name was substituted off course by filename in this post :wink: i already tryed with diferent stuff nothing worked so far.

Byt the way the version i installed unrar with sudo apt-get install unrar .

---

### Post by arazaxirelcinellersadolur on 2005-11-30
[QUOTE=atilasendil]even after installing unrar I could not open the file with "File Roller" so I tried :

unrar x file_name.rar

and I have all the contents in the folder now :-)

(I keep writing real noob things in the forums hoping I might help someone as noob as me someday)[/QUOTE]

so, i tried from synaptic and 

1. first installed the unrar-free, its description is:
Unarchiver for .rar files
Unrar can extract files from .rar archives. Can't handle archives in the
RAR 3.0 format, only the non-free "unrar" package can do that.

and it do not make me happy:
elcin@memmedzadee:~/Desktop/m&#252;v&#601;qq&#601;ti/y&#252;kl&#601;$ unrar Fatma.rar
bash: unrar: command not found
elcin@memmedzadee:~/Desktop/m&#252;v&#601;qq&#601;ti/y&#252;kl&#601;$ unrar x Fatma.rar
bash: unrar: command not found

2. i installed the second at the synaptic it was : unrar-nonfree and its description is:
Unarchiver for .rar files (non-free version)
Unrar can extract files from .rar archives. If you want to create .rar
archives, install package rar.

and after that i typed at terminal:
elcin@memmedzadee:~/Desktop/m&#252;v&#601;qq&#601;ti/y&#252;kl&#601;$ unrar x Fatma.rar

UNRAR 3.40 freeware      Copyright (c) 1993-2004 Alexander Roshal


Extracting from Fatma.rar

Creating    Fatma                                                     OK
Extracting  Fatma/Vsfx.ttf                                            OK
Extracting  Fatma/Fatma Bold BT.ttf                                   OK
Extracting  Fatma/Fatma Bold Italic BT.ttf                            OK
Extracting  Fatma/Fatma Book BT.ttf                                   OK
Extracting  Fatma/Fatma Book Italic BT.ttf                            OK
All OK
elcin@memmedzadee:~/Desktop/m&#252;v&#601;qq&#601;ti/y&#252;kl&#601;$

and it made me happy.

and i wish you it makes u happy too :razz: 
best regards

Edit: 
i just tried from Archive Manager from Menu to find that rar file named above and yes it made me happy too!
i love my ubuntu 
respectfully,
[email]ubuntum@gmail.com[/email]
ps. "ubuntum" means "my ubuntu" in azerbaijanian :)

---

