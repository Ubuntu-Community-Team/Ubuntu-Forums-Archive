---
title: "Pitivi Problem"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Makaio on 2007-04-14
I just installed Pitivi and it is not starting up at all, despite the toolbar telling me that it is. 

Do I need to install any additional plugins or any other components?

Thanks in advance for your help.

---

### Post by caffienefree on 2007-04-15
How did you install pitivi, from the repositories or from source?
What ubuntu version are you running?
Open up a terminal, and type **killall pitivi**. Then, type **pitivi**. Does it start up?

---

### Post by vanadium on 2007-04-15
Part of the problem might be that Pitivi is software in a very early stage of development. It might not yet be stable enough for production.

---

### Post by Darin on 2007-04-19
Hi, I've had the same problem, and it has happened on other programs I have installed on Ubuntu. You click the icon, and the taskbar says it's opening, but it never does. Running it in terminal I get:

```
darin@darin-desktop:~$ pitivi
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 46 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

If I run "pitivi --sync" it opens fine. I'm not very experienced in all this, so I'm not sure if there's anything I can do to fix it or change it, but like I said, it has happened on several programs I've installed on Ubuntu 6.10. I'm going to upgrade to 7.04 over the weekend, so hopefully the same things won't happen after that!

- Darin

---

