---
title: "how come I can't cd/"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-04-18
somebbody tell what I am over llooking


```
harry@harry-desktop:~$ cd qtella-0.7.0
bash: cd: qtella-0.7.0: No such file or directory
harry@harry-desktop:~$ cd qtella-0.7.0
bash: cd: qtella-0.7.0: No such file or directory
harry@harry-desktop:~$ cd qtella-VERSION
bash: cd: qtella-VERSION: No such file or directory
harry@harry-desktop:~$ cd /qtella-VERSION
bash: cd: /qtella-VERSION: No such file or directory
harry@harry-desktop:~$ cd /qtella-0.7.0
bash: cd: /qtella-0.7.0: No such file or directory
harry@harry-desktop:~$ cd /qtella-0.7.0/
bash: cd: /qtella-0.7.0/: No such file or directory
harry@harry-desktop:~$ cd home/harry/qtella-0.7.0/
bash: cd: home/harry/qtella-0.7.0/: No such file or directory
harry@harry-desktop:~$ cd home/harry/Desktop/qtella-0.7.0
bash: cd: home/harry/Desktop/qtella-0.7.0: No such file or directory
harry@harry-desktop:~$ 

```

---

### Post by Can+~ on 2008-04-18
cd is to access a directory, apparently, you are trying to access a file.

cd - access folder
ls - list folders and files on the current folder

What do you want to do? Edit it? Execute it?

Btw, in the repository (Applications>Add/Remove), there's an application called Gnutella, it should satisfy your needs, and it's easy to install and execute (as most things on the repository).

---

### Post by joshrobinson on 2008-04-18
is the file on your desktop?

---

### Post by rogirwin on 2008-04-18
Try This:

```
locate qtella-0.7.0
```

or if it dosen't work:

```
find / | grep qtella-0.7.0
```

---

### Post by harryliddic on 2008-04-18
It is staring right at me and I am following the instructions for confiquring qtella from a forum staff member

---

### Post by joshrobinson on 2008-04-18
are you sure you extracted it? if you right click it, does it say "extract here"?
if not

```
cd Desktop
```
```
cd qtella-0.7.0
```

---

### Post by harryliddic on 2008-04-18
thanks that did the trick. I have run the configure file and everything when as it should but now it balks at the make command.

---

### Post by joshrobinson on 2008-04-18
> **harryliddic said:**
> thanks that did the trick. I have run the configure file and everything when as it should but now it balks at the make command.

could you post the output of your make command

---

### Post by garyed on 2008-04-19
try   

```
  cd Desktop/qtella-0.7.0
or  cd /home/harry/Desktop/qtella-0.7.0  
```

You might have forgot the "/" before home/harry...... assuming you're spelling it right

---

### Post by harryliddic on 2008-04-19
It is pretty simple

```
harry@harry-desktop:~/Desktop/qtella-0.7.0$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by joshrobinson on 2008-04-19
> **harryliddic said:**
> It is pretty simple

```
harry@harry-desktop:~/Desktop/qtella-0.7.0$ make
make: *** No targets specified and no makefile found.  Stop.

```

looks like ./configure kicked out an error and never made a makefile
qtella is a QT/Kde application, and if your running ubuntu/gnome then you would def get an error because you would need the QT/Kde developmental libraries

have you thought of doing what Can+~ said above, and use Gnutella

```
sudo apt-get install gtk-gnutella
```
just installing this one will save you from installing alot of other software that you really wont use much

---

### Post by harryliddic on 2008-04-19
thank you for that I downloaded Qt4 a few days ago the includes are probably hid  away in some dusty folder.

---

