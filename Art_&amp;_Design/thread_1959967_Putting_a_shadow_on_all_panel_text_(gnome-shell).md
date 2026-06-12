---
title: "Putting a shadow on all panel text (gnome-shell)"
date: 2012-04-16
forum: Art &amp; Design
---

### Post by ubiquitin.jf on 2012-04-16
(This question is a hard one to put into words, so please take a look at the attachment and you should see what I mean immediately.)

I've been messing around with my favourite gnome-shell theme (Zukini) to make it play nice with 3.4 and have found that the app label font which appears in the top left looks much nicer than the font used for the clock and my name. This is due to a shadow being drawn on that font and not on the other panel fonts. How do I modify gnome-shell.css to draw shadows on all panel text?

---

### Post by MooseDog on 2012-05-02
search the .css file for 'text-shadow', which is what is typically used.

[http://dochub.io/#css/text-shadow](http://dochub.io/#css/text-shadow)

However, the Gnome implementation of CSS leaves a lot to be desired, I think it's there but am not positive.

---

