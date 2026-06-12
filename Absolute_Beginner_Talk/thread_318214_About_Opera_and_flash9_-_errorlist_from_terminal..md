---
title: "About Opera and flash9 - errorlist from terminal."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-12-13
Have opera Version 9.02, Build 434 on my gnome/dapper 686 box. As seen in previous posts I've been having problems with opera freezing up and then using 100% CPU - capacity. I think this is a known issue. Funny thing is that is works most of the time, so don't want to stop using. I've been using opera for many years and I do not want to quit now. 

Started Opera in terminal though, and pasting here the result from my latest crash. maybe this can help someone help me in getting it stable again? Or are there other tricks to it? Like installing flash 7 again?

Terminal:

lodravah:~$ opera -notrayicon

(process:22133): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertio n failed, use IA__g_type_init() prior to this function

(process:22133): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_ IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to c all gtk_init(0,0);
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 2063 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
opera: Plug-in 22133 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plu g-ins.

(process:22152): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertio n failed, use IA__g_type_init() prior to this function

(process:22152): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_ IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to c all gtk_init(0,0);
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1609 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
opera: Plug-in 22152 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plu g-ins.

(process:22160): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertio n failed, use IA__g_type_init() prior to this function

(process:22160): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_ IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to c all gtk_init(0,0);
Killed


There y'all go :)

---

### Post by shilliard on 2006-12-28
I get the same occassional crash using Opera 9.10 and Flash 9 in Dapper, looks like a problem with opera and the flash plugin.

Very annoying cause Opera works great most of the time but just crashes once in a while when I click "Back"

---

