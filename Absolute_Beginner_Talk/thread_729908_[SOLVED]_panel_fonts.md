---
title: "[SOLVED] panel fonts?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-20
How do i change the panel fonts in ubuntu?

thanks in advance

---

### Post by philinux on 2008-03-20
System Prefs Appearance

then fonts tab.

---

### Post by kamitsukai on 2008-03-20
> **philinux said:**
> System Prefs Appearance

then fonts tab.

Ok thanks but which one will change the panel fonts?

---

### Post by spiderbatdad on 2008-03-20
To change panel fonts or font colors, I believe you want to create/copy and modify to suit, a .gtkrc-2.0 file in your home directory. I used to have a good template, but alas no longer. You might search the forum for .gtkrc-2.0 posts and copy one to your home directory.

an example of a .gtkrc-2.0:

gedit .gtkrc-2.0

Insert the following into this file

style &#8220;panel&#8221;
{
# fg[NORMAL] = &#8220;#ffffff&#8221;
# fg[PRELIGHT] = &#8220;#000000&#8243;
# fg[ACTIVE] = &#8220;#ffffff&#8221;
# fg[SELECTED] = &#8220;#000000&#8243;
# fg[INSENSITIVE] = &#8220;#8A857C&#8221;
# bg[NORMAL] = &#8220;#000000&#8243;
# bg[PRELIGHT] = &#8220;#dfdfdf&#8221;
# bg[ACTIVE] = &#8220;#D0D0D0&#8243;
# bg[SELECTED] = &#8220;#D8BB75&#8243;
# bg[INSENSITIVE] = &#8220;#EFEFEF&#8221;
# base[NORMAL] = &#8220;#ffffff&#8221;
# base[PRELIGHT] = &#8220;#EFEFEF&#8221;
# base[ACTIVE] = &#8220;#D0D0D0&#8243;
# base[SELECTED] = &#8220;#DAB566&#8243;
# base[INSENSITIVE] = &#8220;#E8E8E8&#8243;
# text[NORMAL] = &#8220;#161616&#8243;
# text[PRELIGHT] = &#8220;#000000&#8243;
# text[ACTIVE] = &#8220;#000000&#8243;
# text[SELECTED] = &#8220;#ffffff&#8221;
# text[INSENSITIVE] = &#8220;#8A857C&#8221;
}
style "my_color"
{
font_name = "DejaVu Sans 9"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
widget &#8220;*PanelWidget*&#8221; style &#8220;panel&#8221;
widget &#8220;*PanelApplet*&#8221; style &#8220;panel&#8221;
class &#8220;*Panel*&#8221; style &#8220;panel&#8221;
widget_class &#8220;*Mail*&#8221; style &#8220;panel&#8221;
class &#8220;*notif*&#8221; style &#8220;panel&#8221;
class &#8220;*Notif*&#8221; style &#8220;panel&#8221;
class &#8220;*Tray*&#8221; style &#8220;panel&#8221;
class &#8220;*tray*&#8221; style &#8220;panel&#8221;

You can comment or uncomment lines to suit your wants, or change the color values or font, altogether. This one is set to use the above font in white text.
To begin using reboot or run sudo killall gnome-panel.

---

### Post by kamitsukai on 2008-03-20
hmmm forum search doesent find anything on that and google only finds limited things (T_T)

---

### Post by spiderbatdad on 2008-03-20
I believe the above file will get you started. save it as .gtkrc-2.0  (notice the dot. a hidden file in your home directory.) Then you can tinker with it. If you want to disable it temporarily, I would just rename it, and run killall gnome-panel to revert.

---

