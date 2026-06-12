---
title: "A little guidance please?"
date: 2008-05-19
forum: Arch and derivatives
---

### Post by handy on 2008-05-19
I have put this question out in an inappropriate thread before, without success, so I'm going to have another go here in it's own thread:

I am using Openbox & GTK-2 is installed & playing a part in the theme.

Can someone please tell me what file I have to edit to control the colour of the menu's that belong to running application's ?  

E.g. The Firefox menu - including the address & search fields & tab name text in Firefox, Sakura, emelFM2, Leafpad, ePDFview, Mirage... all these & more have horrid snow white menu lettering, help please, make it go away?

I can not control these colours through the ~/.config/openbox/.xml files, nor the ~/.themes/Laza/openbox-3/themerc file, nor the contents of /etc/gtk-2.0/

I have read & reread the /icculus/openbox.org instructions, the Openbox instructions on the Arch Wiki, in the Arch forums I have searched & pawed over posts & threads, I've been through the Gentoo Openbox doc's, I am still unable to find (or recognize) what I need to know. 

So, therefore, I need the help of one who does know?

Many, many thanks in advance to the enlightened one who can offer me a vision of salvation, for thus it is written, that it shall be they who saves my vision!

---

### Post by finferflu on 2008-05-19
You need the gtk-chtheme package. What you are looking for is changing the gtk theme, and not the Openbox theme. Have a look [here](http://wiki.archlinux.org/index.php/Openbox#GTK_Themes) ;)

---

### Post by handy on 2008-05-19
> **finferflu said:**
> You need the gtk-chtheme package. What you are looking for is changing the gtk theme, and not the Openbox theme. Have a look [here](http://wiki.archlinux.org/index.php/Openbox#GTK_Themes) ;)

Sorry finferflu, I should have stated that I am already using  GTK+ 2.0 Change Theme (gtk-chtheme); how do I edit the  menu colours of a theme?

Following is a theme that I am in the process of modifying, nowhere can I get at the application menu's & such (as mentioned in my initial post):

[I]# Laza by lyrae | thrynk.deviantart.com

# Window geometry
padding.width: 2
border.width: 1
window.client.padding.width: 0
window.client.padding.height: 0
window.handle.width: 2

#Menu geometry
menu.border.width: 1
menu.overlap: 0

# Border colors
window.active.border.color: #272521
window.inactive.border.color: #272521
menu.border.color: #272521
window.active.client.color: #272521
window.inactive.client.color: #272521

# Text shadows
window.active.label.text.font: shadow=n
window.inactive.label.text.font: shadow=n
menu.items.font: shadow=n
menu.title.text.font: shadow=n

# Window title justification
window.label.text.justify: center

# Active window
window.active.title.bg: Flat Gradient Vertical
window.active.title.bg.color: #b89c77
window.active.title.bg.colorTo: #917249
window.active.label.bg: Parentrelative
window.active.label.text.color: #754c12

window.active.handle.bg: Flat Gradient Vertical
window.active.handle.bg.color: #b89c77
window.active.handle.bg.colorTo: #b7b0a5

window.active.grip.bg: Flat Gradient Vertical
window.active.grip.bg.color: #b89c77
window.active.grip.bg.colorTo: #b7b0a5

window.active.button.unpressed.bg: Flat Gradient Vertical Border
window.active.button.unpressed.bg.color: #b89c77
window.active.button.unpressed.bg.colorTo: #b7b0a5
window.active.button.unpressed.bg.border.color: #272521
window.active.button.unpressed.image.color: #786e5b

window.active.button.pressed.bg: Flat Gradient Vertical Border
window.active.button.pressed.bg.color: #b89c77
window.active.button.pressed.bg.colorTo: #b7b0a5
window.active.button.pressed.bg.border.color: #272521
window.active.button.pressed.image.color: #786e5b

window.active.button.disabled.bg: Flat Gradient Vertical Border
window.active.button.disabled.bg.color: #b89c77
window.active.button.disabled.bg.colorTo: #b7b0a5
window.active.button.disabled.bg.border.color: #272521
window.active.button.disabled.image.color: #c0c0c0

window.active.button.toggled.bg: Flat Gradient Vertical Border
window.active.button.toggled.bg.color: #b89c77
window.active.button.toggled.bg.colorTo: #b7b0a5
window.active.button.toggled.bg.border.color: #272521
window.active.button.toggled.image.color: #c0c0c0

window.active.button.hover.bg: Flat Gradient Vertical Border
window.active.button.hover.bg.color: #b89c77
window.active.button.hover.bg.colorTo: #b7b0a5
window.active.button.hover.bg.border.color: #272521
window.active.button.hover.image.color: #B7B0A5

# Inactive windows
window.inactive.title.bg: Flat Gradient Vertical
window.inactive.title.bg.color: #b89c77
window.inactive.title.bg.colorTo: #917249

window.inactive.label.bg: Parentrelative
window.inactive.label.text.color: #05690e

window.inactive.handle.bg: Flat Gradient Vertical
window.inactive.handle.bg.color: #a5b8b1
window.inactive.handle.bg.colorTo: #b7b0a5

window.inactive.grip.bg: Flat Gradient Vertical
window.inactive.grip.bg.color: #a5b8b1
window.inactive.grip.bg.colorTo: #b7b0a5

window.inactive.button.unpressed.bg: Flat Gradient Vertical Border
window.inactive.button.unpressed.bg.color: #a5b8b1
window.inactive.button.unpressed.bg.colorTo: #b7b0a5
window.inactive.button.unpressed.bg.border.color: #272521
window.inactive.button.unpressed.image.color: #786e5b

window.inactive.button.pressed.bg: Flat Gradient Vertical Border
window.inactive.button.pressed.bg.color: #a5b8b1
window.inactive.button.pressed.bg.colorTo: #b7b0a5
window.inactive.button.pressed.bg.border.color: #272521
window.inactive.button.pressed.image.color: #786e5b

window.inactive.button.disabled.bg: Flat Gradient Vertical Border
window.inactive.button.disabled.bg.color: #a5b8b1
window.inactive.button.disabled.bg.colorTo: #b7b0a5
window.inactive.button.disabled.bg.border.color: #272521
window.inactive.button.disabled.image.color: #786e5b

window.inactive.button.toggled.bg: Flat Gradient Vertical Border
window.inactive.button.toggled.bg.color: #a5b8b1
window.inactive.button.toggled.bg.colorTo: #b7b0a5
window.inactive.button.toggled.bg.border.color: #272521
window.inactive.button.toggled.image.color: #786e5b

window.inactive.button.hover.bg: Flat Gradient Vertical Border
window.inactive.button.hover.bg.color: #a5b8b1
window.inactive.button.hover.bg.colorTo: #b7b0a5
window.inactive.button.hover.bg.border.color: #272521
window.inactive.button.hover.image.color: #786e5b

# Menus
menu.title.bg: Flat Solid
menu.title.bg.color: #302e29
menu.title.bg.colorTo: #272521
menu.title.text.color: #5A8233
menu.title.text.justify: center

menu.items.bg: Flat Solid
menu.items.bg.color: #272521
menu.items.text.color: #5A8233
menu.items.disabled.text.color: #5A8233

menu.items.active.bg: Flat Gradient Vertical
menu.items.active.bg.color: #302e29
menu.items.active.bg.colorTo: #302e29
menu.items.active.text.color: #9C6518
menu.items.active.disabled.text.color: #c3c3c3

#osd
osd.border.width: 1
osd.border.color:  #272521

osd.bg: flat border vertical gradient
osd.bg.color: #272521
osd.bg.colorTo: #272521
osd.bg.border.color: #786e5b

osd.label.bg: parentrelative

osd.label.text.color: #B7B0A5
[/I]

---

### Post by freduardo on 2008-05-19
I believe that's an openbox theme. 
Changes made to that will only affect openbox's "things" (main menu, window borders...).

In order to change a gtk theme you'll need the gtkrc file of the theme.

---

### Post by chucky chuckaluck on 2008-05-19
> **freduardo said:**
> I believe that's an openbox theme. 
Changes made to that will only affect openbox's "things" (main menu, window borders...).

In order to change a gtk theme you'll need the gtkrc file of the theme.

yup. you'll find the gtkrc file in the theme's directory, which will either be in ~/.themes, or /usr/share/themes. if the latter, you'll need to be in root to edit, or you can copy the theme directory to ~/.themes and edit it as user (now that i think about it, you might have to move it, not just copy it. not sure about that one).

---

### Post by handy on 2008-05-19
> **freduardo said:**
> I believe that's an openbox theme. 
Changes made to that will only affect openbox's "things" (main menu, window borders...).

In order to change a gtk theme you'll need the gtkrc file of the theme.

Thanks, you have opened another door for me.

What I found was that there was no gtkrc file for it, so I stole one from another theme, to modify, but it is not as simple as xml, so I'm stoinked again! :lolflag:

> **chucky chuckaluck said:**
> yup. you'll find the gtkrc file in the theme's directory, which will either be in ~/.themes, or /usr/share/themes. if the latter, you'll need to be in root to edit, or you can copy the theme directory to ~/.themes and edit it as user (now that i think about it, you might have to move it, not just copy it. not sure about that one).

Thanks chucky; when I installed this theme it went into ~/.themes, but as already stated, there was no gtkrc for it, & I have just learned that I don't know how to edit them yet anyway!

---

### Post by chucky chuckaluck on 2008-05-19
> **handy said:**
> Thanks, you have opened another door for me.

What I found was that there was no gtkrc file for it, so I stole one from another theme, to modify, but it is not as simple as xml, so I'm stoinked again! :lolflag:



Thanks chucky; when I installed this theme it went into ~/.themes, but as already stated, there was no gtkrc for it, & I have just learned that I don't know how to edit them yet anyway!

no gtkrc??? what theme is it?

---

### Post by rjmdomingo2003 on 2008-05-19
If you want to learn how to edit gtk themes, check out this guide: [http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

---

### Post by handy on 2008-05-19
> **chucky chuckaluck said:**
> no gtkrc??? what theme is it?

Laza.

***_[http://www.gnome-look.org/content/show.php/Laza+Theme+Pack?content=64953](http://www.gnome-look.org/content/show.php/Laza+Theme+Pack?content=64953)_***

> **rjmdomingo2003 said:**
> If you want to learn how to edit gtk themes, check out this guide: [http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

Thanks for your post, though I found the site on my own; it is where I have been for some hours now.  

I have been slowly identifying which colour is which in the ~/.themes/gtk-2.0/gtkrc file that I stole from another theme called ldc, so that I can convert the colours from floating point to hex, & then easily use agave to modify the colours to suit my taste/needs.  

So, the theme I have at the moment is a modified combination of Laza & ldc. It still has quite a ways to go though.

I tell you what, I'm glad that Arch has a rolling release system in place, there is going to be a lot of hours go into setting Openbox up just so... & I won't feel like reinventing this wheel for quite some time.  

All good educational fun though.

I reckon I'll surely make a backup of all the configuration files & email them to myself & leave them on my ISP's server.

---

### Post by Dr Small on 2008-05-19
Just a hint here, as I can't provide any help. But if you use gcolor2, you can color pick and find what color it is on the gtk and then I would search the file for that hex value.

It might save some time :)

---

### Post by chucky chuckaluck on 2008-05-19
> **handy said:**
> Laza.

the gtkrc file is in there. in fact, there's nothing else in that theme directory. i see laza is a theme pack (which seems to mean, these days, that it's a box inside a box inside another box inside another stupid box and then, you still have to untar it). are you sure you got the gtk theme unpacked? i'm wondering if you only got the openbox theme unpacked.

---

### Post by handy on 2008-05-19
> **Dr Small said:**
> Just a hint here, as I can't provide any help. But if you use gcolor2, you can color pick and find what color it is on the gtk and then I would search the file for that hex value.

It might save some time :)

Thank you good Dr. :-)  I have been using agave to do the same thing.  The time consuming part is working out which part of Openbox's environment the actual line is effecting?

I'll post the file below so you can see what I mean, you'll see that I have duplicated all of the lines pertaining to colour, & commented them all out then I've been going through trial & error to identify the colour after which it is really easy to convert it to hex with agave or GColor2 :

[I]#ldc theme 

style "dark" {
  font = "snap"
 # fg[NORMAL]           = { 0.75, 0.75, 0.68 }
   fg[NORMAL]           = "#BFC3C0"
 # fg[PRELIGHT]         = { 0.85, 0.85, 0.78 }
 # fg[PRELIGHT]         = { 0.85, 0.85, 0.78 }
 # fg[ACTIVE]           = { 0.75, 0.75, 0.68 }
 # fg[ACTIVE]           = { 0.75, 0.75, 0.68 }
 # fg[SELECTED]         = { 0.85, 0.85, 0.78 }
 # fg[SELECTED]         = { 0.85, 0.85, 0.78 }
 # fg[INSENSITIVE]      = { 0.48, 0.48, 0.44 }
 # fg[INSENSITIVE]      = { 0.48, 0.48, 0.44 }
 # bg[NORMAL]           = { 0.40, 0.40, 0.40 }
   bg[NORMAL]           = "#666666"
 # bg[PRELIGHT]         = { 0.35, 0.35, 0.39 }
   bg[PRELIGHT]         = "#BFC3C0"
 # bg[ACTIVE]           = { 0.25, 0.25, 0.25 }
 # bg[ACTIVE]           = { 0.25, 0.25, 0.25 }
 # bg[SELECTED]         = { 0.30, 0.30, 0.34 }
 # bg[SELECTED]         = { 0.30, 0.30, 0.34 }
 # bg[INSENSITIVE]      = { 0.20, 0.20, 0.20 }
 # bg[INSENSITIVE]      = { 0.20, 0.20, 0.20 }
 # base[NORMAL]         = { 0.32, 0.32, 0.32 }
   base[NORMAL]         = "#515151"
 # base[PRELIGHT]       = { 0.12, 0.12, 0.08 }
 # base[PRELIGHT]       = { 0.12, 0.12, 0.08 }
 # base[ACTIVE]         = { 0.35, 0.35, 0.30 }
 # base[ACTIVE]         = { 0.35, 0.35, 0.30 }
 # base[SELECTED]       = { 0.40, 0.40, 0.30 }
   base[SELECTED]       = "#736E2D"
 # base[INSENSITIVE]    = { 0.12, 0.12, 0.08 }
 # base[INSENSITIVE]    = { 0.12, 0.12, 0.08 }
	engine "xeno" {
		
	}	
}

style "shade" {
	engine "xeno" {
		
	}
}

class  "*" style "dark"
widget "*" style "dark"
class "GtkButton"   style "shade"[/I]

---

### Post by lswest on 2008-05-19
i think you may have downloaded the openbox download from the gnome-looks page?  If you choose the first download it provides the gtkrc file.

*EDIT* ah, two more replies in the 10 minutes since i meant to reply to this thread (was distracted) :P oh well, sorry to repeat what was said.

---

### Post by handy on 2008-05-19
> **chucky chuckaluck said:**
> the gtkrc file is in there. in fact, there's nothing else in that theme directory. i see laza is a theme pack (which seems to mean, these days, that it's a box inside a box inside another box inside another stupid box and then, you still have to untar it). are you sure you got the gtk theme unpacked? i'm wondering if you only got the openbox theme unpacked.

I unpacked it all, I have actually downloaded it again from the link that I posted in my previous reply to you & had a look inside & there is no gtkrc file there?

After I deleted the gtk-1 stuff from the ldc gtkrc that related to the xeno engine, I could access the Laza theme via GTK+ 2.0 Theme Changer, due to the fact that I'm using (& in the process of modifying) the ldc gtkrc with the Laza theme! :lolflag:

---

### Post by handy on 2008-05-19
> **chucky chuckaluck said:**
> the gtkrc file is in there. in fact, there's nothing else in that theme directory. i see laza is a theme pack (which seems to mean, these days, that it's a box inside a box inside another box inside another stupid box and then, you still have to untar it). are you sure you got the gtk theme unpacked? i'm wondering if you only got the openbox theme unpacked.

> **lswest said:**
> i think you may have downloaded the openbox download from the gnome-looks page?  If you choose the first download it provides the gtkrc file.

*EDIT* ah, two more replies in the 10 minutes since i meant to reply to this thread (was distracted) :P oh well, sorry to repeat what was said.

Yep, I just did a couple more downloads, & you guys are right, I missed out on the gtk-2 version!

I'll carry on with the theme I'm creating out of ldc & Laza anyway, too late to stop now!

Thanks for pointing it out to me too... :-)

[I]**[Edit:]**  No, I'm not going to continue on with the ldc gtkrc, because the Laza one has it's colours in hex, which makes it so mush quicker & easier to modify with agave or GColor2.

My mistake has at least caused me to learn things I would have otherwise missed at least.[/I] :oops:

---

### Post by chucky chuckaluck on 2008-05-19
why are gtk themes packed so densely these days? it used to be a theme directory tarred. now, it's often a tarball inside a directory, inside another directory inside another tarball.

---

### Post by Dr Small on 2008-05-19
> **chucky chuckaluck said:**
> why are gtk themes packed so densely these days? it used to be a theme directory tarred. now, it's often a tarball inside a directory, inside another directory inside another tarball.
I don't know. That sounds ridiculous...

---

