---
title: "Modify gnome theme"
date: 2007-01-11
forum: Art &amp; Design
---

### Post by Arcet on 2007-01-11
Hi, i downloaded a custom gnome GTK theme from art.gnome.org.

I would like to change the image used for certain applets (see attached image)

This theme doesn't specify the image to use so the default image is used. Problem is I don't know where to look for this file.

Where can i find this file, or how do i specify a different one in my theme??

Cheers

---

### Post by jem7v on 2007-01-11
Let's pretend my original post was never here, because the one following it seems to be the answer to what you were actually asking.

---

### Post by bvc on 2007-01-11
the handle?

Put the following either in the themes gtkrc (image in the gtk-2.0 directory) or .gtkrc-2.0 in your home dir (image in your home dir). If the gtkrc-2.0 file is not there in your home dir, create it.
```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

---

### Post by Arcet on 2007-01-12
Problem solved, thx. It did't work right away, i had to do:

sudo apt-get install gtk2-engines-pixbuf

Thx.

---

