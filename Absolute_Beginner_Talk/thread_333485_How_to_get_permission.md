---
title: "How to get permission?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Quby on 2007-01-07
When trying to alter fstab in /ect I get the error message
What do i need to obtain permission?  Is there an administrator account which i need to log into?  What would its password be?

You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

---

### Post by MkfIbK7a on 2007-01-07
do 
gksudo gedit /path/of/file/and/name/
put in your password when it asks

---

### Post by Quby on 2007-01-07
(gedit:26780): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Thats what it returns as

What did i do wrong? :-k

---

### Post by MkfIbK7a on 2007-01-07
nothing came up?
if not do
gksudo nano /name/and/path/of/file/

---

### Post by halitech on 2007-01-07
to get permission you need to ask nicely ;)

try 

```

sudo gedit /etc/fstab

```

then put in your password and it should load the fstab file with no errors.

---

### Post by Quby on 2007-01-07
that worked.. so it was a difference of gk in front of sudo.. 
okay, thanks for your help.

---

### Post by taurus on 2007-01-07
Either use

```
gksudo gedit /etc/fstab
```
or
```
sudo nano -w /etc/fstab
```

p.s.  And that message is a warning so gedit should pop up with /etc/fstab.

---

### Post by MkfIbK7a on 2007-01-07
well you really shouldnt just use sudo it can mess up your files permissions pretty badly but if it worked...:D

---

### Post by Quby on 2007-01-07
> **wert613 said:**
> well you really shouldnt just use sudo it can mess up your files permissions pretty badly but if it worked...:D

Hehe.. well now i know :( 
But yes, it worked!

---

### Post by halitech on 2007-01-07
> **wert613 said:**
> well you really shouldnt just use sudo it can mess up your files permissions pretty badly but if it worked...:D

I know gksudo is supposed to be to start graphical programs from the terminal with root(or sudo) permission but I'd never heard that running them as just sudo could mess up file permissions. 

in the nano example, you use the -w switch, what does that do? ( too lazy to try and find it in the man pages right now)

---

### Post by taurus on 2007-01-07
To prevent lines that are longer than 80 characters to "wrap" to the next line.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by MkfIbK7a on 2007-01-07
>  in the nano example, you use the -w switch, what does that do? ( too lazy to try and find it in the man pages right now)

its ok to use sudo to do nano but try not to use it for gedit...

---

### Post by MkfIbK7a on 2007-01-07
this thread
[http://www.ubuntuforums.org/showthread.php?t=331643&highlight=mess+up+file+permissions](http://www.ubuntuforums.org/showthread.php?t=331643&highlight=mess+up+file+permissions)
five posts down

---

### Post by halitech on 2007-01-07
ok, maybe I'm just dense today but other then the fact that if you close the terminal by mistake you will cause the other window to close as well I still don't see much of a difference as you still can't do anything with that terminal until you close the app but I don't see how making changes to a file and then closing it without saving (which would basically be the effect of closing the terminal window) will mess up file permissions.

I'll just take your advice and not tempt the great god murphy :)

---

### Post by MkfIbK7a on 2007-01-07
lol good idea:mrgreen:

---

### Post by Quby on 2007-01-11
Ok, back again..
This time i wonder how do i put files into a folder which tells me i need admin privileges for?
or put a folder into a folder which tells me i need admin privileges?

---

### Post by taurus on 2007-01-11
```
sudo mv **filename** **destination**
man mv
```

---

### Post by Quby on 2007-01-11
thanks!  Question answered!

---

