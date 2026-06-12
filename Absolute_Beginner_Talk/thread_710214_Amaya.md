---
title: "Amaya"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by U-b-u-n-t-u on 2008-02-28
Hi

I just installed amaya but when ever I try to open it i pops up real quick and dissapers.
can you help?

---

### Post by frankos44 on 2008-02-28
I havent got amaya loaded here but it could be permissions or membership rights, Try:

$ sudo amaya

Dont continue to run this program this way. Let me know the outcome?

---

### Post by U-b-u-n-t-u on 2008-02-28
Thanks, I did that and this is what I got:

07:19:38 AM: Deleted stale lock file '/home/adamjackson/.amaya-root'.

(amaya:8295): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 6987 error_code 8 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

then it pops up again for a half a second.

---

### Post by frankos44 on 2008-02-28
I installed it on my PC here, Ubuntu 64 bit 7.10 and all seemd to be OK. Which flavour of Ubuntu are you  using?

You might try:

remove GTK and amaya using package manager

sudo rm -r '/home/adamjackson/.amaya-root

Re- install again

---

### Post by SOULRiDER on 2008-02-28
Do not remove GTK or amaya, just reinstall them.

```
sudo aptitude install amaya libgtk2.0-0
```

---

### Post by U-b-u-n-t-u on 2008-02-28
I did that but it didn't help.  But what is GTK?

---

### Post by frankos44 on 2008-02-29
> **U-b-u-n-t-u said:**
> I did that but it didn't help.  But what is GTK?

This should give you a good insite to GTK  [http://www.gtk.org/](http://www.gtk.org/)

---

