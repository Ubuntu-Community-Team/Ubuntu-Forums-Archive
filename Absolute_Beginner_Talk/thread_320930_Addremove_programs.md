---
title: "Add/remove programs"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2006-12-18
Hi there,
Since last night, every time I choose Add/Remove.. I get the following:

[IMG]http://img257.imageshack.us/img257/8384/errorql4.jpg[/IMG]

Now, if I click reload, it says downloading files.. and goes to 14/14 (in zero time, so fast that I can't click details before it's done).  And it works normally.  [EDIT: no it doesn't, see post below].

However, it does this every time I open the add/remove.

I've tried the apt-get update etc, to no avail.  It's a minor niggle really but I'd like it ironed out if at all possible.

Appreciate any help you guys can offer me.

Matt

---

### Post by Hurricane on 2006-12-18
Hm, well I thought it operated normally.  But it appears I can't install any software using add/remove; I get the following when trying:

ePDFViewer (or whatever) cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by Bachstelze on 2006-12-18
Is there any reason why you want to use that thing instead of apt-get/Synaptic ? I think you will be better of with one of them.

---

### Post by Hurricane on 2006-12-18
Sure, if I'm just browsing for some software (when I don't know which piece I want), I can search for categories and types of software...

---

### Post by Hurricane on 2006-12-18
I've just re-added some of my reps back into sources.list (not the default ones, ones I've added over time) and I'm now able to install software again.. however this original problem still persists.

---

### Post by Hurricane on 2006-12-18
Sorry to be a pain.

This problem has fixed itself as quick as it created itself.  Just went in again, and all is well.  All I did was uncomment all my sources.  However, I only commented them in the first place as an attempt to fix this problem (!).

This is one I can't explain but am happy it's fixed.

Sorry for the trouble

Matt

---

