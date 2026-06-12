---
title: "DVDRIP problems"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Bias on 2007-03-21
Hi,

Been struggling with this for a couple of evenings now.

I have followed the instructions in the desktop guide but am not getting anywhere.

When I run dvdrip from the command line I get:-

Can't load '/usr/lib/perl5/auto/Gtk/Gtk.so' for module Gtk: libgtk-1.2.so.0: cannot open shared object file: No such file or directory at /usr/lib/perl/5.8/DynaLoader.pm line 225.
 at /usr/lib/perl5/Gtk/Gdk/Pixbuf.pm line 4
Compilation failed in require at /usr/lib/perl5/Gtk/Gdk/Pixbuf.pm line 4.
Compilation failed in require at /usr/share/perl5/Video/DVDRip/GUI/ImageClip.pm line 14.
BEGIN failed--compilation aborted at /usr/share/perl5/Video/DVDRip/GUI/ImageClip.pm line 14.
Compilation failed in require at /usr/share/perl5/Video/DVDRip/GUI/Project.pm line 16.
BEGIN failed--compilation aborted at /usr/share/perl5/Video/DVDRip/GUI/Project.pm line 16.
Compilation failed in require at /usr/share/perl5/Video/DVDRip/GUI/Main.pm line 18.
BEGIN failed--compilation aborted at /usr/share/perl5/Video/DVDRip/GUI/Main.pm line 18.
Compilation failed in require at /usr/bin/dvdrip line 91.

Have to admit I'm somewhat lost here.

Any help appreciated.

Nick.

---

### Post by Bias on 2007-03-22
Well, I went to bed shortly after that post with the hope that when I woke up there would be some suggestions as to what I could try to resolve this but it would appear that I am a sad and lonely psycho clown :)

---

### Post by MrKlean on 2007-03-22
I would try to install it from Synaptic... see iy you get the same errors ; )  Just a thot ; )

---

### Post by Bias on 2007-03-22
Not quite so sad and lonely :), thank you for your reply.

I did install this from the synaptic package manager, I also installed the codecs in the instructions:-

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

The guide tells me I can run this from terminal by typing dvdrip, the above output is what I get when I do this.

Not at the machine at the moment so can't actually try anything but I'm thinking along the lines of complete uninstalls of all that the guide suggests followed buy a reboot (probably not required) then go through the guide again from scratch. Not very opptimistic though.

No doub't I'll get it going eventually, so far I am enjoying my conversion to Ubuntu.

---

