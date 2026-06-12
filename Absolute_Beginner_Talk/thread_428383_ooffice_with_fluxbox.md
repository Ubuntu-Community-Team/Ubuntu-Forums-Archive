---
title: "ooffice with fluxbox"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by XProgrammer on 2007-04-30
Hi All,

I'm running feisty fawn (7.04) with fluxbox. I'm facing a problem in ooffice. When I run ooimpress, i couldnt see any checkbox. It doesn't shows up checkbox anywhere. Even in the Options, i couldnt see any drawing objects. It only shows texts.

Any idea waht is the problem ?.

Thanks,
Regards,
XProgrammer.

---

### Post by kerry_s on 2007-04-30
Can you post a screen shot? (sudo apt-get install scrot) (in terminal> scrot -sb %T.jpg < and click on impress.)

Mine looks like this->

---

### Post by XProgrammer on 2007-05-01
Hi Kerry,

Thanks for your reply.

It seems to issue witht GTK. I'm was getting GTK warnings when i run ooimpress.

(process:14157): Gdk-CRITICAL **: gdk_screen_get_font_options: 
_SCREEN (screen)' failed

(process:14157): GLib-GObject-CRITICAL **: gtype.c:2242: initia
n failed, use IA__g_type_init() prior to this function

(process:14157): Gdk-CRITICAL **: gdk_screen_get_font_options: 
_SCREEN (screen)' failed

(process:14157): GLib-GObject-CRITICAL **: gtype.c:2242: initia
n failed, use IA__g_type_init() prior to this function

(process:14157): Gdk-CRITICAL **: gdk_screen_get_font_options: 
_SCREEN (screen)' failed

-----


I did setting environment variable to Gnome via OOO_FORCE_DESKTOP="gnome".

It worked fine.

I've attached the screenshot.

Thanks,
XProgrammer.

---

