---
title: "How to change Leafpads background color"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by housekid on 2007-10-16
I downloaded Leafpad to give it a try. I am using Mepis 6.5.
Here is a FAQ from Leafpads website on changing the background color:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Leafpad website: [http://tarot.freeshell.org/leafpad/](http://tarot.freeshell.org/leafpad/)
FAQ
How do I change background color?
Check your .gtkrc-2.0 (or .gtkrc-2.0.mine) in home folder and modify properly.

example:
style "default"
{
	GtkTextView::cursor_color	= "#ffffff"
	
	base[NORMAL]	= "#000000"
	base[ACTIVE]	= "#000080"
	base[SELECTED]	= "#808080"
	text[NORMAL]	= "#c0c0c0"
	text[ACTIVE]	= "#c0c0c0"
	text[SELECTED]	= "#000000"
}
class "GtkTextView" style "default"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I have been unable to find such a file as these (.gtkrc-2.0 (or .gtkrc-2.0.mine)
to make the changes.
Could someone that knows about these things Please tell me how to change the
background color? I have searched every form that has Ubuntu/Mepis postings 
that I can Google up.

---

### Post by kerry_s on 2007-10-16
" .gtkrc-2.0 " is a file you create.

press alt+f2 type > **leafpad ~/.gtkrc-2.0**

then just put your settings.
[B]
style "default"
{
GtkTextView::cursor_color = "#ffffff"

base[NORMAL] = "#000000"
base[ACTIVE] = "#000080"
base[SELECTED] = "#808080"
text[NORMAL] = "#c0c0c0"
text[ACTIVE] = "#c0c0c0"
text[SELECTED] = "#000000"
}
class "GtkTextView" style "default"
[/B]
save it and you should be good to go.

---

### Post by housekid on 2007-10-17
Thank u kerry_s, now I'm changing colors!

---

