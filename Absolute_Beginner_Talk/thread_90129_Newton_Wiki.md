---
title: "Newton Wiki"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by maskkkk on 2005-11-14
This program ([http://freshmeat.net/projects/newtonwiki/](http://freshmeat.net/projects/newtonwiki/)) just freezes when I try to use it.  (I compiled it from src)  No window popus up or anything, and there aren't any error messages...What's the deal here?

---

### Post by az on 2005-11-14
I dunno.  Please post the readme in the tarball which lists the  requirements for building it.

Also, launch it from a terminal and post any error output.

---

### Post by brim4brim on 2005-11-14
[https://sourceforge.net/projects/newton/](https://sourceforge.net/projects/newton/)

It's a beta so it could still be pretty buggy.

---

### Post by ardchoille on 2005-12-16
I am having problems too:
Newton doesn't start up, running from a term produces no errors and doesn't return my prompt. How does one use Newton?

---

### Post by Eyez on 2006-04-05
same here...i tried running it from terminal and it doesn't output anything...

---

### Post by Eyez on 2006-04-05
ok...i tried running it from the applet and it crashed.

---

### Post by htinn on 2006-04-06
There's a bug associated with the python, it looks like.

[http://sourceforge.net/mailarchive/forum.php?thread_id=10034292&forum_id=45438](http://sourceforge.net/mailarchive/forum.php?thread_id=10034292&forum_id=45438)

> This bug is suspected to be in Firefox. See Malone #26436[1] and
MozillaBugzilla #325884[2]. I certainly hope they can fix it soon!

Cheers,
~djc

[1] [https://launchpad.net/distros/ubuntu/+source/firefox/+bug/26436](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/26436)
[2] [https://bugzilla.mozilla.org/show_bug.cgi?id=325884](https://bugzilla.mozilla.org/show_bug.cgi?id=325884)

---

### Post by Mustard on 2006-04-06
It anyone wants to try something different that has the same functionality (but is not gnome specific), you could try Tomboy (I find this interface a bit ugly), or Zim is a nice looking interface written in Gtk-Perl.  I started with Tomboy and then switched to Zim as my favourite personal desktop wiki.

Tomboy is available in the repositories.

I've installed Zim from the tar.gz and can help anyone with the process if they are interested.  I use the checkinstall command as a substitute for 'make install', so as to create a .deb package.  I suppose I could just throw the .deb on some site somewhere and people could try it, but I have no experience with finding hosting for a .deb package, nor any experience with what happens when someone uses on another system ie what dependencies issues come up et.

[http://freshmeat.net/projects/zim/](http://freshmeat.net/projects/zim/)

Zim is pretty active with development.  I've updated 3 times since the start of the year I think.

[[IMG]http://img86.imageshack.us/img86/874/zim9zp.th.png[/IMG]](http://img86.imageshack.us/my.php?image=zim9zp.png)

-edit-

I chucked the debian package for Zim I built with checkinstall on a hosting site if anyone wants to try installing with it.

[http://www.savefile.com/files/9271688](http://www.savefile.com/files/9271688)

Hmm..I'm a bit disappointed that the free hosting site appended its own extensions to the name of the file, but I guess you can always rename it to what it normally was...

zim-0.14_0.14-1_i386.deb

---

