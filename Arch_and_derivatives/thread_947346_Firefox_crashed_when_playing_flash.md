---
title: "Firefox crashed when playing flash"
date: 2008-10-14
forum: Arch and derivatives
---

### Post by Louis de Broglie on 2008-10-14
Well, In the recent days, I've been asking a lot of questions here :oops:

Here is one more :)

I am using OSS v4.1 . Installed flash from pacman and also installed libflashsupport-oss pacakage too. Flash plays with sound but every now and then firefox just crashes ( when playing flash movie ) :(

I found a workaround of this in the internet : I removed the packages I installed then installed flash from adobe web site. ( this time without libflashsupport-oss ).Now flash plays ok and firefox no longer crashes. But I hear no sound :(

---

### Post by handy on 2008-10-14
Are you using 32 or 64bit Arch?

---

### Post by Louis de Broglie on 2008-10-14
Sorry for being non-specific. 32 -bit and the flash version is 10 beta :)

**Edit : Just tried flash 9. No sound here too .**

---

### Post by Rumor on 2008-10-14
I think the best approach would be to go back to where you were at first with the packages through pacman. Remove whatever you downloaded and installed yourself, reinstall the flashplugin package with pacman.

Then start firefox from a terminal. Once (if) it crashes, then you'll have the error message in the terminal window that will help you figure out why it is crashing.

That same approach can be used to figure out your other question in the other thread about mplayer not being able to play a file. There would be a reason given in a terminal that you could research to see how you go about fixing it.

The command line is most helpful in diagnosing problems.

---

### Post by Louis de Broglie on 2008-10-14
Thank you very much for the tips. This is what I get when loading [www.meebo.com](www.meebo.com) which requires heavily on flash .

> 
**
Gtk:ERROR:gtkplug.c:201:gtk_plug_set_is_child: assertion failed: (!GTK_WIDGET (plug)->parent)
Aborted


---

### Post by Louis de Broglie on 2008-10-15
Nobody ? :(

---

### Post by fwojciec on 2008-10-15
Firefox often crashes when used with a buggy GTK theme.
> assertion failed: (!GTK_WIDGET (plug)->parent)
This would suggest that the problem has something to do with the gtk theme...

---

### Post by Louis de Broglie on 2008-10-15
I tried changing xfce theme into a gtk theme. And now flash is working. Hopefully this is the end of crashing :D

However, I get this in the terminal when I close firefox :

> (firefox:6169): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6169): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


Any idea ? :)

---

### Post by fwojciec on 2008-10-15
If I recall correctly the errors on closing Firefox have been there since early ff3 betas.  They're not something to worry about, in other words.  If you tried running every GTK application on your system from the CLI you'd notice that a lot of them produce error messages like these.

---

### Post by Cope57 on 2008-10-15
It is not FireFox's fault that the Adobe flash code has many bugs in it.
I use [swfdec-gnome]("http://packages.debian.org/search?suite=all&section=all&arch=any&searchon=names&keywords=swfdec-gnome") and [swfdec-mozilla]("http://packages.debian.org/search?suite=all&section=all&arch=any&searchon=names&keywords=swfdec-mozilla") myself, with no issues at all.

I can watch youtube videos, play flash games... and so on.

---

### Post by Louis de Broglie on 2008-10-15
Well, after restarting the pc , those messages are gone :) But firefox crashed again . This time segmentation-fault :(

I tried installing swfdec and swfdec-mozilla package from pacman. It installed correctly. But when I go visit youtube, I do not hear anything and also I do not see anything but a blank black screen although the slider shows that the video is streaming . Can you be a bit more specific about this ? :) Did you do anything do make it work ? :)

---

