---
title: "Help me with my themeing ."
date: 2005-07-11
forum: Art &amp; Design
---

### Post by bored2k on 2005-07-11
I don't much about customizing themes, so are my problems:

Here's what I use:
- **Controls:** I use the Gperfection2 color scheme gnome-look.org/content/show.php?content=23563.

- **Window borders:** Clearbox-out
[http://gnome-look.org/content/show.php?content=25060](http://gnome-look.org/content/show.php?content=25060)

- **Icons: **Suede
[http://gnome-look.org/content/show.php?content=13430](http://gnome-look.org/content/show.php?content=13430)


Here are my *two*..er.. okay **four** problems:

1) If you click on Clearbox's screenshot, you will see the titles are aligned to the left but I want them centered. What would I have to change in the "metacity-theme-1.xml"  :neutral: ?

2) The Suede icons are light brown, wich don't fit with GPerfection2 as good as I'd like them. How would I change the icon's colors to the appropiate dark-brownish one ?

3) I kind of want to mix the Suede icons with the GP2 ones (I *love* Suede mimetypes. I could have simply started copying/pasting them, but Suede has one single scalable folder with .SVGs while GP2 has a gazillion folders in .PNG. If possible, how would I do this ? 

4) Suede uses the default nautilus control icons, but I want the ones from GP2 so they fit my Firefox and overall themeing. How, oh how ?


[CENTER]Here's a screenshot showing most of my "problems" (Suede icons are too light but lovely, control icons are default, title is aligned to the left) :-(.
[IMG]http://img339.imageshack.us/img339/6690/screenshotrebfilebrowser7ar.png[/IMG] 


**Any** help would be deeply appreciated :D ![/CENTER]

---

### Post by bvc on 2005-07-21
clearbox-out
```
<draw_ops name="title_focused">
  <include name="bg_topbar"/>
  <!-- <title color="gtk:fg[SELECTED]" x="4" y="((height-title_height)/2) `max` 0"/> -->
  <title color="gtk:fg[SELECTED]" x="(width - title_width) / 2 + 1" y="(height - title_height) / 2 + 1"/>
</draw_ops>

<draw_ops name="title_unfocused">
  <include name="bg_topbar"/>
  <!-- <title color="shade/gtk:bg[SELECTED]/1.4" x="4" y="((height-title_height)/2) `max` 0"/> -->
  <title color="shade/gtk:bg[SELECTED]/1.4" x="(width - title_width) / 2 + 1" y="(height - title_height) / 2 + 1"/>
</draw_ops>
```

---

