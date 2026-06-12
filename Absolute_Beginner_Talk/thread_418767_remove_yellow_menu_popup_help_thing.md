---
title: "remove yellow menu popup help thing?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-22
Title says it all really, how do i get rid of the yellow popup i get when i hover the mouse over a menu or icon

and also while iam here, how do i get rid of the black lines that appear when i lower a window into the lower tray?

thanks in advance

---

### Post by mills on 2007-04-22
am i the only one annoyed by these features?

i mean c'mon, i don't need a popup to tell me that the application menu is to "browse and run applications" or that firefox is to "browse the world wide web"

ok it had its uses at 1st but iam bored of it now and iam sure the solution is easy

and the window retracting with repeating blacklines, well that annoyed me from day one and was hoping or even expecting feisty to abandon it for some reason

---

### Post by Campingman on 2007-04-22
Hi Mills,
You are not the only one, I saw a thread about this while ago but did not follow it up as it does not overly bother me.  I have searched the forums for yellow/box and pop but came up with a blank.  There is one out there somewhere.

---

### Post by mills on 2007-04-22
yeah i think i know the post your on about, and iam kickin myself for not following up on it straight away coz i cant  find it anywhere, i thought it would be easy to find again but ive made several attempts to find it but no joy

---

### Post by apunc1 on 2007-04-22
[http://ubuntuforums.org/showthread.php?t=414126&page=2&highlight=help+boxes](http://ubuntuforums.org/showthread.php?t=414126&page=2&highlight=help+boxes)

see reply by swab in the above thread for help with the black lines when minimizing windows

---

### Post by Swab on 2007-04-22
Alt+F2 and run "gconf-editor"

apps > panel > global  and uncheck tooltips_enabled

---

### Post by mills on 2007-04-22
ahhhh thats better

cheers swab, i knew it would be something simple

any ideas on the black window lines?

---

### Post by jiminycricket on 2007-04-22
You get rid of the black lines by putting metacity in reduced resources mode, from: [http://sourcefrog.net/weblog/software/gnome/metacity-slow-machines.html](http://sourcefrog.net/weblog/software/gnome/metacity-slow-machines.html)

gconftool-2 -t bool -s /apps/metacity/general/reduced_resources true
metacity-message restart

Or you could  use beryl or compiz, they have nice minimizing effects.

---

### Post by Campingman on 2007-04-22
An odd thing happens when I select reduced resources, it gets rid of the black lines but then if I hold down on a window to move it I get a grid of rectangles.  Is that normal?

---

### Post by mills on 2007-04-22
thats done it, chhers for the tip

and camping man if you got to preferences - accesabiltity - assisted technologies preferences and enable that will get rid of the wire mesh effect

cheers guys

---

