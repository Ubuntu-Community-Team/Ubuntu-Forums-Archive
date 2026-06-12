---
title: "Rhythmbox"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by derouge on 2006-07-04
Having a few problems with Rhythmbox. Everytime I launch it I get a message box saying it has encountered a critical error, and gives me the option to inform developers, restart the app, etc. The output from the terminal is

> 
(rhythmbox:6369): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `fi lename != NULL' failed

(rhythmbox:6369): Rhythmbox-WARNING **: Unable to load icon media-eject

Rhythmbox-ERROR **: file rb-entry-view.c: line 1851 (rb_entry_view_resort_model) : assertion failed: (sort_data)
aborting...


I think the first error is the one that is causing the shutdown, but I'm not really sure what the problem is. It worked great before I upgraded to Dapper. I've been running Dapper Drake for a few weeks now and have solved all my other issues. Rhythmbox is the only problem that remains ..

---

### Post by derouge on 2006-07-04
Update: I just used "sudo rhythmbox" and it now seems to be working. It launched the setup stuff (selecting music folders, etc). I do not understand why this didn't work on the initial launch .. if someone could possibly explain.

---

