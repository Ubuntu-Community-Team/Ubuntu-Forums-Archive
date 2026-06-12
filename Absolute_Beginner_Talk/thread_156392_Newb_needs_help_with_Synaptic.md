---
title: "Newb needs help with Synaptic"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by robTard on 2006-04-06
I've been trying to set up my airport card, in order to do so I need the ndisgtk package which is dependent upon the ndiswrapper-utils package.  Synaptic cannot find the ndiswrapper-utils package hence i cannot install ndisgtk.  I have built the extra repositories and don't know what to do next...

---

### Post by aysiu on 2006-04-06
You shouldn't need extra repositories for *ndiswrapper-utils* according to [this](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=name&subword=1&version=all&release=all).

You will need the universe repositories for *ndisgtk*, though.

I would use [this](http://www.psychocats.net/ubuntu/sources) to get extra repositories.

---

### Post by catlett on 2006-04-07
Any time you add and or change your repositories you need to update your cache of files in Synaptic Package Manager. If you followed the directions on enabling extra repositories type in this command ```
sudo apt-get update
``` Now open up Synaptic Package Mnager (either by the menu or by typing in "synaptic" in the terminal). Once you open Synaptic scroll through the list until yopu see the program. Highlight it and right click. Choose "mark for installation". Then choose "apply" at the top of the Synaptic menu. Let Synaptic run. You will either have the program in your menu or you can start it by going to the terminal and typing in the name of the program. (you can start programs by typing in their name in the terminal). Hope it helps . Regards.

---

### Post by linear on 2006-04-07
[quote=robTard]I've been trying to set up my **airport card**...
Synaptic cannot find the **ndiswrapper-utils** package hence i cannot install ndisgtk. I have built the extra repositories and don't know what to do next...[/quote]
What platform? ndiswrapper doesn't exist for PPC.
 
If that's not it - do you have the install CD enabled in sources.list? It might be there.

---

