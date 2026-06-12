---
title: "Clearlooks question"
date: 2005-03-13
forum: Art &amp; Design
---

### Post by paul.hendrick on 2005-03-13
I'm using the clearlooks engine, with the indubstrial theme. I'd like to know how i can make some small mods to it(never done engine mods before).
I'd like the top panel(original) to look like the mod below it.

[img]http://software.xkopex.com/cl.png[/img]

as you can see there's a small 1pixel boarder around each of the tasks in the task list, and i think it looks better.

---

### Post by psychic on 2005-03-13
i like it ;)

---

### Post by bvc on 2005-03-13
You'd have to edit the source. This is not something that can be done in the gtkrc.
[http://sourceforge.net/mailarchive/forum.php?thread_id=6761844&forum_id=44090](http://sourceforge.net/mailarchive/forum.php?thread_id=6761844&forum_id=44090)
> * Regarding the gnome-panel buttons,
 This bugs me as well. Having buttons stacked against eachother like that 
 looks bad. In fact, I doubt that the gnome HIG says it"s ok to do that. 
 So I wonder, why the hell does gnome panel do that in the first place? I 
 could create paddings and margins for the buttons, but why would I do 
 that if the real problem is not clearlooks but the panel itself. If 
 someone would take the time to add a 1px spacing to the gnome-panel, it 
 would look good on all themes.
 
 Even if I added the paddings, the spacing between buttons would become 
 2px and not 1px. The reason is because when I add a padding to only one 
 side of the button (bottom+right, for example) the text won"t be 
 centered anymore. So I"d have to add it to all borders and then increase 
 the default buttons size (else it would look smaller than default). To 
 me this just screams "UGLY HACK!". Instead, I trust on the gnome folks 
 to fix their software, unless I can be convinced that it"s really a 
 theme bug.

---

