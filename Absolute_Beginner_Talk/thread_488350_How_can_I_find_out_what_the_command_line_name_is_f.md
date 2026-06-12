---
title: "How can I find out what the command line name is for an app?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-30
Sometimes the apps have a different names in the terminal than they do in the menus. How do I find out what a programs command line name is?

---

### Post by ashwin_cse on 2007-06-30
In the console type "apropos name-of-the-app" without the qoutes.

---

### Post by RomeReactor on 2007-06-30
Hi. First open Synaptic (System-->Administration-->Synaptic Package Manager) and search for the application you want to run from the command line. Once you find it, highlight it and click on the **Properties** button, and go to the **Installed Files** tab; then look for entries in **/usr/bin, /usr/sbin,** or **/usr/share/bin**. Those are the ones you want to enter into the command line, either by going to the terminal (Applications-->Accessories-->Terminal) or by pressing **ALT+F2**.

EDIT
> In the console type "apropos name-of-the-app" without the qoutes.
That works even better :)

---

