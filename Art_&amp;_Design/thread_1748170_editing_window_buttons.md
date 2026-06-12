---
title: "editing window buttons"
date: 2011-05-03
forum: Art &amp; Design
---

### Post by justborn on 2011-05-03
[http://brainstorm.ubuntu.com/idea/27678/ ]("http://brainstorm.ubuntu.com/idea/27678/")

i'm wanting to design a GTK+ theme that complements the above brainstorm idea.Can anyone one please help me with a link to a  tutorial and also recommend a suitable theme editor?

---

### Post by justborn on 2011-05-07
bump!:(

---

### Post by Copper Bezel on 2011-05-07
Technically, it's not the GTK+ theme you want to edit, but the Metacity theme. Depending on the theme, these buttons may or may not be easily editable images. If the theme uses pixmap buttons, you can find them in the Metacity subfolder of the theme's folder. Notice that themes shipped by default are in /usr/share; the minimize buttons for Ambiance would be at /usr/share/themes/Ambiance/metacity-1/ as minimize.png, minmize_focused_normal.png, etc.

I, too, use an arrow for minimize, though it's a down arrow, rather than a left arrow, because I think there are a few reasons that this is still the more intuitive representation; to think of it, perhaps the most sensible would be a right triangle with the 90° angle at the lower left, conveying the idea of "reducing" and the position of the Launcher bar at once.

---

### Post by justborn on 2011-05-20
> **Copper Bezel said:**
> Technically, it's not the GTK+ theme you want to edit, but the Metacity theme. Depending on the theme, these buttons may or may not be easily editable images. If the theme uses pixmap buttons, you can find them in the Metacity subfolder of the theme's folder. Notice that themes shipped by default are in /usr/share; the minimize buttons for Ambiance would be at /usr/share/themes/Ambiance/metacity-1/ as minimize.png, minmize_focused_normal.png, etc.

I, too, use an arrow for minimize, though it's a down arrow, rather than a left arrow, because I think there are a few reasons that this is still the more intuitive representation; to think of it, perhaps the most sensible would be a right triangle with the 90° angle at the lower left, conveying the idea of "reducing" and the position of the Launcher bar at once.

hey,i tried doing this to the dust theme.but now my theme seems to have rendered unusable.

---

### Post by Copper Bezel on 2011-05-22
I'm sorry I never got back to this. I've had some difficulty with Metacity themes doing this, and I'm not really certain what the cause is. I found that editing the image file rather than replacing it helped prevent this. I don't know whether it has to do with indexing or what. However, it seemed to work for me to just select all, float, and rotate left on each of the three image files:

[url=http://dl.dropbox.com/u/17749392/Screenshots/metacity-button.png][img]http://dl.dropbox.com/u/17749392/Screenshots/metacity-button-thumb.png[/img]
[/url]

It's also best to have the theme folder in your home folder while you're working with it (under .themes) to be able to edit and check more efficiently, if you haven't been doing so.

---

### Post by justborn on 2011-05-23
yeah,this is what it'd look like....

---

### Post by justborn on 2011-05-23
> **Copper Bezel said:**
> I'm sorry I never got back to this. I've had some difficulty with Metacity themes doing this, and I'm not really certain what the cause is. I found that editing the image file rather than replacing it helped prevent this. I don't know whether it has to do with indexing or what. However, it seemed to work for me to just select all, float, and rotate left on each of the three image files:

[url=http://dl.dropbox.com/u/17749392/Screenshots/metacity-button.png][img]http://dl.dropbox.com/u/17749392/Screenshots/metacity-button-thumb.png[/img]
[/url]

It's also best to have the theme folder in your home folder while you're working with it (under .themes) to be able to edit and check more efficiently, if you haven't been doing so.


doesn't it look cool and precise?

---

### Post by Copper Bezel on 2011-05-24
It's not bad. It wouldn't make sense for every layout any more than the "_" underscore, but most new themes (including Ambiance) use a more general "-" instead, meant to resemble a minus sign rather than a taskbar item.

To me, the left arrow is slightly misleading or awkward when it appears on the left side of the title bar:

[[img]http://dl.dropbox.com/u/17749392/Screenshots/left-arrow-thumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/left-arrow.png)

Personally, I use a down arrow. Notice that since my dock doesn't fill the full height of the screen, this is a more accurate representation of the direction from the button to the dock for a maximized window.

[[img]http://dl.dropbox.com/u/17749392/Screenshots/down-arrow-thumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/down-arrow.png)

I guess I just don't think of the up and down arrows as actually representing a direction, though; they mean the same thing as the plus and minus signs. I certainly prefer the arrows, particularly because I don't use the maximize button.

Oh, since I didn't include them earlier, [here]("http://dl.dropbox.com/u/17749392/Screenshots/left-min-buttons-for-dust.tar.gz") are the edited left-arrow minimize buttons for Dust.

Edit: See, the trouble is that a left arrow normally means "back" or "previous," which could create confusion to use one meaning "left" literally.

---

