---
title: "SVG makes webbrowser crash"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by HMartinho on 2008-04-19
Hi guys and gals;

I'm running hardy with latest updates and when tryin to open an svg file on a webbrowser (tried firefox 3.0b5 and latest epiphany available) the browser crashes. Nautilus displays the svg thumbnails just fine and i can also open them either with inkscape or image viewer. But when I try to open an svg file within a browser, for example from openclipart or even some images from wikipedia, the browser crashs.

Any hints on this?

Thanks in advance.
Cheers.

---

### Post by schiznik on 2008-04-19
do you get any meaningful errors when running the browser via a command line?

---

### Post by HMartinho on 2008-04-19
can you tell me how to do that?
cheers

EDIT:

```
:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x622920: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622920: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622920: NP_GetValue
GCJ PLUGIN: thread 0x622920: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622920: NP_GetValue return
GCJ PLUGIN: thread 0x622920: NP_GetValue
GCJ PLUGIN: thread 0x622920: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622920: NP_GetValue return
/usr/lib/firefox-3.0b5/firefox: symbol lookup error: /usr/lib/xulrunner-1.9b5/libxul.so: undefined symbol: cairo_path_extents

```

---

### Post by Martje_001 on 2008-04-19
Have you tried deleting ~/.mozilla? This may help.

---

