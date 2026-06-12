---
title: "How hard is it to tweak themes?"
date: 2005-06-26
forum: Art &amp; Design
---

### Post by carlc on 2005-06-26
How hard is it to tweak themes?

I really like this theme, [industrial-myst version 5.0.0](http://art.gnome.org/themes/gtk2/764). However, I would rather have white entry boxes instead of light blue.

---

### Post by bvc on 2005-06-26
open mainrc line 64 and change
base[NORMAL]    = "#D9E2E8"
to
base[NORMAL]    = "#FFFFFF"

---

### Post by bvc on 2005-06-26
to just change Entry use the entryrc and add it like so
```
style "industrial-entry" = "industrial-main"
{
	base[NORMAL]    = "#FFFFFF"
	#This color of the cursor in entry and text widget in general.

	GtkEntry::cursor_aspect_ratio = 0.2
	
	GtkEntry::cursor_color = "#7b96ac"
	 
	engine "pixmap"
	{
```

and you can see there where to change the cursor color as well, although it is also in the mainrc. For a regular cursor comment them all out.

---

