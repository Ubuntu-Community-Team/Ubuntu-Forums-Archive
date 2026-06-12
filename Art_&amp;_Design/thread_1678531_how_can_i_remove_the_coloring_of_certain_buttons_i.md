---
title: "how can i remove the coloring of certain buttons in the ambiance theme?"
date: 2011-01-30
forum: Art &amp; Design
---

### Post by iamnotthemessiah on 2011-01-30
[IMG]http://i56.tinypic.com/afdkki.jpg[/IMG]

in short i want to remove the full colouring of certain buttons

---

### Post by Copper Bezel on 2011-01-31
Is that color coming from your system colors (I.e. "selected",) or is it in the image itself? I only ask because if it's the latter, your job here will be easier....

Either way, you'll be replacing one .png with a copy of another, so search in Nautilus for .png in the GTK folder of the theme so that you have a big scrollable list of all the images used in the controls, look for the two button prelight files, and make a copy of the one you like in the name of the one you don't.

If it's a theme the system came with, which Ambiance kinda is, isn't it, you'll want to copy it to your /home/user/.themes directory so that you can modify it.

I empathize - I've been making little nitpicking modifications like this to the two themes I use (two accounts), and it can become a bit of an obsession. But I want things to be *neat*.

---

