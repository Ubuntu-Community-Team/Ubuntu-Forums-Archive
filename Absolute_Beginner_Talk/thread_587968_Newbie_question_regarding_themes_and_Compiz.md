---
title: "Newbie question regarding themes and Compiz"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-10-23
I have Compiz Fusion running but don't quite get the themes.  When I load a theme in Emerald it changes the title bar / border of the window but not the menu, colours, etc.  I can download GTK theme and import them into the Appearance window (from Preferences > Appearence) but it never seems to change the buttons and the menu colours.

Am I doing something wrong?  Can I change everything in the Emerald theme manager?

---

### Post by realvz on 2007-10-23
emerald only changes window decorations...if you want the contents of the window to change you have to use gtk themes
what themes are you using and where are you downloading them from?

---

### Post by DrQuincy on 2007-10-23
That what I thought.  However:

1) I'm downloading gtk themes from gnome-look and none of them seem to effect the 'controls'.  They just stayy as glossy.

2) How come in Emerald each theme has an engine?

3) In Emerald if I go to the repositories tab and fetch themes no new ones show in the themes section.

---

### Post by blackened on 2007-10-23
Some gtk themes require different engines than those that come with the default install. For example, the Murrina themes require the gtk2-engines-murrine (installable with apt-get or synaptic). So the theme determines the engine required (unless the theme uses an engine that comes with the default install). 

Make sure you read the comments posted by the theme author on gnome-look as it should give the name of the engine required.

---

### Post by realvz on 2007-10-23
1) I'm downloading gtk themes from gnome-look and none of them seem to effect the 'controls'. They just stayy as glossy.
   Did you try hitting the customize button and see if the new option apart from glossy appears?

2) How come in Emerald each theme has an engine?
  i really dont know...I guess its about how many options do you have to configure in the themes...some engines have lesser options some have more.

3) In Emerald if I go to the repositories tab and fetch themes no new ones show in the themes section.
  try closing emerald and restarting after it has fetched the new themes.

---

### Post by skymera on 2007-10-23
to get themes

i got Emerald Themes
added a nice one to that
then...

compiz --replace -c emerald

i suggest that, it sticks too

---

### Post by DrQuincy on 2007-10-23
> **realvz said:**
> 1) I'm downloading gtk themes from gnome-look and none of them seem to effect the 'controls'. They just stayy as glossy.
   Did you try hitting the customize button and see if the new option apart from glossy appears?

3) In Emerald if I go to the repositories tab and fetch themes no new ones show in the themes section.
  try closing emerald and restarting after it has fetched the new themes.

Re 1: I tried that - it has the theme controls selected (smoked glass) yet it still shows Glossy.  Which ever one you choose it stays as glossy.  I had a problem like this with metacity some time ago . . . how do you launch appearence preferences from the shell?

Re 3: Tried that too but nothing.

---

### Post by DrQuincy on 2007-10-23
I remember what I did last time and it works.

Type switch2 in the terminal then choose your new theme; after that everything will be okay.

If you run gnome-control-center from the terminal you'll see that the AlphaCube theme causes an error.

---

