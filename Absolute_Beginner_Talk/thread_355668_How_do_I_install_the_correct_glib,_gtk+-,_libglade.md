---
title: "How do I install the correct glib, gtk+-, libglade, and libgnome packages?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-02-07
For Ubuntu 2.6.15-27-386 (6.06 / Dapper), Gnome 2.1.3.

I'm trying to install the *glipper* clipboard manager for gnome.  Slowwwly, I've been using glipper's *./configuration* environment validation pre-processor to identify missing infrastructure, then using the Synaptic GUI acquire and install the (absurd number of) modules and packages that the glipper installation evidently requires.

Now glipper is unhappy because (line breaks added for readability):

> 
configure: error: Package requirements (
glib-2.0 >= 2.6.0
gtk+-2.0 >= 2.6.0
libglade-2.0 >= 2.0.0
libgnome-2.0 >= 2.0.0
) were not met

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'libgnome-2.0' found
I've heretofore been using Synaptic to identify and then install other missing  required by glipper's *./configure* tool, but my Synaptic GUI *Search* tool can't find these packages.  So, can someone please tell me:[LIST]
[*]Where and how to acquire the correct packages?
[*]How to correctly install the packages so that glipper's .configure program will be happy?[/LIST]Cheers & thanks,
Ric
SFO

---

### Post by ComplexNumber on 2007-02-07
i think it may well be because:
a) dapper contains less up to date packages than edgy
b) you're probably trying to install the very latest glipper.


try installing the last version of glipper or the one before that. [here]("http://sourceforge.net/project/showfiles.php?group_id=167085") is where you can download the source. 
can i assume that glipper is not in the dapper repos?


if you get any problems, post back.

---

### Post by Phrawm48 on 2007-02-07
Sorry, this newbie is confused.   First, the preceding version of glipper displays exactly the same error messages.

Can someone please advise the command line that I can use to determine whether any version of these libraries has been installed?

If they aren't installed, how do I acquire them and correctly (that is to say, safely and without screwing up the rest of my working system) install them?

Finally, no, the Synaptic Search tool can't locate anything glipper.  And this newbie is about to abandon glipper as being wayyyyy too hard to install...

Cheers & thanks for your help,
Ric
SFO

---

### Post by ComplexNumber on 2007-02-07
can you not check by doing a search in synaptic to see what you have? 

you need to have the following:
libglib2.0-dev
libgtk2.0-dev
libgnome2-dev
libglade2-dev

install them (it will just skip past the ones that are installed), so type in:
[B]sudo apt-get install libglib2.0-dev libgtk2.0-dev libgnome2-dev libglade2-dev

[/B]then try installing the latest glipper. if that doesn't work, try the next one down.

---

### Post by konst88 on 2007-02-07
```
sudo apt-get build-dep glipper 
```
Will install all build dependencies.

---

### Post by Phrawm48 on 2007-02-07
Thanks.

The command line downloaded and installed 38+ libraries but did report some problems.  When I then ran glipper's ./configure, I received a very similar error message:

> 
No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'libgnome-2.0' found


"sudo apt-get build-dep glipper" produced "unable to find a source package for glipper" even though I ran the command in the directory containing the entire contents of the glipper .gz file.

This is now wayyyy more trouble than it's worth -- I'm abandoning glipper until it's ready for prime time...

Thanks 'gain for your help,
Ric
SFO

---

### Post by Phrawm48 on 2007-03-21
Sometimes the best tool for working with Linux is a lot of patience.  It took more than a little while to sort this out for myself, but a version of Glipper that's compatible with Dapper can be downloaded from:

[http://www.getdeb.net/release.php?id=54](http://www.getdeb.net/release.php?id=54)

Other useful threads on this forum are:

[**how to install glipper**]("http://ubuntuforums.org/showthread.php?t=349783&highlight=glipper+dapper")

**[Anyone got Glipper to work?]("http://ubuntuforums.org/showthread.php?t=186375&highlight=glipper+dapper")**

Thanks again to all who made an effort to help.

Cheers & hope this helps,
Ric
SFO

---

