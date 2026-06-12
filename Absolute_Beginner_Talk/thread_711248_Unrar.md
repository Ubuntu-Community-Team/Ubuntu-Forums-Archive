---
title: "Unrar"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by SimonHalliday on 2008-02-29
I have a problem with unraring a file.  I have unrar installed (used sudo apt-get) and have done recent updates to check that everything was all well there.  I also installed p7zip to see if that would work and nothing happened.  The file is a RAR 3.70 file.  Am I doing something wrong? 

I have looked at a number of the forum posts but haven't found anything helpful.  

I'm running 7.10. 

Thanks.

---

### Post by jan quark on 2008-02-29
have a look at this thread perhaps

[http://ubuntuforums.org/showthread.php?t=433223](http://ubuntuforums.org/showthread.php?t=433223)

---

### Post by SimonHalliday on 2008-02-29
Tried using Ark and it didn't work.  I then uninstalled and re-installed unrar and unrar-free to see if that helped.  But I didn't see any change.  

Any other ideas?

---

### Post by SteelDragon on 2008-02-29
Can't tell if you're doing something wrong if you don't post what you're doing, but the obvious 'unrar file.rar' won't work. What you need is:
```
unrar x file.rar
```
to extract the entire heirarchy, or
```
unrar e file.rar
```
to extract all files to the current directory.

---

### Post by SimonHalliday on 2008-02-29
It's now telling me that it's not a rar archive.  I am going redo this from the start and recopy the file from my external HDD in case something got messed up.  Will try to report back when I've done that. 

I had tried both of 
unrar e file.rar
and
unrar x file.rar

Previously.  Was trying to see if I could do it in a GUI though to explain 'How easy it is' to my wife.

---

