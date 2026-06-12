---
title: "[SOLVED] filezilla not working after X11 update"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by shadow-of-sin on 2008-01-19
I get this error when trying to run filezilla:
```
The program 'filezilla' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 201 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I'm pretty sure that it was todays update that caused this problem. Anyone know how to resolve it?

---

### Post by asmoore82 on 2008-01-19
first, I would try moving filezilla's private settings for your user account to a backup location:
open a terminal and:
```
mv .filezilla .filezilla_backup
```
Then, try to run Filezilla as normal.

---

### Post by shadow-of-sin on 2008-01-19
Tried that but it still produces the same error message.

---

### Post by asmoore82 on 2008-01-19
have you restarted since the updates; it's normally not necessary but it couldn't hurt.

---

### Post by shadow-of-sin on 2008-01-19
Yeah I have restarted.

---

### Post by asmoore82 on 2008-01-19
something funny happened today with an xserver package and a 403 forbidden error;
try to get your system fully up to date again and see if it catches another package ...
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by asmoore82 on 2008-01-19
ahh... don't forget to undo the filezilla move ...
```
mv -f .filezilla_backup .filezilla
```

---

### Post by shadow-of-sin on 2008-01-19
Thanks, after I ran sudo apt-get update/upgrade and restarted, FileZilla works fine.

---

