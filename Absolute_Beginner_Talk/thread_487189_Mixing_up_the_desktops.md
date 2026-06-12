---
title: "Mixing up the desktops"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by rzj on 2007-06-28
I have this problem with buffets - not trying a little of everything is a major challenge.

So of course when I stumbled across the instructions for loading KDE on top of ubuntu I HAD to try it. Then when I discovered that (as should have been obvious) it was another whole exercise in "now where's the program to do this.." when I hadn't yet got the hang of gnome, I uninstalled it again. 

Strangely I seem to still have Konqueror that sort of still works but has an empty tools menu, KNetworkManager that doesn't seem to do anything and Konsole which seems to work and I like much better than Terminal.

So is there any way to identify which KDE tools will work in Gnome, and how do I know when a Synaptic or google search finds an application whether it is gnome compatible or not?

Ray

---

### Post by p_quarles on 2007-06-28
Well, first of all, as you now know: KDE programs will work in Gnome as long as the KDE libraries are installed. They don't require the entire desktop environment. 

Second, most KDE tools will work in Gnome, it's just a matter of dependencies. If you're using apt-get, aptitude or synaptic, the system will retrieve all of the dependencies, tell you how much space they'll take, and ask if you want to install them. 

Finally, if you'd like KNetwork manager to run, you could just uninstall then reinstall it, and it should get the dependencies.

---

### Post by rzj on 2007-06-28
Thanks,

I do like some of the tools from KDE but I found the actual desktop a bit annoying and I missed some of the tools that I'd got comfortable with in gnome, so maybe I'll try a mix and match.

It's kind of strange how having an open architecture gives you lots of options but makes it much harder to choose the right ones! I keep ending up with a nagging suspicion that every one else may be using some tool for a task that is much better than the one I'm using. 

Ray

---

