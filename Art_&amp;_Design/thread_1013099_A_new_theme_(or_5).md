---
title: "A new theme (or 5)"
date: 2008-12-16
forum: Art &amp; Design
---

### Post by cookieofdoom on 2008-12-16
Okay, so I was bored with all the themes out there. I've tried so many of them. Most of the ones I really like are buggy. Dust is probably my favourite theme but I've gotten a bit tired of it lately.

I decided to try designing my own theme in GIMP. [This is what I came up with](http://cookieofdoom.com/images/newgtktheme.png). Now it does look a bit like OS10 to a degree. The gray backround I think is the main reason for that. Most of my friends think it's fairly distinctively Linux, though. The widgets are (somewhat) copied off of the KDE4 Oxygen theme. The window decorations and top menu bit is fairly unique, I think.

Anyway, would anyone be interested in a theme like this? It seems like a fairly big (though fairly plausible) project, from where I sit. I've never really made a GTK theme before, and I've only ever made modifications to them in the past.

If you like the idea, where do you suppose would be a good place to start? I'm fairly certain that pixmap will be needed for parts of it. I'd like to avoid aurora because it's rather non-standard. The new Murrine seems really powerful, but I don't know what all it can do.

Anyway, opinions are welcome... as is any help at all. I think I may try to start by creating an Emerald theme.

---

### Post by lyceum on 2008-12-16
Well, I switched to KDE once 8.10 came out, so I would not use it, but it does look cool. I say make it. I do not think it looks like OS10.

---

### Post by alex.rayu on 2008-12-16
Does not look like OS10. I could not evaluate the theme, it's very immature:

1. General: I do believe you made the mockup in GIMP. What would be better done with vector images and layer styles looks very immture and raw. Design lacks details (could not group layers and the layer window became overcluttered).

2. No text for menus in top panel. Or will it be as gigantic and white as the top right clock text?

3. Window heading "Lord of the rings" type of text is hard to read.

4. Window heading buttons look very poor. Again, thanks to GIMP that does not support vector shapes well enough.

5. General: text look gigantic. You should stick to certain text proportions for window menu and text field text.

6. "Slider thingy" - too narrow.

If you want to learn and grow fast and successful, ditch that GIMP. Install a trial of Photoshop CS2 and learn it. You can't grow well with tools that were not intended to design, but to only edit photos.

I do like the color choice.

---

### Post by cookieofdoom on 2008-12-16
> **alex.rayu said:**
> Does not look like OS10. I could not evaluate the theme, it's very immature:

Well, I'm going to take this one point at a time. I like constructive criticism, although I would consider yours a little on the harsh side.

> 1. General: I do believe you made the mockup in GIMP. What would be better done with vector images and layer styles looks very immture and raw. Design lacks details (could not group layers and the layer window became overcluttered).

You have several good points here. GIMP is not the best tool for the job. This is not the final design, though. I use GIMP to create mockups for stuff like this (though usually for web design). I add more details as I go. The more I work the better it will get, I hope.

> 2. No text for menus in top panel. Or will it be as gigantic and white as the top right clock text?

The reason for no text on the panel was because I didn't think it needed any. I usually switch my menu so that it just has one button to save space and make things less complicated. On my laptop's 1024x768 screen, space like that is valuable.

In regards to the giant clock at the top left, you're right, it's huge. Actually, all the text is. This is again because GIMP isn't the best tool for the job... and also because I don't have 20/20 eyesight. I just started out with size 18 font, and never bothered changing it, because this is just a mockup.

> 3. Window heading "Lord of the rings" type of text is hard to read.

I chose that font only for the window heading. Some people drop window headings all together, so if it's not easy to read, I don't think it's a huge deal. This is probably the most easily customisable thing in a theme, so if you were using it and didn't like it you could change it.

> 4. Window heading buttons look very poor. Again, thanks to GIMP that does not support vector shapes well enough.

Actually this is because of the font.I used an underscore, a greater-than sign, and a letter X to make the buttons. I will rework these a bit before I go to the final design.

> 5. General: text look gigantic. You should stick to certain text proportions for window menu and text field text.[/quote[

I will likely do that next time as it will make the whole thing more realistic.

[quote]6. "Slider thingy" - too narrow.

You have a good point here, too, I think. Assuming you're talking about the part you actually click on to grab and move the slider. To be honest, I don't even know if I can make it that skinny given GTK's limitations.

> If you want to learn and grow fast and successful, ditch that GIMP. Install a trial of Photoshop CS2 and learn it. You can't grow well with tools that were not intended to design, but to only edit photos.

I've actually installed trials of every Photoshop from 7.0 onto CS4. It's a great program to work with. I would say it is better than GIMP in a lot of ways. Designing stuff is just a hobby, though, and I don't have $700 to spend on a hobby.

> I do like the color choice.

Thank you.

Oh, here's my latest real-world attempt. The GTK theme still isn't what I'd like... Let me know what you think, please.

[[img]http://ubuntuforums.org/attachment.php?attachmentid=96665&stc=1&thumb=1&d=1229482160[/img]](http://ubuntuforums.org/attachment.php?attachmentid=96665&d=1229482160)

---

### Post by wecannotbesaved on 2008-12-17
I really like the panel, very clean and elegant.  I'm not as big of a fan of the close/max/min buttons, not sure why, they seem a little out of place with the rest of the theme.  But overall very nice!

---

### Post by alex.rayu on 2008-12-17
Yep it might. Sorry - no harshness intended.

The top panel intended to be empty? Mean it's there just for the clock? See it's a waste of space. OS10 has menus there. Space should not be wasted on good designs, especially on top and bottom of the screen - the few areas where you can stick things that are not changing, like icons and menus.

The window border buttons. Maybe not use font but use vector on them? I was told that Gimp now has vector support?

Slider - yes. GTK limitations - probably so. I guess for UBUNTU, they wan't draw anything new and special antil it's GTK3. GTK2 is waaay to old.

On the last mockup I like the colors choice and windows internals even more. Even if you don't make it into a final theme, such experience is of value.

I thought about drawing and making a theme as wel a few months ago, but I then figured out that what I can do with a theme is very limited. Even if I knew c++ and wanted to write a theme engine like aurora - the GTK2 is too rigid. That is why all themes on Gnome look pretty much the same.

---

### Post by cookieofdoom on 2008-12-17
> **wecannotbesaved said:**
> I really like the panel, very clean and elegant.  I'm not as big of a fan of the close/max/min buttons, not sure why, they seem a little out of place with the rest of the theme.  But overall very nice!

Thank you. If you could elaborate on just what you mean by out of place, that would be great. A couple of my friends have said the same sort of thing, but I'm having trouble finding out just what's wrong with them.

> **alex.rayu said:**
> Yep it might. Sorry - no harshness intended.

The top panel intended to be empty? Mean it's there just for the clock? See it's a waste of space. OS10 has menus there. Space should not be wasted on good designs, especially on top and bottom of the screen - the few areas where you can stick things that are not changing, like icons and menus.

The window border buttons. Maybe not use font but use vector on them? I was told that Gimp now has vector support?

Slider - yes. GTK limitations - probably so. I guess for UBUNTU, they wan't draw anything new and special antil it's GTK3. GTK2 is waaay to old.

On the last mockup I like the colors choice and windows internals even more. Even if you don't make it into a final theme, such experience is of value.

I thought about drawing and making a theme as wel a few months ago, but I then figured out that what I can do with a theme is very limited. Even if I knew c++ and wanted to write a theme engine like aurora - the GTK2 is too rigid. That is why all themes on Gnome look pretty much the same.

The last image (and the one at the end of this post), I should note, is not really a mockup. It's a real theme now... I may not work well, but I do work quick. :p :lolflag:

Anyway, what exactly are you seeing in the window border buttons that says they need to be vectorized? I can do it, but if you can tell me why you think they should be I may be able to do it better.

Your point on the top panel is a good one. Sometimes to save space I put the task manager in the top bar, drop the bottom one all together, and put remove the date from the clock. Since most people don't operate that way, my latest screenshot includes a menu.

I've also started colourising the theme. If I use extremely low saturation and approximately the same lightness, I can just use the default gnome settings to colourise it. I'm trying to match my green walpaper right now, but I'll move onto other colours soon. Of course, grey will still be an option.

[[IMG]http://img396.imageshack.us/img396/9379/greenthemeiu1.th.jpg[/IMG]](http://img396.imageshack.us/my.php?image=greenthemeiu1.jpg)

---

### Post by wecannotbesaved on 2008-12-18
The rest of the theme seems smooth, rounded and clean whereas the buttons look kind of sharp and uneven.  It's the X mainly.  It has a sharp edge on the top right and the forslash is smaller than the other.  I'd make it a simple uniform X.  The minimize button also looks a bit thin, maybe thicken it up a little

---

### Post by xakh on 2008-12-18
Can I just have that one? I like it a lot! You've made a GNOME theme. not a Windows looking theme, not a Mac looking theme, a GNOME theme. I love it!
Edit: that little spike on the X is one of the reasons I like the theme, don't change it, please!

---

### Post by everytimeref on 2008-12-19
I think the problem that people are seeing with the window buttons is partly down to the large radius on the window's corners meaning that the X, which is essentially a square element, struggles to fit.

That said I really like the theme, it gives a nod to the nerd in all of us linux types whilst looking very slick and designery.

I'd describe it as satisfying, and look forward to being able to download it.

and Kudos to you for following this through.

---

### Post by cookieofdoom on 2008-12-20
Alright, well. I've had a couple requests from people to be able to download the theme. Before I put a link up, I want to make a couple of things clear...

This theme isn't complete. It's still got bugs and stuff. It's not (I don't think anyway) going to break your computer, but it might look wonky in some areas. If you see a bug, please report it (or fix it, and send me the new file :P).

To install the emerald theme you'll need to install emerald. Then you'll need to run the emerald-theme-manager and import the emerald them (included in the tar.gz). To get the fonts running you'll need to install the package: ttf-ancient-fonts.

Also: This theme was coded for the Intrepid Ibex version of the Murrine engine. I can't guarantee that it will work anywhere else. It should be a couple simple fixes if it doesn't work, though.

**[SIZE="5"][The New Theme](http://cookieofdoom.com/downloads/themes/newtheme.tar.gz)[/SIZE]**

______________________________________________

On a design note. I forgot that I stink at vectoring. It has nothing to do with software. I've used GIMP, Inkscape, and Photoshop. I stink with all of them. For right now, the X is going to stay as is. If anyone is interested in tweaking it, please feel free. I'll even send you the .XCF file I used to make the theme.

On another note: Here's a screenshot from my laptop. I got the wallpaper from deviantart. I've got the calculator and Nautilus running. The things on the desktop are screenlets.
[B][SIZE="4"]
[Screenshot](http://img518.imageshack.us/img518/4263/laptopthemedl9.png)[/SIZE][/B]

To adjust the colour of the theme to go with your wallpaper, I recommend using a very light colour that is heavily desaturated. It'll make the text easier to read. The colour used there used there is #a8b5c0.

Have fun. If you use this theme, please let me know and leave me some feedback. Also: Feel free to modify the theme as much as you want. If you release, and the theme is close to mine, I'd appreciate being mentioned but it's not necessary.

---

