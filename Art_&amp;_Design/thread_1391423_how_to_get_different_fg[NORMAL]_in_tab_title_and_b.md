---
title: "how to get different fg[NORMAL] in tab title and body?"
date: 2010-01-26
forum: Art &amp; Design
---

### Post by VCoolio on 2010-01-26
Example: nautilus edit > preferences window; the name of the tabs, where you click them, I want white (on a black background, which I have); the text of the tabs themselves, the stuff you read, I want just black. How to achieve that? 

I did it for GtkNotebook, but nautilus uses just Notebook widget. It works for example with thunar or midori if I do:
widget_class "*.GtkNotebook.GtkLabel*" style "<a style with fg[NORMAL] = "white">"
and then fix the contents with:
widget_class "*Notebook*Frame*Label*" style "<a style with fg[NORMAL] = "black">"

But with nautilus (and gedit; there will be more I guess) this line does both tab name and content and I can't subdivide it seems:
widget_class "*Notebook.*Label*" style "<a style with fg[NORMAL] = "white">"

That fixes the tab names; now what about the contents? There is no frame there to specify for.

---

### Post by VCoolio on 2010-01-28
Sort of solved. Use HBox to specify for the tabs, then VBox for contents. But I'm unsure if that goes for vertical tabs too and if contents are always put on a VBox. Seems reasonable though and it works. Result in my theme [here]("http://gnome-look.org/content/show.php?content=119286").

---

