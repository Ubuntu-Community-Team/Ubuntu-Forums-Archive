---
title: "Gnome Terminal doesn't start"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by mdoyle on 2007-08-29
My Gnome Terminal seems to be broke. When I try to start it from the Applications menu, there is a box in the bottom panel that says Starting Application, but when that goes away the Terminal still doesn't start. I have been getting around using xterm, but that really doesn't fix my problem, just lets me do stuff. I'd like to be able to fix whatever is wrong with Gnome's Terminal.

---

### Post by diatribe on 2007-08-29
try running gnome-terminal from an xterm session and see if it displays any errors

---

### Post by por100pre1 on 2007-08-29
Try installing **xterm** with Synaptic, then run it pressing ALT+F2 and typing **xterm**.

From xterm run:

```
gnome-terminal
```

check whatever errors occur.

---

### Post by mdoyle on 2007-08-29
Gdk-ERROR **:  The program "gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
   (Details: serial 111 error_code 2 request_code 78 minor_code 0)
   (Note to programmers: normally, X errors are reported by asynchronously;
    that is, you will recieve the error a while after causing it.
    To debug your program, run it with the --sync command line
    option to change this behavior. You can then get a meaningful
    backtrace from your debugger if you break on the gdk_x_error() fuction.)
aborting...
Aborted (core dumped)

---

### Post by JymmyZ on 2008-01-11
Any solution to this? I get the same problem.  I just did a fresh Gutsy install and it used to work on my old Gutsy install but now it doesn't.

---

### Post by pure1uck on 2008-02-02
yeah, i got the same exact problem.  how does something like that happen?

---

### Post by wmbclark on 2008-02-08
Same problem here.  This only started after I exchanged my Matrox G450 for an nVidia 6800 and the nVidia proprietary driver.

---

### Post by nosebreaker on 2008-03-01
Same error for me, I don't know what I updated, I did upgrade the nVidia drivers recently though (along with lots of other things).  I don't use the terminal unless i am going to SSH somewhere, so for now xterm is fine but this is a rather annoying bug!

---

