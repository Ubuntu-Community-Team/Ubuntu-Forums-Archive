---
title: "Unable to locate theme engine in module_path: &quot;ubuntulooks&quot;"
date: 2007-08-20
forum: Art &amp; Design
---

### Post by Jota1234 on 2007-08-20
I installed gtk+-2.10, glib-2.12, cairo-1.4, and gtk-engines-2.10 today, and now every gtk based application I open gives the following error:

Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks"

In addition, it seems as though there are issues with rendering .svg files in applications, which makes some apps look a little off and makes a few unusable.

I assume the two problems are related.

The ubuntulooks shared libraries are installed and are in the directory /usr/lib/gtk-2.0/2.4.0/engines/

I tried reinstalling the gtk2-engines-ubuntulooks (version 0.9), but no help.

Any ideas?

---

### Post by Jota1234 on 2007-08-21
I guess I answered half of my own question.  The following site was useful in solving the error message, especially the part about the GTK_PATH environment variable and the search procedure for theme engines.

[http://www.gtk.org/api/2.6/gtk/gtk-running.html](http://www.gtk.org/api/2.6/gtk/gtk-running.html)

GTK+ based programs still don't seem to want to render .svg files, which was apparantly the bigger issue.  Some programs have a fallback that displays other items (causing an altered appearance), and in other programs, they are just invisible.

Anyone else encountered this one before, or any ideas about fixing it?

---

### Post by Jota1234 on 2007-08-21
Long story short, typical newbie errors.  I had some libraries in the wrong places and apparantly some broken dependencies (although I never really pinned down which one exactly was the problem).

I re-installed a bunch of the dependencies and their latest versions.  Here's what worked for me (installed in this order):

librsvg-2.18
tiff-3.8
cairo-1.4
pango-1.16
glib-2.12
gtk-engines-2.10
gtk+-2.10

That fixed the .svg problem.

The error message was resolved by moving the ubuntulooks shared libraries to the right place as described at

[http://www.gtk.org/api/2.6/gtk/gtk-running.html](http://www.gtk.org/api/2.6/gtk/gtk-running.html)

---

### Post by peterdk on 2008-05-16
Thanks, had the same issue, and moved the ubuntulook files to /usr/local/***
Now it finally works :)

---

### Post by junglism on 2008-11-26
wow, thanks for this solution peterdk, worked a treat!

---

### Post by Mike.lifeguard on 2009-06-26
> **peterdk said:**
> Thanks, had the same issue, and moved the ubuntulook files to /usr/local/***
Now it finally works :)

How do you find those files? I don't know where to look in order to move them.

---

### Post by andrewmcdonough on 2009-07-14
I also got this error, but it happened when I upgraded from 8.10 to 9.04.  I fixed it by updating the package gtk2-engines-ubuntulooks:

[FONT=Courier New]  sudo apt-get install gtk2-engines-ubuntulooks
[/FONT]
---
[Andrew McDonough]("http://www.andrewmcdonough.com")

---

### Post by Tapas Bose, India on 2009-07-30
I also got this problem.

solution : sudo apt-get install gtk2-engines-ubuntulooks

---

### Post by ticket on 2009-08-23
Installing 

    gtk2-engines-ubuntulooks 

on Jaunty 9.04 automatically removed these packages:

   human-theme
   ubuntu-artwork
   ubuntu-desktop

Is that going to cause problems in the future?
(e.g. the 'official' human-theme has now disappeared).

Please can someone advise!

---

### Post by MichaelGld on 2011-02-15
> **Tapas Bose, India said:**
> I also got this problem.

solution : sudo apt-get install gtk2-engines-ubuntulooks

I tried this, but got the following.

```
mike@mike-desktop:~$ sudo apt-get install gtk2-engines-ubuntulooks
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gtk2-engines-ubuntulooks is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  human-theme
E: Package gtk2-engines-ubuntulooks has no installation candidate
```

---

