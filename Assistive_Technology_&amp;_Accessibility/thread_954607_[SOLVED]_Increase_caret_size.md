---
title: "[SOLVED] Increase caret size?"
date: 2008-10-21
forum: Assistive Technology &amp; Accessibility
---

### Post by hictio on 2008-10-21
Is there any way (tweaking a config file, for instance) to increase the size -the width, actually- of the text caret cursor?

I know you can increase the size of the whole cursor icon set (it the set allows to do so), and that you can increase or decrease the rate at which the text cursor blinks, but I want to make it a little bigger so it is easier to see.

For instance, on Firefox, I have been able to do it: [Making the caret more visible]("http://forums.mozillazine.org/viewtopic.php?f=38&t=865895"), editing a setting on the 'about: config' page.

TIA

---

### Post by hictio on 2008-10-29
There is no way of doing this?
I found, that, for instance, on gedit, if you switch to "Insert Mode", the caret fattens the way I want it, but I don't like to work on that mode, personally I find it annoying.

TIA

---

### Post by joannah on 2008-10-30
Hictio,

Yes you can make the text caret cursor bigger in Gnome. Editing a few lines in your gtkrc file in your favorite themes directory will make the text cursor larger and wider similar to when the insert key is on. I use the LargePrint themes, so I edited my /usr/share/themes/LargePrint/gtk-2.0/gtkrc file and reapplied the theme. I also changed a few more settings to make things like the scroll bars, and radio buttons larger and easier to see. 

Here is the file with some comments:

```


# Large Print Theme v0.1
# 
# Written by Bill Haneman, based on Standard theme by T. Liebeck, 
# which was in turn based on lots of different gtkrc files but
# primarily the one for the metal theme.
#
# Large-size pixmap icons by tigert.
#
# email: bill.haneman@sun.com

gtk-icon-sizes = "mini-commander-icon=24,24:print-manager=64,64:panel-button=32,32:gtk-dnd=48,48:gtk-menu=32,32:panel-menu=48,48:gtk-large-toolbar=48,48:gtk-small-toolbar=32,32:gtk-button=32,32:gtk-dialog=64,64"

style "default"
{
  GtkWidget::focus-line-pattern = "\10\2"
  GtkWidget::interior_focus = 1
  GtkWidget::focus-padding = 0
  GtkWidget::focus-line-width = 2
# GtkWidget::cursor_aspect_ratio = 0.1

  GtkHSV::focus-line-pattern = "\0"

  # This will make the scroll bar much larger
  # Originaly the width was set to 20
  # and size to 18
  GtkRange::slider_width = 40
  GtkRange::stepper_size = 40

  GtkPaned::handle-size = 20

  # This will adjust the overall color and size of
  # the text cursor
  # Originaly the aspect ratios were set to 0.1
  # You can play this aspect radio value (from .1 to .9) 
  # I like .9 but you might what something different like .7 or .8
  GtkEntry::cursor_color    = { 0.50, 0.00, 0.00 }
  GtkEntry::cursor_aspect_ratio = 0.9

  GtkTextView::cursor_color    = { 0.50, 0.00, 0.00 }
  GtkTextView::cursor_aspect_ratio = 0.9

  EelEditableLabel::cursor_color    = { 0.50, 0.00, 0.00 }
  EelEditableLabel::cursor_aspect_ratio = 0.9

  # This will make check box and radio button
  # selection much bigger
  # Originaly set to 18
  GtkCheckButton::indicator_size = 40
  GtkCheckMenuItem::indicator_size = 18

  # 

  GtkTreeView::expander_size = 20
  GtkExpander::expander-size = 24
  GtkExpander::expander-spacing = 8

  # This will make the expander arrows on the gnome-panel
  # larger
  # Originaly set to 18
  PanelToplevel::arrow-size = 40

}

class "GtkWidget" style "default"


```

The only trouble with setting the aspect ratio to the maximum value is that it is sometimes hard to see what is under the cursor. So I increased the blink rate, by going to System-> Preferences -> Keyboard -> General -> Cursor Blinking.

Hope this helps,
Joannah

Also thanks for the firefox tip :)

---

### Post by hictio on 2008-10-30
Works like a charm!!!!!! 
Thanks a lot!!! :D

I was thinking that it had to be that file, and Googled around that, found this: [The :gtk-cursor-theme-size property](http://library.gnome.org/devel/gtk/2.10/GtkSettings.html#GtkSettings--gtk-cursor-theme-size). But, this turns to be, AFAIK, the size of cursors for the theme, if they are scalable.

---

### Post by hictio on 2008-10-31
A little update on this, in case somebody cares.
Found that Evolution (testing on the plain vanilla version that comes with 8.04 with all updates applied, no time to update to 8.10 yet) does not honor the cursor settings of the gtkrc file.
Well, at least, it does so, but only on the 'To:', the 'CC:' and the 'Subject:' boxes, fields, on the message (where you type it) it doesn't, doesn't matter if you set that as plain text or HTML emails.

---

### Post by notlistening on 2008-11-01
To further add to this topic there is a gui based gnome configuration tool, I appologise as I can not remember the command but i know it exists. If someone knows of this tool could they post it on here. It allows tweaking of a huge amount of setting. Not sure how accessible it is. 

Tom

---

### Post by stevemidgley on 2010-12-27
> **notlistening said:**
> To further add to this topic there is a gui based gnome configuration tool, I appologise as I can not remember the command but i know it exists. If someone knows of this tool could they post it on here. It allows tweaking of a huge amount of setting. Not sure how accessible it is. 

Tom

I think you're referring to the program: gconf-editor

---

### Post by Sef on 2010-12-27
Locked. Necromancy.

---

