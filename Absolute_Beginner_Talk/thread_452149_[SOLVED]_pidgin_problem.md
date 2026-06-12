---
title: "[SOLVED] pidgin problem"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-23
i try to install pidgin but i get this error 

You must have the GLib 2.0 development headers installed to build.


how can i fix this ? thanks

---

### Post by Bachstelze on 2007-05-23
```
sudo apt-get install libglib2.0-dev
```

---

### Post by Princey on 2007-05-23
> **HunkieChan said:**
> i try to install pidgin but i get this error 

You must have the GLib 2.0 development headers installed to build.


how can i fix this ? thanks

```
sudo apt-get install libglib2.0-dev
``` or just search for libglib in synaptic

---

### Post by Bachstelze on 2007-05-23
I win :p

---

### Post by Fiyastone on 2007-05-23
```
sudo apt-get install libglib2.0-dev
```
That will install the development files to compile source code using the Glib.

An easier way though is to install the debian packages.  A very good resource for this another post found [here]("http://ubuntuforums.org/showthread.php?p=2647568")

A direct link would be [http://www.getdeb.net/app.php?name=Pidgin]("http://www.getdeb.net/app.php?name=Pidgin")

---

### Post by HunkieChan on 2007-05-23
You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.


^ what do i do now ?

---

### Post by Bachstelze on 2007-05-23
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by HunkieChan on 2007-05-23
well it seems i had to install something else called libxml.dev and i used the synaptic to install it and it works now.. so i guess this becomes a tutorial of pidgin on edgy

---

### Post by Princey on 2007-05-23
> **HymnToLife said:**
> I win :p

Lol hymntolife, want to show me the trophy? :p

---

### Post by Scrum on 2007-05-31
Hello, I have just upgraded from 6.10 to 7.04 but I have a problem installing Pidgin:

On ./configure, I get this error:
You must have libxml2 >= 2.6.0 development headers installed to build.

I tried installing glib and gtk as described above, but...
libglib2.0-dev is already the newest version.
libgtk2.0-dev is already the newest version.

I tried Synaptic, but when searching libxml2, it tells me that I already have it, version 2.6.27 even (which is obviously greater than 2.6.0...)

I`m no linux guru, so... can anyone lend me a hand here? :) Thanks!

---LATER----

Problem solved, had to install libxml2-dev also.  Hope this helps if others have same issue :)

---

### Post by sanguis on 2007-06-21
> **Fiyastone said:**
> 
An easier way though is to install the debian packages.  A very good resource for this another post found [here]("http://ubuntuforums.org/showthread.php?p=2647568")

A direct link would be [http://www.getdeb.net/app.php?name=Pidgin]("http://www.getdeb.net/app.php?name=Pidgin")

thank you this worked nicly

---

### Post by deuscapturus on 2007-09-26
FYI

You will also need to install SSL libraries to get msn working:

```
sudo aptitude install libnss-dev
```

---

### Post by myhnet on 2008-03-03
> **deuscapturus said:**
> FYI

You will also need to install SSL libraries to get msn working:

```
sudo aptitude install libnss-dev
```


should be libnss3-dev
:popcorn:

---

### Post by FrozenFox on 2008-03-03
Why are you compiling pidgin anyway? getdeb.net has a .deb for the newest version.

---

### Post by kevdog on 2008-03-03
If you want to compile pidgin (which I recommend since you can then learn how to compile and install various third party plugins), the best guide I found is here:
[http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin)

It gives you all the dependencies you need.  I would cut and paste the commands listed in the guide to the command prompt.

---

### Post by HunkieChan on 2008-03-03
it works now , thanks guys :)

---

