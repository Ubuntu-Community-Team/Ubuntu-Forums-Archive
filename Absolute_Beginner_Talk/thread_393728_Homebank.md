---
title: "Homebank"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by deafchickadee on 2007-03-26
I installed homebank onto my desktop and converted to the files to deb. It apparently has been installed but I can't find it and doesn't show up in the applications menu..  im going nuts..  

I would like it to be displayed in the applications menu. Can anyone please help?

---

### Post by cowlip on 2007-03-26
try in a terminal:

locate homebank

or 

whereis homebank

If these don't work it might not have been indexed yet, try 

find / -name homebank 

(the syntax is, 'find PATH EXPRESSION', so this looks in all your directories under '/')

So after you've found out where it's installed, add it to your applications menu by right clicking on it and selecting "edit menus".

---

### Post by deafchickadee on 2007-03-26
Hi Cowlip..

thanks for your quick reply.. Im not 100% sure what you mean "indexing"

..  ran the codes you suggested

Where is ran like this:

ella@ella:~$ whereis homebank
homebank: /usr/local/bin/homebank
ella@ella:~$ 


... tried right clicking as you suggested..  bt there are no options to 

"edit menus"

---

### Post by cowlip on 2007-03-26
ok can you run 'alacarte' in the terminal?  That will let you create a new menu.  Sometimes there's a delay in the menu creation for a new program as well, but sometimes it just doesn't create one and you have to do it manually.  You should also be able to access alacarte by looking for the gnome menu with the orange ubuntu symbol or the hovering the mouse over the "Applications Places System" menu bar, and then right click it, and choose "Edit menu".

By indexing I meant the locate service that I think the command locate and whereis use, sometimes if you install something it can take a while to show up using these commands.

---

### Post by deafchickadee on 2007-03-26
hmm alcarte isn't responding...

ella@ella:~$ alcarte
bash: alcarte: command not found
ella@ella:~$

---

### Post by cowlip on 2007-03-26
it looks like you missed an 'a' in al**a**carte, I would try it again.   Or maybe gnome-menu or gnome-menus or gnome-menu-editor

---

### Post by kinson on 2007-03-26
> **deafchickadee said:**
> 
... tried right clicking as you suggested..  bt there are no options to 

"edit menus"

I might sound a bit stupid here, but I hope you aren't right clicking in the terminal.

You're supposed to right click the "applications" button on the gnome panel/task bar(whatever its called).

Apologies if this seems offensive :/

Cheers,
Kinson

---

