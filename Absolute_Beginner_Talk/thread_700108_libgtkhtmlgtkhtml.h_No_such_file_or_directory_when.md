---
title: "libgtkhtml/gtkhtml.h: No such file or directory when installing GPHPEdit"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by mr_tk on 2008-02-18
Hello!

New Ubunutu user here.

I'm trying to install GPHPEdit version 0.9.91 on my Ubunutu Gutsy 7.10 (server) with a GNOME desktop installed.

After running ./configure and get presented with some packages missing (listed below), I came to face the problem of not finding the gtkhtml.h file under libgtkhtml when running make! I looked and couldnt find a solution anywhere! In the Synaptic Package Manager, when I search for libgtkhtml, the list of installed packages I get are:

libgtkhtml2-0 installed version 2.11.1-0ubuntu1
libgtkhtml3.14-19 installed version 3.16.1-0ubuntu1
libgtkhtml3.8-15 version 1:3.13.5-1

The packages that were missing during the ./configure process were:

gtk+-2.0
libgnomeui-2.0
gnome-vfs-2.0
libgtkhtml-2.0

all of which I believe were installed properly since I the ./configure file processed successfuly.

A glimpse of where the error shows up when running make is here:

```

In file included from classbrowser.h:34,
                 from classbrowser.c:27:
tab.h:37:32: error: libgtkhtml/gtkhtml.h: No such file or directory
In file included from classbrowser.h:34,
                 from classbrowser.c:27:
tab.h:60: error: expected specifier-qualifier-list before ‘HtmlDocument’
In file included from classbrowser.c:29:
main_window_callbacks.h:31:39: error: libgtkhtml/layout/htmlbox.h: No such file or directory
main_window_callbacks.h:32:43: error: libgtkhtml/layout/htmlboxtext.h: No such file or directory
classbrowser.c: In function ‘classbrowser_update’:
classbrowser.c:660: error: ‘Editor’ has no member named ‘filename’
classbrowser.c:661: error: ‘Editor’ has no member named ‘filename’

```

Any suggestion/adivce is greatly appreciated.

Thanks,

T

---

### Post by paultag on 2008-02-18
```


tab.h:37:32: error: libgtkhtml/gtkhtml.h: No such file or directory


```

Did you happen to install the -dev sources?

Try installing these:


libgtk-dev
libgnomeui-dev
libgnome-vfs-dev
libgtkhtml2-dev


and if needed:

libgtkhtml3.14-dev
 or
libgtkhtml3.8-dev

They should all be in the repository, you should be able to find them in Synaptic,

Cheers,
Paul

---

### Post by mr_tk on 2008-02-18
Apperantly I didnt!! Thank you very much! It worked!

I'm just confused though because I was under the impression they were installed. Could you kindly elaborate why I needed to install -dev sources?

Thanks!

---

### Post by paultag on 2008-02-18
of course,

When you compile an app, it requires something called a Header. (the .h file)
This .h contains source to a function or method. Now when an app is compiled, the source is not necessary, so it is taken out.

When you have dependency on an app, chances are they implement the function from the source, not the library (lib) or binary (bin), so the compiler needs to link to the header.

Simple lesson, but important when compiling

More Reading:
[http://hepwww.ph.qmul.ac.uk/mcps/compile.html?desc=Compiling+and+Linking+a+C%2B%2B+program&file=compile.html](http://hepwww.ph.qmul.ac.uk/mcps/compile.html?desc=Compiling+and+Linking+a+C%2B%2B+program&file=compile.html)

Cheers,
Tag

---

### Post by mr_tk on 2008-02-18
I really need to refresh my C and C++ knowledge. Thank you much though for your time.

All the best!

---

