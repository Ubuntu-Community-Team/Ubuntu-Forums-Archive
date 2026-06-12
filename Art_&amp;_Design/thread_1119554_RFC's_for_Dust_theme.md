---
title: "RFC's for Dust theme"
date: 2009-04-08
forum: Art &amp; Design
---

### Post by gwi on 2009-04-08
I have been using the Dust theme for a few weeks now. I made a little change to it: I reversed the look of the radion button, by changing the following in gtk-2.0/gtkrc:
```
# SZ07: This is added to tell the theme how to color checkmarks and radio items that are not in menus.
style "murrine-radiocheck" = "default"
{
	text[NORMAL]	= @selected_fg_color # Color for selected checks/radio items.
	text[PRELIGHT]	= @selected_fg_color	# Color for selected checks/radio items on prelight.
	engine "murrine"{
	}
}

class "GtkRadioButton"	style:highest "murrine-radiocheck"	# SZ07: Added for the checkmarks/radio
class "GtkCheckButton"	style:highest "murrine-radiocheck"	# SZ07: Added for the checkmarks/radio
```
into the following:
```
# SZ07: This is added to tell the theme how to color checkmarks and radio items that are not in menus.
style "murrine-radio" = "default"
{
	bg[SELECTED]	= @bg_color
	text[NORMAL]	= @selected_bg_color # Color for selected radio items.
	text[PRELIGHT]	= @selected_bg_color	# Color for selected radio items on prelight.
	engine "murrine"{
	}
}

style "murrine-check" = "default"
{
	text[NORMAL]	= @selected_fg_color # Color for selected checks.
	text[PRELIGHT]	= @selected_fg_color	# Color for selected checks on prelight.
	engine "murrine"{
	}
}

class "GtkRadioButton"	style:highest "murrine-radio"	# SZ07: Added for the checkmarks/radio
class "GtkCheckButton"	style:highest "murrine-check"	# SZ07: Added for the checkmarks/radio
```
:confused:This works, but it does not change the looks of the radio button in menu's. How can I change that?

Besides this I would like the item separator in menu's to have better visibility. I tried changing the color in line 282, but that didn't have any effect.
:confused:How can the appearance of the separator line be changed?

And finally: the restore and maximize buttons have the same image, making it very difficult to see the whether a window is really maximized, or just has the same size as the desktop. I would like to have a separate restore button image. Maybe with a small square or rectangle in it?

(Btw: I am using Compiz.)

---

### Post by MadsRH on 2009-04-08
Sorry I can't help you, but I'm also using Dust and this sounds very interesting :cool:  
Could you post a screenshot???

---

### Post by gwi on 2009-06-24
Just try what I did (and described in my first post). Don't forget to make a backup copy of the file first.

That should be better than a screen shot.

---

