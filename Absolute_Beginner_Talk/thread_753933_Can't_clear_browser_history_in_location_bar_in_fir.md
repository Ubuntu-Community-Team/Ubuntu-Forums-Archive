---
title: "Can't clear browser history in location bar in firefox 3beta5"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Michl on 2008-04-13
Firefox 3.0 beta 5 doesn't clear the browsing history in the drop down menu
of the location bar.  I'm not sure what happens when you clear the browsing
history because some locations disappear but others stay there.  In earlier
versions this was not a problem for me.

Alternatively, what is the name of the file where this info is stored so that I
can clear it by hand?  Is is that doable?  Everything should be doable in
linux.

M

---

### Post by energy. on 2008-04-13
> **Michl said:**
> Firefox 3.0 beta 5 doesn't clear the browsing history in the drop down menu
of the location bar.  I'm not sure what happens when you clear the browsing
history because some locations disappear but others stay there.  In earlier
versions this was not a problem for me.

Alternatively, what is the name of the file where this info is stored so that I
can clear it by hand?  Is is that doable?  Everything should be doable in
linux.

M

I'm having a similar issue.  It isn't clearing out everything like in previous versions of firefox, instead, sites that I have bookmarked stay in this menu even after "private data" is cleared.  

Are the sites that are staying in your bar bookmarked?

---

### Post by 289Shelby on 2008-04-13
Have a look here and see it this is what you're looking for:

[http://kb.mozillazine.org/Browser.urlbar.maxRichResults](http://kb.mozillazine.org/Browser.urlbar.maxRichResults)

---

### Post by Michl on 2008-04-13
> **energy. said:**
> 
Are the sites that are staying in your bar bookmarked?

No, come to think of it none of them are bookmarked.  I don;t
know what principle is being used.


[QUOTE=289SShelby]]Have a look here and see it this is what you're looking for:

[http://kb.mozillazine.org/Browser.urlbar.maxRichResults](http://kb.mozillazine.org/Browser.urlbar.maxRichResults)[/QUOTE]

Thanks -- this does explain the problem.  Set the browser.urlbar.maxRichResults
to 0 and that gets rid of everything.  But now this feature looks like a regression 
because it seems that the available choice is now worse.  Before you could keep your history
in the location drop down bar until you decided to clear it.  Now you have to go
to about:config and change the configuration to clear the history, and that's a pain in
the butt.  For example, what am I going to tell my wife -- you have to enter
about:config, get a scary warning, then get a monster list, find browser.what
was that again... change save ..... .

---

### Post by 289Shelby on 2008-04-14
> 
Before you could keep your history
in the location drop down bar until you decided to clear it.


I have to agree with you there. The first extension I've always installed is 'Prefbar'. Unfortunately it's not compatible with beta5 at the moment. From what you say I think Prefbar will do exactly what you want. We'll have to wait and see.

---

### Post by bluester on 2008-06-08
> **289Shelby said:**
> Have a look here and see it this is what you're looking for:

[http://kb.mozillazine.org/Browser.urlbar.maxRichResults](http://kb.mozillazine.org/Browser.urlbar.maxRichResults)

This is what I was looking for.
Thanks for the information and support! :)

---

