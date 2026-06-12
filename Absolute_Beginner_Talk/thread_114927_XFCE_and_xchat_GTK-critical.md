---
title: "XFCE and xchat? GTK-critical"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by Oaf on 2006-01-09
Yello.
After installing xubuntu-desktop and choosing it on sessions, xchat refused to work. It does start up and after clicking on the connect tab on servers list the following error occurs:

(xchat:8628): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(xchat:8628): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
The program 'xchat' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 14085 error_code 9 request_code 14 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Same problem after running with --sync...?
Any ideas, help would be greatly appreciated as I failed to find similar probs on the forums - or am going blind :)
Thanks in advance.

---

