---
title: "Using the Ubuntu font for personal website"
date: 2012-06-27
forum: Art &amp; Design
---

### Post by d4wntracker on 2012-06-27
Quick question...
Am I allowed to use the Ubuntu font on my personal website?

In other words...is it OK to code my CSS with
```
font-family:"Ubuntu"
```

I like the font :)

---

### Post by nidzo732 on 2012-06-27
It would work for computers that have Ubuntu font installed. You will have to find a way to get Ubuntu font onto computers that don't have it 
(Windows, Mac, other Linux distros...). I'm not sure how it's done. Search for embedded fonts.

---

### Post by d4wntracker on 2012-06-27
> **nidzo732 said:**
> It would work for computers that have Ubuntu font installed. You will have to find a way to get Ubuntu font onto computers that don't have it 
(Windows, Mac, other Linux distros...).

I know about the issue of not having the font locally on a system (...for which I would sent a petition to every OS developer out there to include it in their distros :mrgreen: but that's beside the point)
It's just that for those few using Ubuntu or having the font on their machine it's nice to see the site with that font. For everyone else I have back-up fonts in the CSS.
I just wanted to make sure that by coding it into the site I wouldn't be breaking any licenses or EULA's or whatever rules organizations think of to protect their creations.
I will provide a download link to the Ubuntu Font-Family site so visitors of my site can download and install this better-then-awesome font. :D

---

### Post by nidzo732 on 2012-06-27
The font is free (as in free speech) so you probably can use it as you wish, but even if it wasn't free it shouldn't break any licences, the font is on the user's computer, not on your site. You can find the Ubuntu font licence on [[COLOR="Blue"]this link[/COLOR]]("http://font.ubuntu.com/ufl/") if you have any more doubts.

---

### Post by snowz on 2012-06-27
If you want the font to be displayed on all computers ([COLOR=DarkOrange]** the viewers don't need to have the font installed**[/COLOR] ) put this in the **CSS** file:

```

[COLOR=#a1a100]@font-face {[/COLOR]

         [COLOR=#000000]**font-family**[/COLOR][COLOR=#00AA00]:[/COLOR] font_name[COLOR=#00AA00];[/COLOR]
         src[COLOR=#00AA00]:[/COLOR] [COLOR=#993333]url[/COLOR][COLOR=#00AA00]([/COLOR][COLOR=#ff0000]'font_name.ttf'[/COLOR][COLOR=#00AA00])[/COLOR][COLOR=#00AA00];[/COLOR]
[COLOR=#00AA00]}[/COLOR]


```[COLOR=Black][B]

The font has to be included in the sites folder.[/B][/COLOR]

---

### Post by matiic on 2012-06-29
Try using [Google Webfonts]("http://google.com/webfonts") - you can use them to display fonts on any computer, without requiring them to have the font installed. I don't know how it works, but I do know that it does ;)
If you search there for "Ubuntu", you can find the font and a few variations on it.

---

### Post by donnadon on 2012-07-13
I also use Ubuntu codes. Thanks ;)

---

### Post by hovrashko on 2012-07-13
> **snowz said:**
> If you want the font to be displayed on all computers ([COLOR=DarkOrange]** the viewers don't need to have the font installed**[/COLOR] ) put this in the **CSS** file:

```

[COLOR=#a1a100]@font-face {[/COLOR]

         [COLOR=#000000]**font-family**[/COLOR][COLOR=#00AA00]:[/COLOR] font_name[COLOR=#00AA00];[/COLOR]
         src[COLOR=#00AA00]:[/COLOR] [COLOR=#993333]url[/COLOR][COLOR=#00AA00]([/COLOR][COLOR=#ff0000]'font_name.ttf'[/COLOR][COLOR=#00AA00])[/COLOR][COLOR=#00AA00];[/COLOR]
[COLOR=#00AA00]}[/COLOR]


```[COLOR=Black][B]

The font has to be included in the sites folder.[/B][/COLOR]

will that work for a different font as well?

---

### Post by GreatDanton on 2012-07-13
Of course. Font_name doesn't exists, lol

Regards.

---

