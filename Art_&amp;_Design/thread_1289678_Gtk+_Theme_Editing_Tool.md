---
title: "Gtk+ Theme Editing Tool"
date: 2009-10-12
forum: Art &amp; Design
---

### Post by days_of_ruin on 2009-10-12
I know a lot of theme designers hang out here, and I figured this might be of interest to them: [The Widget Laboratory]("http://blog.mahboy.com/archives/174") 

[IMG]http://blog.mahboy.com/wp-content/uploads/screenshot_039.png[/IMG]

And no this is not the same as The Widget Factory. Hit the link above to read more about it.

---

### Post by Incendia on 2009-10-12
Thanks. I will have a play tomorrow after I've slept. :]

---

### Post by UbuntuNerd on 2009-10-12
i'll check it out :)

---

### Post by Merk42 on 2009-10-12
Well I gues Balanzan uses something different as using it doesn't allow TWL to open,
```
starting viewer process
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 346, in <module>
    main()
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 339, in main
    object = Preview(session_bus, '/Preview')
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 66, in __init__
    meta_theme = metacity.theme_load(self.theme_name)
glib.GError: Failed to find a valid file for theme balanzan

Could not connect to dbus server, retrying...
starting viewer process
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 346, in <module>
    main()
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 339, in main
    object = Preview(session_bus, '/Preview')
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 66, in __init__
    meta_theme = metacity.theme_load(self.theme_name)
glib.GError: Failed to find a valid file for theme balanzan

Could not connect to dbus server, retrying...
starting viewer process
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 346, in <module>
    main()
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 339, in main
    object = Preview(session_bus, '/Preview')
  File "/usr/lib/python2.6/dist-packages/twl/preview.py", line 66, in __init__
    meta_theme = metacity.theme_load(self.theme_name)
glib.GError: Failed to find a valid file for theme balanzan

Could not connect to dbus server, retrying...

```

I also find it funny the screenshots show Dust, which if used, makes the icon for TWL almost impossible to seee

---

### Post by days_of_ruin on 2009-10-13
> **Merk42 said:**
> Well I gues Balanzan uses something different as using it doesn't allow TWL to open,


I also find it funny the screenshots show Dust, which if used, makes the icon for TWL almost impossible to seee

This isn't a problem with Balanzan, its a silly bug in twl.Thanks for reporting this. I have fixed it and will be updating the ppa and the downloads on the download page.



I need a new icon for it anyway.:lolflag:

---

### Post by days_of_ruin on 2009-10-13
Ok, I fixed that bug.

---

### Post by vinutux on 2009-10-13
mmm................ :lolflag:

---

### Post by days_of_ruin on 2009-10-13
> **vinutux said:**
> mmm................ :lolflag:

:confused:

---

### Post by VCoolio on 2009-10-13
Nice, it does have some additional features compared to the widget factory. Main thing though is I can mess with my themes and hit the refresh button there to see the results too. Old habits die hard.
TWL has also the metacity theme of course, but not the prelight / hover effects on the buttons, which would be nice although it's not a metacity editing tool (yet?). 
The menu feature to open the theme folder is very useful, but where is the file that defines what command to use for that (it doesn't work for me, but since I'm using e17 that is quite possible; the folderview screenlet has the same problem, I hacked that too). 
The glade thing is beyond my league; is there a place to find examples?

---

### Post by days_of_ruin on 2009-10-13
> **VCoolio said:**
> Nice, it does have some additional features compared to the widget factory. Main thing though is I can mess with my themes and hit the refresh button there to see the results too. Old habits die hard.
TWL has also the metacity theme of course, but not the prelight / hover effects on the buttons, which would be nice although it's not a metacity editing tool (yet?).

Unfortunately, the library that I am using for the preview doesn't have that feature. And TWL is not primarily a metacity editing tool, although it does monitor the metacity theme too.
> 
The menu feature to open the theme folder is very useful, but where is the file that defines what command to use for that (it doesn't work for me, but since I'm using e17 that is quite possible; the folderview screenlet has the same problem, I hacked that too).

The command is "xdg-open" which is a freedesktop.org command, I guess e17 isn't a freedesktop.org compliant DE. I'll probably add an "Edit -> Copy Filename" option to the next version.
> 
The glade thing is beyond my league; is there a place to find examples?

I don't think so, but its not very hard to create your own.

---

### Post by VCoolio on 2009-10-14
> **days_of_ruin said:**
> 
The command is "xdg-open" which is a freedesktop.org command, I guess e17 isn't a freedesktop.org compliant DE. I'll probably add an "Edit -> Copy Filename" option to the next version.


I've investigated a little and it seems and xdg-open bug. E17 does make an effort to be as freedesktop.org compliant as possible if I'm not mistaken. Rumor states it's fixed in Karmic, so we'll wait 15 days. In the meantime, could you still point me to the file with the code? I can change it to open with thunar.

Edit: found it! With the help of aptsh listfiles I found the file /usr/share/pyshared/twl/main.py, changed xdg-open in line 502 to thunar and it works.
Also I noticed the icon is invisible on a dark panel. Nothing serious, but a white border around the W would suffice.

---

