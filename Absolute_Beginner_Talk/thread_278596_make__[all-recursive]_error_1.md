---
title: "make: *** [all-recursive] error 1"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by elnerion on 2006-10-16
I've been trying to get a file manager like windows commander running on ubuntu and so far I've tried linux commander and gnome file manager. I've managed to get through all the package dependencies (I think) but now both of them give me the same error after I run ./configure during make. Below is the one I got from linux cmd but they're both basically the same.

```
lucid@lucid-desktop:~/dloads/linuxcmd-0.5.2$ make
Making all in src
make[1]: Entering directory `/home/lucid/dloads/linuxcmd-0.5.2/src'
gcc -DPACKAGE=\"linuxcmd\" -DVERSION=\"0.5.2\" -DSTDC_HEADERS=1  -I. -I.  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -D_REENTRANT  -g -O2 -c callbacks.c
callbacks.c: In function ‘cb_file_delete’:
callbacks.c:545: error: invalid lvalue in assignment
make[1]: *** [callbacks.o] Error 1
make[1]: Leaving directory `/home/lucid/dloads/linuxcmd-0.5.2/src'
make: *** [all-recursive] Error 1

```

any ideas?

EDIT: Also tried this with xmms, got the same thing.

---

### Post by podunk on 2006-10-16
I can't really help you with the compile problem (you did proceed  the ./configure command with "sudo" – yes?) except to pass this link:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

xmms is in the repositories – why do you want to compile it?
System>Administration>Synaptic Package Manager>Search

A nice file manager that is sort of like what you want is Gnome Commander, it's in the repositories. 

I really like Krusader for Kubuntu – I don't know if it would work on Ubuntu? It's a KDE app in the repositories.

---

### Post by elnerion on 2006-10-17
ok I got gnome commander installed with synaptic and I found it in usr/lib but I don't know how to run it.

---

### Post by monktbd on 2006-10-17
maybe just 
> gnome-commander
in the terminal?

if not just write "gnome" in the terminal and hit tab to get some choices.
or maybe it is just gc?
(midnight commander uses mc)

---

