---
title: "How to add a new installed program to a menu?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by kranknut on 2006-07-12
*Confessions of a newbie*
Hi:
I just started on Ubuntu/Linux and although I have had to deal with a number of issues its been great. I am a 'believer' already...not to say an Evangelist! 

Here is a problem I have been trying to solve. Through Synaptic I installed a program called Sixpack. But it won't show in the Applications menu. I have tried to get it to work via Alacarte, but Alacarte won't let me do anything with Debian. I can't--for now--figure out how to run it from the run command. 
Could anyone help me with this??

Thanks...
K

---

### Post by timetunnel on 2006-07-12
Lots of packages don't install proper menu items, which is a pity, I think. Here's what you can do:

[LIST=1]
[*]In Synaptic, in menu "Preferences" open the preferences windows. In tab "general" there's an option saying something like "Show package properties in main window". Enable that.

[*]Then search for package "sixpack". Below the package list in Synaptic there are several tabs, one's called "installed files". Mark the "sixpack" package with you mouse as the current on and change to that tab. You'll see all files that were installed with that package. Going through the list look for entries with "/usr/bin". There you'll mostly find the executable. In this case it's the file "/usr/bin/bib". 

[*]Now open the Alacarte Menu Editor. Pick a category on the left side by clicking on it. On my system, it'll last about 2 seconds until my selection is applied. Then click on menu "file" and choose "new". Enter something in field "Name", in "Command" enter "/usr/bin/bib" (or whatever the executable is called). You can choose an icon as well
[/LIST]

You should now have a menu item.

I just installed the "sixpack" package to have a look and it seems to have problems. Running "bib" from the command line gives an error. I have no idea what that package does and how to solve this. But it seems like you maybe won't be lucky after you have the menu item, because it will do nothing due to this error.

---

### Post by kranknut on 2006-07-12
Thanks so much for the prompt reply...
Now at least I have some sense of things and I really appreciate your clear and concise directions...


with gratitude,
K
ps.
Like you noted I didn't have luck with Sixpack through the Menu. I am going to read more about it--maybe it works embedded in the Openoffice program. Basically it is a bibliogrpahy/reference manager...and I need something like this to be completely comfortable about making a 100% switch to it.
best...

---

### Post by timetunnel on 2006-07-12
You're welcome. :-)

---

