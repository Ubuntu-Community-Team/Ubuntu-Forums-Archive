---
title: "temp. root permission in gui"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-02-22
I was wondering if there is a way to have permission to move files in a "root owned" folder in the gui interface. without having to sign in as root?

---

### Post by chimera on 2006-02-22
you can run nautilus in root mode by

```

sudo nautilus

```

or, if you're using KDE, you can do similarly with konqueror by

```

sudo konqueror

```

---

### Post by suRoot on 2006-02-22
Well, I'm sure there's some pretty gui way of doing it, but this works for me... open a console & type:

```
sudo cp /home/baz/httpd.conf /root/
```
... if you just wanted to copy the file 'httpd.conf' from your home directory to /root

```
sudo cp /home/baz/* /root
```
... if you wanted to copy all files from your home directory to /root

```
sudo cp -R /home/baz/* /root
```
... if you wanted to copy everything (files & directories) from your home directory to /root

You could substitute 'mv' for 'cp' if you wanted to move as opposed to copy.

---

### Post by Mustard on 2006-02-22
[QUOTE=chimera]you can run nautilus in root mode by

```

sudo nautilus

```

or, if you're using KDE, you can do similarly with konqueror by

```

sudo konqueror

```[/QUOTE]

When doing it from gnome, you really should use ..

```
gksudo nautilus
```

There is a chance you can corrupt your system if you just use sudo when starting some graphical applications.  I believe the corruption is recoverable, but not everyone would know or understand what has occured or how to reverse it.

---

