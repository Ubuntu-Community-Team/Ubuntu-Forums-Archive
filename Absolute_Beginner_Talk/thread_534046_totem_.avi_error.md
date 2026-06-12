---
title: "totem .avi error"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-24
nolan@LinBox:~/Desktop$ totem untitled.avi
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I've installed libxine1 so thats not it. Any ideas?

---

### Post by mysticmatrix on 2007-08-24
Do you happen to be using Compiz Fusion and/or Beryl?

---

### Post by swoll1980 on 2007-08-24
compiz

---

### Post by mysticmatrix on 2007-08-24
See if this fix works:

Open Applications --> Acesseries --> Terminal
Type the following code:

```
gstreamer-properties 
```

Under the Video Tab, select the option:
```
Plugin: X Video System(No Xv) 
```

Reply back if this doen't fix your problem

---

### Post by swoll1980 on 2007-08-24
That worked good. Thanks

---

### Post by mysticmatrix on 2007-08-24
Please mark the thread as solved

---

