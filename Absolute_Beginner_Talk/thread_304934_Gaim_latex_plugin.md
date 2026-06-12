---
title: "Gaim latex plugin"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by olejorgen on 2006-11-22
Hi, I'm trying to build the gaim latex plugin, but I'm just getting errors.

I've installed gaim-dev and libgtk2.0-dev, but Im still getting this:

```

[...]/gaim-latex-0.4$ make
gcc  -fPIC -c LaTeX.c -o LaTeX.o -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DHAVE_CONFIG_H
In file included from LaTeX.c:32:
LaTeX.h:32:27: error: gaim/internal.h: No such file or directory
LaTeX.c:38:1: warning: "MAX" redefined
In file included from /usr/lib/glib-2.0/include/glibconfig.h:9,
                 from /usr/include/glib-2.0/glib/gtypes.h:30,
                 from /usr/include/glib-2.0/glib/galloca.h:30,
                 from /usr/include/glib-2.0/glib.h:30,
                 from /usr/include/gaim/account.h:30,
                 from /usr/include/gaim/conversation.h:136,
                 from LaTeX.h:33,
                 from LaTeX.c:32:
/usr/include/glib-2.0/glib/gmacros.h:167:1: warning: this is the location of the previous definition
LaTeX.c: In function &#8216;analyse&#8217;:
LaTeX.c:423: warning: passing argument 1 of &#8216;g_strdup_printf&#8217; makes pointer from integer without a cast
LaTeX.c: In function &#8216;gaim_latex_write&#8217;:
LaTeX.c:484: error: &#8216;GaimConversation&#8217; has no member named &#8216;log&#8217;
LaTeX.c:485: error: &#8216;GaimConversation&#8217; has no member named &#8216;log&#8217;
LaTeX.c: In function &#8216;message_recv&#8217;:
LaTeX.c:591: error: incompatible type for argument 1 of &#8216;gaim_find_conversation_with_account&#8217;
LaTeX.c:591: warning: passing argument 2 of &#8216;gaim_find_conversation_with_account&#8217; from incompatible pointer type
LaTeX.c:591: error: too few arguments to function &#8216;gaim_find_conversation_with_account&#8217;
LaTeX.c: At top level:
LaTeX.c:662: error: initializer element is not constant
LaTeX.c:662: error: (near initialization for &#8216;info.name&#8217;)
LaTeX.c:663: error: initializer element is not constant
LaTeX.c:663: error: (near initialization for &#8216;info.version&#8217;)
LaTeX.c:665: error: initializer element is not constant
LaTeX.c:665: error: (near initialization for &#8216;info.summary&#8217;)
LaTeX.c:667: error: initializer element is not constant
LaTeX.c:667: error: (near initialization for &#8216;info.description&#8217;)
make: *** [LaTeX.o] Error 1

```

When i look in the content of gaim-dev, internal.h is not there either!?

What's going on?

Thanks (Sorry I miss-posting this first. Realised my misstake 5 sec after I clicked post ^^)

---

### Post by olejorgen on 2006-11-23
hm.. there sure is a lot of activity here... :) Will I be banned for a bump?

---

### Post by olejorgen on 2006-12-01
No one? :(

I guess it has something to do with this? 
[http://lists.alioth.debian.org/pipermail/pkg-ggz-maintainers/2006-October/000169.html](http://lists.alioth.debian.org/pipermail/pkg-ggz-maintainers/2006-October/000169.html)

---

