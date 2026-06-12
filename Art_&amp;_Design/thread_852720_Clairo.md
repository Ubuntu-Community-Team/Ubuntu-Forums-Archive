---
title: "Clairo"
date: 2008-07-07
forum: Art &amp; Design
---

### Post by dabugas on 2008-07-07
I've been working on a series of themes these last few months that have been getting increasingly darker and less shiny but always maintaining good contrast.

These days I've gotten round to work on a proper dark theme based on clearlooks (and a pinch of aurora, which sadly introduces its own inconsistencies) and the colours from "Cairo style for GNOME", itself derived from the (possibly vaporware) Cairo Desktop for Vista. (I never liked the grey/black of most dark themes.) The metacity is a slight modification of "Blended".

Currently, the most reliable dark theme for GTK+ is "LUX". But it cheats in the sense that the BASE colour is actually lighter than the BG, so it can use black TEXT. A "proper" dark theme should have a darker BASE than the BG. I was wondering how much is fixable within the bounds of a "proper" dark theme.

Clairo, as the theme is called, works tolerably well with most applications, including some annoying ones like OpenOffice. (I have made sure, for example, that the insensitive menu options don't go all green.)

It would be great if some folks could give this theme a spin and point out bugs and, even better, fixes. Ideally, a bunch of generic fixes for dark themes will emerge.

At the moment I'm aware that:
	* Pidgin misbehaves.
	* Firefox 3 is fine, except for certain websites with white forms (e.g., amazon, last.fm). I assume a userContent.css is required here, but my feeble attempts have proven unsuccessful.
	* The panel menu is dodgy -- I believe this can be fixed easily, but as I don't use it myself, I haven't bothered.
	
Words of warning: I am using Gutsy with the new, Hardy-era, clearlooks, aurora 1.4, OpenOffice 2.4, Firefox 3. Non-GTK apps, such as Azureus, are not a priority. I think, ultimately, dark themes may be more trouble than they are worth :)

---

### Post by smartboyathome on 2008-07-08
Cairo Desktop isn't vaporware. Also, this theme is too dark for me, but still looks very nice.

---

### Post by exploder on 2008-07-08
The theme looks very good to me. Keep up the fine work!

---

### Post by lyceum on 2008-07-08
The time to load bars could be better, I do not like the gray/black stripes. Also, the black should be more black and less gray. Otherwise, it looks good.

---

### Post by dabugas on 2008-07-08
> **smartboyathome said:**
> Cairo Desktop isn't vaporware.

That is why I said possibly :) In any case, I have no stake in XP/Vista themes. I was merely clarifying my sources -- i.e., that both I and kimmik (author of "Cairo style for GNOME") worked off a couple of screenshots. I also meant to imply that this is not meant to be a port of any sort.

> **exploder said:**
> The theme looks very good to me. Keep up the fine work!

Thanks!

> **lyceum said:**
> The time to load bars could be better, I do not like the gray/black stripes. Also, the black should be more black and less gray. Otherwise, it looks good.

It took me awhile to see what you mean here. If I've understood you correctly, you're saying that the background of the progress bars should be darker, more like the combo box entry, for example. I happen not to agree with you, but this is a matter of preference. Even if I did agree there is a hitch: the background color of the progress bars should be the same as the scale widget (the sliders). Sadly, there is a limitation in the clearlooks engine which forbids you to colour the background of the scales! It's automatically 90% darker than the normal background. So, this stays as it is.

Thanks for the positive comments y'all.

/awaits further comments, even some (gasp!) bugfixes.

---

### Post by lyceum on 2008-07-09
> **dabugas said:**
> It took me awhile to see what you mean here. If I've understood you correctly, you're saying that the background of the progress bars should be darker, more like the combo box entry, for example. I happen not to agree with you, but this is a matter of preference. Even if I did agree there is a hitch: the background color of the progress bars should be the same as the scale widget (the sliders). Sadly, there is a limitation in the clearlooks engine which forbids you to colour the background of the scales! It's automatically 90% darker than the normal background. So, this stays as it is.

Not the background to the bar, but the bar itself, the part the gets bigger as the computer gets something done. But you are right, it is personal preference.

---

### Post by geoken on 2008-07-09
I can identify with your issues. I never actually made a dark theme, but I made a theme that used dark gray for the active/prelight state and switched the text to white so it was readable when the widgets where in that dark state. I came across so many apps that would use some weird combinations of active/prelight/normal states for there widgets. For example, Deluge's progress bars.

---

### Post by dabugas on 2008-07-09
> **lyceum said:**
> Not the background to the bar, but the bar itself, the part the gets bigger as the computer gets something done. But you are right, it is personal preference.

OK, I see. Sorry for misunderstanding.

I went through all sorts of prototypes before settling on the darkish blue for menu/lists (@selected_bg_color) and the pale blue for highlights, tooltips, progress bars, and sliders (@tooltip_bg_color). If you want to change the later, all you have to do is edit the colour, either from the GNOME Appearance Preferences or by editing the gtkrc directly.

> **geoken said:**
> I came across so many apps that would use some weird combinations of active/prelight/normal states for there widgets. For example, Deluge's progress bars.

Deluge bugs me too. I've switched the list selection to use the aurora engine, so that it'll be a nice gradient instead of the more flat clearlooks. Of course, this also themes the progress bars in Deluge. It's a slight thing, but annoying if you're a pedant like me.

Apart from using this little bit of aurora, though, I'm not trying to do anything remarkably strange. 99.9% of the problems I'm having have to do with entry forms, text boxes, and the like. Where I get white on white (some pages in firefox) or black on black (pidgin). Renaming in nautilus is dodgy as well. :(

---

### Post by Xfcn on 2008-07-09
This is very fine work, and a good effort.

---

### Post by Sand &amp; Mercury on 2008-07-10
Absolutely fantastic work!

---

### Post by lyceum on 2008-07-10
> **dabugas said:**
> OK, I see. Sorry for misunderstanding.

I went through all sorts of prototypes before settling on the darkish blue for menu/lists (@selected_bg_color) and the pale blue for highlights, tooltips, progress bars, and sliders (@tooltip_bg_color). If you want to change the later, all you have to do is edit the colour, either from the GNOME Appearance Preferences or by editing the gtkrc directly.

That is cool, I did not know you could do that, thanks for the tip!

:)

---

