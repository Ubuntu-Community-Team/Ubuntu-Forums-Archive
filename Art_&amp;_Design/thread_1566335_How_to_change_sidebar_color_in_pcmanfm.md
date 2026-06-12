---
title: "How to change sidebar color in pcmanfm ?"
date: 2010-09-02
forum: Art &amp; Design
---

### Post by tydell on 2010-09-02
Hi. I was wondering of there anybody at this forum can tell me how to solve this problem:
there is screenshot of nautilus elementary:

[IMG]http://lh3.ggpht.com/__QZICaRXSMs/TAiwQ8dnayI/AAAAAAAAAKM/QCFwfFsCTK8/s640/zrzut_ekranu1.png[/IMG]

The sidebar on the left is different background color than other background area in nautilus. It is mostly white but sidebar is blue
I would like to do the same in pcmanfm file manager, but i don't know how to change sidebar color.
I looked into gtkrc files in elementary theme folder and other .rc files there. The problem is i don't know what gtk element is that sidebar, don't know how to do this.
For nautilus it's for example:
```
style "nautilus-sidebar" {

	text[NORMAL]	= mix (0.3, @sidebar_color, @text_color)

	font_name 	                  	= "Regular"

	GtkTreeView::odd_row_color		= @sidebar_color
	GtkTreeView::even_row_color		= @sidebar_color

      # these make the padding from left window edge a little more sane
	GtkTreeView::horizontal_separator	= 15
      	xthickness				= 8
	ythickness				= 0
}

...

widget_class	"*Nautilus*Places*Sidebar*"	style "nautilus-sidebar"
```
Maybe someone knows what to do, what widget_class is pcmanfm sidebar ?

---

### Post by claudia89 on 2010-10-05
I'm also interestet in changing some PCManFM widgets from within a GTK-theme.
I've tried to simply replace the *Nautilus* -parts in the gtkrc file with *PCManFM* ones, but it didn't work.

Does anybody in this world know how to specify any PCManFM widgets in a gtkrc file? i searched the web for this since the last 4 hours, but i found noting useful :(

thx, claudia

---

### Post by dzon65 on 2010-11-19
Could you post the entire rc?

---

### Post by arzali on 2011-02-25
```
widget_class    "*FmPlacesView*"    style "nautilus-sidebar"
```

---

### Post by LarsKongo on 2011-02-27
I'm interested in the best way to extract the names from applications to apply specific gtk styles for them.

---

### Post by arzali on 2011-02-27
> **LarsKongo said:**
> I'm interested in the best way to extract the names from applications to apply specific gtk styles for them.

Im using gtkparasite.
Its really simple just point and click :)
Here is the home page [http://chipx86.github.com/gtkparasite/](http://chipx86.github.com/gtkparasite/)

---

### Post by LarsKongo on 2011-02-28
Nice, thanks. Works great.
Almost have a PCManFM that somewhat looks like nautilus-elementary now. :D

Too bad that I can't open Nautilus with it though. Still have an annoying button I need to change in the adressbar. (The arrow button to the far left in classic nautilus, not elementary. As you can see in the OP's screen up there, the white button with the black arrow.)

---

### Post by arzali on 2011-02-28
can you share that style when its ready?

also nautilus shouldn't be running when you open it with parasite

---

### Post by blackpit on 2011-06-10
Hello to all. I was looking for this feature too. I managed this on nautilus but i couldn't find anything for pcmanfm. But then i found that the gtk orta theme added colour to the sidebar. So I searched at the theme's files and found what i was looking for. I just added the following to the gtrc file:

style "pcmanfm-sidebar"
{
	ythickness				= 3
	xthickness				= 3

	GtkTreeView::horizontal_separator	= 15
	base[NORMAL]				= shade( 0.999, @bg_color)
}


widget "FmMainWin.*.FmPlacesView" 		style "pcmanfm-sidebar"

You can see the results in the screenshots. I was using Lubuntu 11.04 and the lubuntu-default theme.

---

