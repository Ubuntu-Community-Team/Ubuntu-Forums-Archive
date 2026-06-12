---
title: "Changing the theme of tooltips in gnome?"
date: 2007-03-08
forum: Art &amp; Design
---

### Post by ihavenoname on 2007-03-08
Does anyone know how to do this? Is there any gui function for this or is it a matter of manual editing. I am trying to setup a dark gnome theme, but I keep having to mess with the font colors because of the notifications. If I could just change the color it would make this perfect. Thanx.

---

### Post by rcmiv on 2007-03-20
This is a major annoyance.  I have googled for a week now, and have found nothing useful.  Figured I'd subscribe to this thread, and if I ever find anything I will post it here.

-rcmiv

---

### Post by ComplexNumber on 2007-03-20
> **ihavenoname said:**
> Does anyone know how to do this? Is there any gui function for this or is it a matter of manual editing. I am trying to setup a dark gnome theme, but I keep having to mess with the font colors because of the notifications. If I could just change the color it would make this perfect. Thanx.
use an application called gnome-color-chooser. get it from [here]("http://gnome-look.org/content/show.php/gnome-color-chooser?content=47349"). you may need some extra packages to run it, so when you run the configure script, it may report that certain dependencies aren't met. fire up synaptic and install the "dev" version of those packages that it claims are required, then rerun the configure script until there are no errors.

the font colour can either be set in the actual theme or in gnome-color-chooser.

here are 2 screenshots of it in action

NOTE: the colours chosen stay no matter what the theme chosen dictates. for example, if you choose a theme that has white tooltips, gnome-color-chooser will override that with the colours that you have chosen.

---

### Post by ihavenoname on 2007-03-20
> **ComplexNumber said:**
> use an application called gnome-color-chooser. get it from [here]("http://gnome-look.org/content/show.php/gnome-color-chooser?content=47349"). you may need some extra packages to run it, so when you run the configure script, it may report that certain dependencies aren't met. fire up synaptic and install the "dev" version of those packages that it claims are required, then rerun the configure script until there are no errors.

this is are 2 screenshots of it in action

NOTE: the colours chosen stay no matter what the theme chosen dictates. for example, if you choose a theme that has white tooltips, gnome-color-chooser will override that with the colours that you have chosen.

That's amazing thank you very much! I've been thinking of trying to learn how to make .debs this might be a good package to start with.  I'll probably just install it first then find out how to package it. If I ever get around to it I'll post it here. Again thanks for the tip.


nvm I found it in this repository.
[http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)

---

### Post by ComplexNumber on 2007-03-20
> 
nvm I found it in this repository.
[http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)
oh well. i wasn't aware that there had been a deb made for it. i guess that makes things easier.
[]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/")

---

### Post by ihavenoname on 2007-03-20
> **ComplexNumber said:**
> oh well. i wasn't aware that there had been a deb made for it. i guess that makes things easier.
'
yep, and it does exactly what I needed it to do. Thank you!

---

### Post by hikaricore on 2007-03-21
Is this a gui editor for the ~/.gtkrc-2.0 file by any chance?

---

### Post by ComplexNumber on 2007-03-21
> **hikaricore said:**
> Is this a gui editor for the ~/.gtkrc-2.0 file by any chance?
when you install gnome-colour-chooser, it add this line to the ~/.gtkrc-2.0 file:
```
include ".gtkrc-2.0-gnome-color-chooser"
```


so i guess that gnome-colour-chooser is a GUI editor for it, efectively.

---

### Post by hikaricore on 2007-03-21
That rocks like socks.

I've been to find something like this for awhile after
editing my gtkrc by hand for nearly a year.  =)

The human mind can only take editing gui colors in
text for so long before it shuts down. lol

---

