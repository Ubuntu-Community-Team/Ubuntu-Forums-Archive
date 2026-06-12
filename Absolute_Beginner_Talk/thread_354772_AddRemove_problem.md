---
title: "Add/Remove problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-02-06
Some thing odd happened to my Add/Remove programs application, when I click on it all it does is pop up a window to configure the screen resolution, I have Automatix installed would this affect it? or am I totally misunderstanding how it works.
TIA

Mick

---

### Post by nhandler on 2007-02-06
Chances are the command for it got messes up. In the mean time, you can use apt-get, aptitude, or synaptic to manage your programs.

---

### Post by mcduck on 2007-02-07
What happens if you run 'gnome-app-install' in a terminal?

---

### Post by MickS on 2007-02-07
Thanks for your reply.

When I run that command it opens Add/Remove and looks good to go, when I close it and go back to the terminal I find this

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files)

** (gnome-app-install:5375): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:5375): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5375): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5375): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5375): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

All looks a bit scary to me, can I clean this stuff out?

TIA

Mick

---

### Post by mcduck on 2007-02-07
It gives some errors on my machine too, but as long as it's working I wouldn't care about those.

Anyway, if that command's working you should open the Menu Editor (Right-click on the menu & select 'Edit Menus')and make sure that the Add/Remove is pointing to gnome-app-install.

---

### Post by MickS on 2007-02-07
I have just tried that and Add/Remove doesn't appear in the list, although it does appear when I click on Applications:confused: 
Thanks so far.

Mick

---

### Post by SunnyRabbiera on 2007-02-07
well it is the dsame software.
worst comes to worst use the terminal

---

### Post by MickS on 2007-02-07
Ha Ha, sorted. More or less followed mcduck's instructions, it's what mcduck said, just a bit more involved at least for some one new to this, I shall know next time, thanks for your help I would never have found it otherwise.

Mick

---

