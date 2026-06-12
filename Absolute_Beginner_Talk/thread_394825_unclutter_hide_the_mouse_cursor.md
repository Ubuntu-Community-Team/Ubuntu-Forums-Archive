---
title: "unclutter: hide the mouse cursor"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-03-27
I found this little package over at [http://debaday.debian.net/](http://debaday.debian.net/) , it says in the article;

> Do you ever find that occasionally the mouse pointer obscures just the bit of the screen with the word you’re currently reading? Having to move the mouse or guess the word under the pointer is only a minor irritation but it can be an irritation none-the-less.

Unclutter is a small but unique package for X11. What it does is very simple: if you aren’t using the mouse, it hides the mouse. This is useful simply because if you aren’t using the pointer, there’s no reason for it to be visible. This may not sound particularly useful, but making the mouse be invisible frees up screen real estate, prevents it from distracting you, and just generally makes for a much more pleasant experience, particularly when reading a document or using primarily keyboard-based applications.

Unclutter is easy to use. Just put a line like this in your .xsession, .gnomerc, “Startup Programs” or wherever you enter commands to be run at startup/login:

unclutter &

Now, if you stop moving your mouse, the cursor will disappear after 5 seconds.

Have fun with this little package!

---

### Post by m83 on 2007-03-27
Indeed, unclutter is awesome. I use it all the time for 2 years now.

---

### Post by floke on 2007-03-27
It's in the repos :) 

sudo apt-get install unclutter

Thanks for the heads-up - been looking for something like this for watching youtube vids on zoom with beryl!

** EDIT ** Ok so it works but I can't find any menu/config. options for it - I have to run it from a terminal - do you know where I can edit the settings?

---

### Post by BirdZerk on 2007-03-27
I added unclutter to my startup programs in sessions, I suppose you could add arguments to the startup command, not sure about that.  To see the arguments type in a terminal
```
man unclutter
```

---

### Post by floke on 2007-03-28
Aha, cheers. 
I sussed that, but was hoping for a GUI. Still, if its a CLI then that's fine.
At least it does the job!

---

### Post by kostkon on 2007-03-28
Great little app, thanks!! I'll try it.

---

### Post by deuchar1 on 2007-03-28
I'll be trying that one myself!

No awards to anyone - you all missed the easiest but worst pun ever - it's "pointless".
Get it?

Note to self:   sudo apt-get install betterjokes

---

### Post by gcbzzzz on 2008-06-29
that would be a great functionality for a compiz plugin...

---

