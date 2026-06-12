---
title: "Confused about Synaptic PM"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-18
I open up Synaptic PM, go to Search and type in Sea Monkey the browser. It returns a result showing Sea Monkey on the left and a couple of games on the right panel (see attachment). How does this thing work? Also, what's the difference between Synaptic and Applications/Add-Remove? I'm using Ubuntu 6.06. Thanks.

---

### Post by Ozitraveller on 2007-04-18
Try here:

SynapticHowto
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


:)

---

### Post by RomeReactor on 2007-04-18
Hi. That happened because when you did your search for **sea monkey**, the context you were searching for was **Description and Name**, so any package that has the words **sea** and **monkey** in either their name or description will appear as results. However, SeaMonkey, the internet suite, is not on the official repositories (not on the ones i have, at least), so that's why it didn't show up for you. If you want more control over your searches, change the search context on the search box to **Look in: Name**.

---

### Post by jacatone on 2007-04-18
I think I get it. Are all these "packages" part of the Ubuntu install or are they simply indications of what can be downloaded and installed. I tried installing a download manager called freeloader and it obviously downloaded some updates before installing. But where is the program? I don't see it any where in the Applications menu. Thanks.

---

### Post by Madpilot on 2007-04-18
The lists in Synaptic or Add/Remove Applications are available packages, not everything is going to be installed by default. (it couldn't be, there's 17,000+ packages in Ubuntu's repositories!)

Not everything has a menu entry, and not everything in the repositories is even a graphical application - lots and lots of command-line apps in there.

"Freeloader" says it's a Gnome app, so it's got a GUI, at least, but it might not have a menu entry by default. You can start it with Alt+F2 to bring up the Run Applications utility, then just type 'freeloader'.

---

### Post by RomeReactor on 2007-04-18
Sometimes the gnome-panels need a restart after a program is installed to show the entry on the menus; open the system monitor (System-->Administration-->System Monitor), find **gnome-panel**, right-click on it and select **kill process**. That will restart them and Freeloader should now appear under "Applications-->Internet".

---

