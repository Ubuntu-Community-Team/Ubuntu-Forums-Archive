---
title: "Editing themes/icons"
date: 2010-08-07
forum: Art &amp; Design
---

### Post by Peter7K on 2010-08-07
Hello.  There has been something bothering me for a while, and downloading the [Equinox]("http://ubuntu-art.org/content/show.php?content=121881&forumpage=7&PHPSESSID=48038b2c131fea20a8cbf805bbced0c6") theme finally inspired me to confront these issues.  

Essentially, I use [Clearlooks OSX]("http://gnome-look.org/content/show.php/ClearlooksOSX?content=69487").  Now these icons are great and beautiful for my dock among other things, however they don't go well with the awesome monochrome icons on the gnome-panel.  When I went in to attempt to replace them with some of the default monochrome icons, I couldn't find them.  They weren't located in the usual /usr/share/icon with all of the others.  Is there a place where installed icon packs reside on the system?  It's very strange.

Second, I would like to have some transparency on the gnome-panel.  Now, this works great/flawlessly in some themes, like one of the defaults called "Dust".  You can, right click -> Background -> Solid Color and move the transparency slider.  (This is also stupid, I think the transparency slider should work regardless of whether it's a system color or the theme color.)  So in some themes, the whole panel turns transparent, however, in many others, only the parts of the panel that do not have things on it turns transparent, and the rest stays the system color.  I want to find a way to go in and edit the system color to add transparency, or fix this in the bugged theme, etc.  Before now, I was making do by using a customized theme utilizing the Dust Window Rules, mixed with another theme.  This doesn't work well enough with my new theme unfortunately.  

So thank you for your time, I hope people with theming experience can understand what I'm looking for!

---

### Post by miesogeno on 2010-08-08
hi


for your first question, just open nautilus in your home folder and press ctrl+H, to unhide all files. then your icon theme should be instaled in ".icons" folder (~/.icons) (the dot(.) is what hides it).



about the panel, I hated that too when i first started playing with themes, now i just tweak a little in the themes gtkrc file (that should be in ~/.themes, same procedure as above, unless its a default theme and that would be in /usr/share/themes)

example with the new ambiance refined theme, just look for this string:[PHP]style "panel" = "dark"
{
	xthickness = 0
	ythickness = 0

	bg_pixmap[NORMAL] = "panel_bg.png"
        
	engine "murrine" 
	{
		border_colors = {@fg_color, @fg_color}
		border_shades = { 1.4, 1.2 }
		contrast = 1.0   				# 0.8 for less contrast, more than 1.0 for more contrast on borders
		glow_shade = 1.2  				# sets glow amount for buttons or widgets
		lightborder_shade = 1.4  			# sets lightborder amount for buttons or widgets
		lightborderstyle = 1     			# 0 = lightborder on top side, 1 = lightborder on all sides
	}
}
[/PHP]

just erase this line:	bg_pixmap[NORMAL] = "panel_bg.png"
and then do what you usually do, setting the gnome-panel to "solid color" and add transparancy.

notice i'm a bit newbie yet, i just tryed that out and it worked, so if you want to, maybe you can edit some other lines just to try and understand that theme (thats what i'm doing right now!) just be sure to backup the original file before editing.



hope this helps.

---

### Post by Peter7K on 2010-08-09
Thanks!  Worked like a charm (after a couple of hours of fussing with the icons, I have most of them monochrome!  Panel works too!)

---

