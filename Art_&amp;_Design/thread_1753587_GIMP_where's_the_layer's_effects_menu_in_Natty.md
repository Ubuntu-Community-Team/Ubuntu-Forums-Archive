---
title: "GIMP: where's the layer's effects menu in Natty?"
date: 2011-05-09
forum: Art &amp; Design
---

### Post by bobzr on 2011-05-09
Hi. I have installed the new Natty and I like it a lot. I also installed GIMP with the popular extension: gimp-plugin-registry. But when I open GIMP, a useful menu has simply disappeared: I used to right-click on any layer, and the very last item of the menu (at the bottom) was: Layers Effects. And I could easily add any stroke, drop shadow, etc. to the layer.
Now this menu has gone. There's a new menu on the top of GIMP called FX-Foundry, where a "Layers Effects" item can be found. But it's different, less options for drop shadow, no "stroke" option, etc.
I'm very disappointed because I used the former menu a lot. I googled and searched in this forum, but I couldn't find anyone complaining about the same problem.
Does anybody knows how to bring back the former "LAYERS EFFECTS" on GIMP?

---

### Post by CreativeReach on 2011-05-09
> **bobzr said:**
> Hi. I have installed the new Natty and I like it a lot. I also installed GIMP with the popular extension: gimp-plugin-registry. But when I open GIMP, a useful menu has simply disappeared: I used to right-click on any layer, and the very last item of the menu (at the bottom) was: Layers Effects. And I could easily add any stroke, drop shadow, etc. to the layer.
Now this menu has gone. There's a new menu on the top of GIMP called FX-Foundry, where a "Layers Effects" item can be found. But it's different, less options for drop shadow, no "stroke" option, etc.
I'm very disappointed because I used the former menu a lot. I googled and searched in this forum, but I couldn't find anyone complaining about the same problem.
Does anybody knows how to bring back the former "LAYERS EFFECTS" on GIMP?

All those effects are done through filters, but i believe the shortcut you are used to is in the 2.7 dev version.

[http://www.iheartubuntu.com/2011/05/gimp-with-single-window-mode.html](http://www.iheartubuntu.com/2011/05/gimp-with-single-window-mode.html)

---

### Post by prokoudine on 2011-05-09
> **bobzr said:**
> Does anybody knows how to bring back the former "LAYERS EFFECTS" on GIMP?

Sure. Remove the package and install everything yourself. E.g. layer effects are [here]("http://registry.gimp.org/node/186"). The page has basic insructions, but if you want to know **everything**, read [this article]("http://libregraphicsworld.org/articles.php?article_id=30")

---

### Post by bobzr on 2011-05-10
> **prokoudine said:**
> Sure. Remove the package and install everything yourself. E.g. layer effects are [here]("http://registry.gimp.org/node/186"). The page has basic insructions, but if you want to know **everything**, read [this article]("http://libregraphicsworld.org/articles.php?article_id=30")

Thanks so much for suggestions & links.

step1: I removed that evil misleading package named: gimp-plugin-registry
step2: I put the file layerfx.py in my plugins folder and made it executable.

Now everything is back to normal and I can enjoy my beloved menu for Layers Effects. Thanks, you made my day!
:D:D:D

---

