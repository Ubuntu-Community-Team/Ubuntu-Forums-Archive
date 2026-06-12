---
title: "Installing Firefox"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2007-02-20
I'm running Drapper Drake 64-bit edition and I am trying to compile Firefox 2.0. I ran ./configure and it tells me this: ```
checking MOZ_GTK2_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
configure: error: --enable-application=APP is required

```
With the important part being **configure: error: --enable-application=APP is required** (I think.) So I edited my mozconfig file in browser/config/mozconfig so now it reads:
```
# This file specifies the build flags for Firefox.  You can use it by adding:
#  . $topsrcdir/browser/config/mozconfig
# to the top of your mozconfig file.

 . $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-application=browser
ac_add_options --enable-application=APP

```

But it still doesn't work. Please help me.

-Ryan H

---

### Post by r4ik on 2007-02-20
Try,

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Good luck !

---

### Post by aysiu on 2007-02-20
> **r4ik said:**
> Try,

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Good luck !
Won't work for AMD64.

[Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox) will, though.

---

### Post by Ryan H on 2007-02-20
So you can't get plain Firefox 2.0 on Drapper 64?

-Ryan H

---

### Post by aysiu on 2007-02-20
> **Ryan H said:**
> So you can't get plain Firefox 2.0 on Drapper 64?

-Ryan H
No. But you can get plain Firefox 2.0 on Edgy AMD64.

---

### Post by r4ik on 2007-02-20
Thanks for the info i did not know.

---

### Post by Ryan H on 2007-02-20
I've already tried upgrading and it crashed Ubuntu beyond repair. I'll just wait a month for Fiesty Fawn. . .

Thanks for your help.

-Ryan H

---

### Post by aysiu on 2007-02-20
> **Ryan H said:**
> I've already tried upgrading and it crashed Ubuntu beyond repair. I'll just wait a month for Fiesty Fawn. . .

Thanks for your help.

-Ryan H
Don't like Swiftfox?

---

