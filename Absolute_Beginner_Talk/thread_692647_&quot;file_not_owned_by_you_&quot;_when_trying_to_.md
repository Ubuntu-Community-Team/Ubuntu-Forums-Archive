---
title: "&quot;file not owned by you &quot; when trying to install"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-10
I'm trying to install firefox in wine & I keep getting this error message:
wine: ~./wine is not owned by you

I've  checked ownership & it is owned by me.

i type     sudo wine /path to .exe

If I leave out sudo I get nothing at all.

Running Ubuntu Studio I think with Gusty
I did the same thing on my other computer with no problems in Feisty.

Any ideas?

---

### Post by spiderbatdad on 2008-02-10
not sure, but if wine is in your home directory and so is the .exe, then by opening the terminal, your pwd should be home. So i would think sudo wine firefox.exe  if that is the filename.```
ls -l |grep wine
``` would show permissions of wine. Sorry never used it.

---

### Post by smothpocket on 2008-02-10
have you checked the permissions of the directory? 

```
ls -l ~./wine
```

it probably should be something like drwxr-xr-x maybe try

```
sudo chmod -R 755 ~/.wine
```

also have you tried installing it with root permissions?

---

### Post by TheBoat on 2008-02-10
Just curious, why are you using wine to install firefox?

---

### Post by garyed on 2008-02-10
To answer the first question - 
I made sure I was the owner of the .wine directory but noticed that the "wine" executable file in /usr/bin was owned by root.
I changed ownership to me but I still got the error. 
The error keeps referring to the  ".wine" directory which is I know is owned by me & thats what I don't understand.
 

I did try to install as root & it did start the install but I abandoned the install because I didn't want to have to be root all the time. 
I left out a little info. I origonally installed wine & firefox installed fine but when I entered the executeable "firefox" nothing happend I think I tried the whole path from the command line too but it still didn't run.

Quest. $# 2
As far as why I'm installing firefrox in wine.
I need it in wine to run a windows animation program that needs a browser. 
If there's a way to integrate the program from wine to use the linux version of firefox please tell me.

---

### Post by myddewji13 on 2008-02-10
.

---

