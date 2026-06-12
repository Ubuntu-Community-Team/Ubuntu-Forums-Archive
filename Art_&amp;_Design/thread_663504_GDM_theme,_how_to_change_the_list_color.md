---
title: "GDM theme, how to change the list color?"
date: 2008-01-10
forum: Art &amp; Design
---

### Post by oni5115 on 2008-01-10
I found a nice image on interface lift the other day and what started as setting up GDM to have a different background has turned into me making an entire theme out it for fun.  The only problem is that it is a dark theme (black and aqua-ish) and I'm trying to figure out how to change the color of the list/faces font.  I can set the background and icon background black, but the the text is also black.  Pretty much just looking for how to set the backgrounds black, and have the fonts be white, aqua, or whatever else.

---

### Post by smartboyathome on 2008-01-10
*points to the gnome themes link in my sig*
Ask if you need any help. :)

---

### Post by oni5115 on 2008-01-11
Thanks for the link, got it mostly working now using:

```

style "default-style"
{
        #  Normal mode
        bg[NORMAL] = "#000000" 		# background color - black
        fg[NORMAL] = "#30c19d" 		# foreground oolor - aqua
	text[NORMAL] = "#30c19d" 	# widget text color - aqua
	base[NORMAL] = "#000000"	# widget base color - black

	# when mouse is hovering over it
        bg[PRELIGHT] = "#00221a" 	# background color - black 00221a
        fg[PRELIGHT] = "#30c19d" 	# foreground oolor - aqua
	text[PRELIGHT] = "#30c19d" 	# widget text color - aqua
	base[PRELIGHT] = "#00221a"	# widget base color - black 001510

	# color when pressed
        bg[ACTIVE] = "#000000" 		# background color - black  151515
        fg[ACTIVE] = "#30c19d" 		# foreground oolor - aqua
	text[ACTIVE] = "#30c19d" 	# widget text color - aqua
	base[ACTIVE] = "#000000"	# widget base color - black

	# disabled
        bg[INSENSITIVE] = "#000000" 	# background color - black
        fg[INSENSITIVE] = "#30c19d" 	# foreground oolor - aqua
	text[INSENSITIVE] = "#30c19d" 	# widget text color - aqua
	base[INSENSITIVE] = "#000000"	# widget base color - black

	# selected or highlighted
        bg[SELECTED] = "#000000" 	# background color - black
        fg[SELECTED] = "#30c19d" 	# foreground oolor - aqua
	text[SELECTED] = "#30c19d" 	# widget text color - aqua
	base[SELECTED] = "#000000"	# widget base color - black
}

class "GtkWidget" style "default-style" priority "highest"

```

The only problem I have noticed so far is that the Sessions button doesn't seem to color properly.  If I click sessions, it brings up a dialog.  The title is the aqua, and the okay/cancel buttons are as well, but the rest of the window is black.  I can see the radio buttons, but not the text.   When I mouse over, the standard gray/black appears.  So the sessions dialog is functional, just not readable.

What confuses me here though is the GTK theme should in theory make that work, and it does indeed work for langauge and actions!  All the other dialogs from things like shutdown and restart are also colored properly.  Sessions seems to be the only one broken.  :confused:

I tried both with and without the priority setting, figuring maybe that had something to do with it, but it didn't seem to matter.  Although, maybe I have the syntax for it wrong?  Either way, I'm confused.

---

### Post by smartboyathome on 2008-01-11
This sounds like a bug to me. I am not that much into GDM theming yet, I would sugegst contacting the gnome mailing list and seeing what the devs say.

---

### Post by oni5115 on 2008-01-12
ran into one more question. on the password field, when I use 
gdmflexiserver --xnest

the background shows up properly in black.  However, when I actually down and restart, the background is gray and the text is the aqua color.

```

<!-- user-pw-entry -->
									<item type="entry" id="user-pw-entry">
										<pos x="5" y="50%" width="300" height="20" anchor="w"/>
										<normal background="#000000" color="#30c19d" font="Bitstream Vera Sans 10" />
									</item>
								</box>
							</item>

```
:

---

