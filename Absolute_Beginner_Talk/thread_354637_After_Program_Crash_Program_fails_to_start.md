---
title: "After Program Crash Program fails to start"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-02-06
I have been using the "Alexandria Book Collection Manager" to manage my extensive personal/professional library.  Recently it has been unexpectedly crashing, but could be restarted following the crash.

Now, the program refuses to start.  Using the GUI, Application>Office>Alexandria Book Collection Manager the program will not start.

I have tried uninstalling and reinstalling the program -- still nothing.

I have restarted the computer and operating system (Ubuntu 6.10) and still nothing.

How do I get this back?

Thanks for your help!

---

### Post by taurus on 2007-02-06
Can you run it from a terminal to see what's the error message is?

---

### Post by chaplanger on 2007-02-06
Here's a dumb question:
How do I run this from the terminal?
(Along with this -- where do I find executable files within the Linux file system?)

---

### Post by taurus on 2007-02-06
Do you know the exact name of that program?  If you right click on the icon/shotcut and go into Properties, it tells you the name; otherwise, look in /usr/bin.

---

### Post by chaplanger on 2007-02-06
Thanks!  Found it in /usr/bin

When I run the app from here this is what I get for output:

> david@david-desktop:~$ /usr/bin/alexandria
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
-----------------------
Alexandria just crashed
-----------------------
Timestamp: Tue Feb 06 09:06:41 CST 2007
Message: Not a book
Backtrace:
/usr/lib/ruby/1.8/alexandria/library.rb:66:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:53:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:52:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:92:in `loadall'
/usr/lib/ruby/1.8/alexandria/library.rb:86:in `loadall'
/usr/lib/ruby/1.8/alexandria/ui/main_app.rb:266:in `load_libraries'
/usr/lib/ruby/1.8/alexandria/ui/main_app.rb:84:in `initialize'
/usr/lib/ruby/1.8/alexandria/ui.rb:41:in `main'
/usr/lib/ruby/1.8/alexandria.rb:66:in `main'
/usr/bin/alexandria:10
Release: 0.6.1

Uname -a: Linux david-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
--
Please report this dump to 'alexandria-list@rubyforge.org' with some additional
information, such as the description of the crash and the steps to reproduce it
(if it's possible).
david@david-desktop:~$ 



Seeing this output -- any ideas as to he reason for the crash?

(Hmmm. . .  So I guess I need to report this to the Alexandria website . . .  but having seen how quickly such reports are addressed . . . I may be a long time without this program's functionality.

Any ideas for alternate programs that do this same type of book/library cataloguing?)

---

