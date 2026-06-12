---
title: "ERROR Message : Help Please"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Oro_07 on 2008-01-26
I downloaded an XMMS skin and then went into usr/share/xmms/skin to unload it in the skin folder, but an error message popped up saying "You do not have permissions to write to this folder"

How do i get around this?

---

### Post by PmDematagoda on 2008-01-26
You should open the file manager in root mode and then do it.

Open the file manager in root mode using:-

Ubuntu:-
```
sudo nautilus
```

Kubuntu:-
```
sudo konqueror
```

Xubuntu:-
```

sudo thunar
```
[B]
Be warned[/B], using the file manager in root mode means that you can do anything to almost any file in your entire Linux system, which may lead to the entire system becoming unstable or cause it to stop functioning altogether if you make a mistake, so use it carefully.

---

### Post by Oro_07 on 2008-01-26
Thanks

Whats the code for extracting a file into the folder

---

### Post by tojge on 2008-01-26
What format is the file you've downloaded in? I mean, .tar, .tar.gz, .tar.bz2, .zip ...?

---

### Post by Oro_07 on 2008-01-26
tar.bz2

---

### Post by tojge on 2008-01-26
Ok, first, you might wanna move the file into the directory you want it in, so cd to the directory where it resides now, and do
```
sudo mv *your_skin_file_name*.tar.bz2 /usr/share/xmms/skin
```
Then cd to desired directory
```
cd usr/share/xmms/skin
```
Then unpack it
```
sudo tar -xvjf *your_skin_file_name*.tar.bz2
```

OR,

just do, from the directory your file is in,
```
sudo tar -xvjf *your_skin_file_name*.tar.bz2 -C /usr/share/xmms/skin
```

Finally, you might wanna remove the archive (not that it hurts leaving it there, but it just eats the space up for no reason)
```
sudo rm *your_skin_file_name*.tar.bz2
```
That should do it...

---

