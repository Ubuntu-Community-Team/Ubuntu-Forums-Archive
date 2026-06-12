---
title: "This theme suggests a button layout. (?)"
date: 2011-02-12
forum: Art &amp; Design
---

### Post by Copper Bezel on 2011-02-12
Hello all.

Minor Metacity question. I have my buttons on the left, Unity-style, but every theme I download is styled the other way. I'm okay with that - I'd like to be able to see the themes as they're intended - but I hate having to go back into gconf-editor and revert the layout if I switch back to my usual theme (a version of LaGaDesk N12 that I've modified the hell out of.) If I select this theme, Appearance Preferences notes that it "suggests a button layout," which is, of course, the default, with buttons on the right, menu on the left, etc. Is there any way to edit the Metacity theme such that the "suggested" layout is the simple close,minimize I actually use with this theme?

Thanks for any help.

---

### Post by jerrrys on 2011-02-12
i like the easy way, ubuntu tweak

[ATTACH]183323[/ATTACH]

---

### Post by Copper Bezel on 2011-02-12
Well, that's a couple of steps shorter than using GConf, since it's a "more GUI" way of changing the same keys - thanks! But any theme switch will still change them back. Does anyone know where it is that these themes are "suggesting" button layouts and how to change that (so that I'm not applying it globally, but just to my theme?)

---

### Post by Mr. Picklesworth on 2011-02-12
> **Copper Bezel said:**
> Well, that's a couple of steps shorter than using GConf, since it's a "more GUI" way of changing the same keys - thanks! But any theme switch will still change them back. Does anyone know where it is that these themes are "suggesting" button layouts and how to change that (so that I'm not applying it globally, but just to my theme?)

Yeah, if you go to where the theme is installed (probably under .themes in your home folder), there's a file called index.theme. It might actually appear as the theme name in the file browser; just drag it to a text editor to open it.

Now, under [X-GNOME-Metatheme], there may already be a key called ButtonLayout. So, either change that key or add a line at the bottom that says:
ButtonLayout=close,minimize,maximize:

---

### Post by Copper Bezel on 2011-02-12
Ah! Thank you! Exactly what I was looking for. And here I was looking in the Metacity theme file because it was a Metacity setting....

Thanks again!

---

