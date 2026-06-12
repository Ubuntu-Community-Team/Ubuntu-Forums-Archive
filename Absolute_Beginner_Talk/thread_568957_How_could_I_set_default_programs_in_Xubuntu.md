---
title: "How could I set default programs in Xubuntu?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by tico on 2007-10-06
Hi,

I'm using Xubuntu and am getting some trouble with opening files. Here's what's happening: I've installed Krusader, Openoffice and Adobe Reader. If I double click a pdf file in Krusader, it opens with Adobe Reader. If I double click the same file in my desktop, it opens with Evince. If I double click an odt (Openoffice text) file in Krusader, it opens with Openoffice. If I do this in my desktop, it opens with Abiword.
I'd like to always have my pdfs opened with Adobe Reader and my odts with Openoffice.
How could I make this? Is there a way to stop this "double" file association?
Thanks.

---

### Post by julian67 on 2007-10-06
With a mix of applications from different desktop environments you probably need the config tools from those environments, though only temporarily. For controlling default behaviour for your Gnome applications you need gconf editor, I'm sorry but I don't remember the KDE equivalent. I had a similar problem trying to get evolution mail to open links in epiphany and not firefox and I had to install gconf editor to fix it. Another option for you is to only have one application per task, i.e. only one application that can read pdf, only one word processor and so on. Personally I would dump adobe reader and use evince, dump krusader and use emelfm2, dump either abiword or openoffice.  This is not a criticism of any of those apps (krusader must be one of the best 2 pane file managers).

---

### Post by jslmg on 2008-01-02
> trying to get evolution mail to open links in epiphany and not firefox

Hi, Julian. This is exactly what I'm doing now. Did you succeed? Where did you go in gconf-editor to make the change? Or is there another method you used?

I've already tried changing "Desktop/applications/browser" from firefox to epiphany--no go!

---

### Post by jslmg on 2008-01-02
Actually, never mind... System-->Preferences-->Preferred Applications did the trick. That was what I was looking for all along! Found it somewhere in these forums.

---

### Post by julian67 on 2008-01-02
> **jslmg said:**
> Actually, never mind... System-->Preferences-->Preferred Applications did the trick. That was what I was looking for all along! Found it somewhere in these forums.

You'll probably still find that some applications open links in Firefox, or in a new window when you prefer a new tab. In gconf-editor you can go to desktop>applications>browser and set the browser to epiphany, or epiphany -n if you always want pages forced to open in a new tab.  You might also need to go to 
gnome>url-handlers and set the default as epiphany --new-tab %s

---

### Post by jken146 on 2008-01-02
In general in Xubuntu, the easiest way of setting a certain file type to open with a certain program is to right click on a file of that type, click on "Open with other application" and select the app you want from the list (or type it in).  Make sure the box at the bottom is ticked and click OK.

---

### Post by julian67 on 2008-01-02
> **jken146 said:**
> In general in Xubuntu, the easiest way of setting a certain file type to open with a certain program is to right click on a file of that type, click on "Open with other application" and select the app you want from the list (or type it in).  Make sure the box at the bottom is ticked and click OK.

Yes but that doesn't work for the whole environment, particularly if there are applications from KDE and Gnome....i.e. Gnome applications will go by the gconf default not  by the user selected preferred application. On a Xubuntu system the browser default is Firefox and if you install Epiphany you must also install gconf-editor if you want to fully override that default. It's normal for the applications themselves (i.e. evolution) *not* to to offer the user the choice because it's assumed the user has set preferences system wide (Gnome system wide, not Xfce system wide). If you mix kde and gnome apps you'll find you need to use both gnome and kde config tools or you can end up with different applications using different sets of default applications.....hence this thread! ;-)

---

### Post by jslmg on 2008-01-02
> **julian67 said:**
> You'll probably still find that some applications open links in Firefox, or in a new window when you prefer a new tab. In gconf-editor you can go to desktop>applications>browser and set the browser to epiphany, or epiphany -n if you always want pages forced to open in a new tab.  You might also need to go to 
gnome>url-handlers and set the default as epiphany --new-tab %s

Thanks, Julian. That's useful information, especially about getting links to open new tabs instead of new windows. Note that I had already tried changing the desktop>applications>browser entry, to no avail.  Preferred applications did it, at least for now.

---

