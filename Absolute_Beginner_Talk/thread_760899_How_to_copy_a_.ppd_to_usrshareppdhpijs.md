---
title: "How to copy a .ppd to /usr/share/ppd/hpijs"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Frogbarf on 2008-04-20
This is an elementary problem with file permissions and ownership.

I have downloaded a .ppd file and now I want to copy it to a subdirectory in /usr/share/ppd.

However, that directory is owned by root and has read-only access for the rest of the world. When I try to paste, using either my normal user id or my admin id, Linux won't let me. Doesn't ask for the admin user password either.

As Archie said to Mehitabel, wothehell?

Do I have to go into terminal and issue a series of loathsome commands to do this? Why can't I do it using Gnome's file thingie?

---

### Post by drs305 on 2008-04-20
Well, a minimal terminal usage would be:
```
gksu nautilus &
```
This will open up the Gnome file thingie and allow you to put the file where you want. :)

added: if the file you downloaded is on your own desktop, you will find it in nautilus by opening "File system, home, <username>, Desktop".

---

### Post by wolfen69 on 2008-04-20
```
gksudo nautilus
```
this will give you temporary permission to copy it over

---

### Post by AndyCooll on 2008-04-20
You can use Nautilus, however the easiest way is to use the command line, yes.
You don't tell us exactly where you've saved the ppd to. If it's straight into your home directory then it would be:
```
sudo cp hpijs.ppd /usr/share/ppd/hpijs.ppd
```

:cool:

---

### Post by konungursvia on 2008-04-20
Or just

sudo nautilus

and enter your password, then the file manager you see open will have root privileges to do anything.

---

