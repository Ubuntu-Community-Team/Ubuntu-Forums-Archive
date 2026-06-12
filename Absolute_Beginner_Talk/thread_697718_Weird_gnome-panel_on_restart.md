---
title: "Weird gnome-panel on restart"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by RottenBananas on 2008-02-15
Hey guys,
Gnome panel shows up in the middle of the screen after a restart. I have expand unchecked and it sits on the bottom normally, which works fine...but after restarting my computer it looks like this:

How can i fix it?

thanks
-Bananas

---

### Post by y-lee on 2008-02-15
That is a strange problem. Not sure but one thing you could try is

```
gconf-editor
```

now navigate to** /apps/panel/toplevels/**

In here i have an entry called **bottom_panel_screen0** and it seemingly corresponds to the data describing my bottom panels location and preferences. Try changing the preferences for the panel here, since yours shows up in the middle of the screen see if **y_centered **is checked and check the value given for ** y **and see if it seems reasonable. 

I'm running dapper so this information may vary a bit for your system  and if so look thru all the stuff in ** /apps/panel/** found in gconf-editor and try to find the  panel that is not acting  right and change the settings.

NOTE: this is a semi-educated guess :lolflag:

---

### Post by RottenBananas on 2008-02-16
Hey thanks alot for the reply,
   so it seems that the config editor is similar to regedit in windows?

Your guess worked, i went into apps/panel/toplevel/top_panel_screen0 and changed the y to 800 and now its sits on the bottom just right.:)

Thanks!

---

### Post by y-lee on 2008-02-16
> **RottenBananas said:**
> Hey thanks alot for the reply,
   so it seems that the config editor is similar to regedit in windows?

Your guess worked, i went into apps/panel/toplevel/top_panel_screen0 and changed the y to 800 and now its sits on the bottom just right.:)

Thanks!


Yes in many ways the gconfig editor is like regedit in windows, it allows you to tweak and adjust many of the default gnome settings without messing with system files.  Since I'm the kind of person that likes tweaking his system and changing things around often I have it in my menu under **System Tools**. I'm not sure if I put it there or it was there by default. You can look and if it is not there open **Alacarte Menu Editor** (under Accessories) and see if it is just unchecked or add it if not if ya wish :)

That was the first place I looked when i read your problem actually. Took me a while to find the right place tho. Glad it worked anyway.

---

