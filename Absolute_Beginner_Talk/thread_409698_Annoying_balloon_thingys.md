---
title: "Annoying balloon thingys"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2007-04-14
I'm not sure what they're called so I can't do a search, but when you hover your mouse above the application shortcuts on the taskbar you get up these dirty great balloon things that tell you what the quick laucnh buttons are .

Can I stop those coming up?

I'm running Kubuntu.

---

### Post by N Clement on 2007-04-14
I think what you are talking about are called tool tips.  I run Ubuntu (Gnome instead of KDE), so I can't really give you a good idea of how to fix this other than to look for options on tool tips.

Edit: tooltips not tool tips

---

### Post by BoneKracker on 2007-04-14
And if that's your biggest problem in life today, count yourself among the lucky.

:D

---

### Post by dpar on 2007-04-14
I got mine turned off using conf-editor, I have company right now but I'll try to get back with how I did it soon. Do a search for tooltips........theres instructions on how to do it. By the way, I'm using Feisty, but it should work.

---

### Post by RomeReactor on 2007-04-14
Hi. To disable tooltips, right-click on the panel and select "Configure Panel-->Appearance" an un-check the "Show tooltips" near the top.

---

### Post by dpar on 2007-04-14
Go to terminal and enter

gconf-editor

Then click on apps>panel>global

uncheck tooltips-enabled

This is for Gnome, not sure what it would be in KDE......Maybe kconf-editor????:lolflag:

---

### Post by SpongeBob SquarePants on 2007-04-14
Hi guys,

Disabling tooltips doesn't work. I tried that already. However, I have just sussed out how you do stop it.

Configure Panel>Appearance>untick "Enable icon mouseover effects".

Job's a good 'un.

Next job, stopping that daft mouse animation everytime I click on something....lol.

---

