---
title: "How to remove fade to black"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by icelechi on 2007-05-07
Hi,
I use Ubuntu 6.06 and I really like it. But there is one problem that irks me some: When administrative programs are starting up, they prompt for a password. When they do this, the screen fades to black.

Is there any way to get rid of this fading to black?:confused:  It really doesn't look good on my computer since it has a chintzy graphics card.

Thanks

---

### Post by rich.bradshaw on 2007-05-07
Thought this might be about AC/DC then!

The application that does that is called gksudo - you should look that up on google to see if there are any settings you can change. Not sure if it's possible but it probably is!

---

### Post by Cypher on 2007-05-07
If you're running the Ubuntu desktop, that's the gksudo program doing that. Choose a particular admin program that is causing this, right click the properties and see if you see "gksudo" before the program itself, if so, add the option "-g" after "gksudo" and see how it behaves..

---

### Post by icelechi on 2007-05-07
Will do.
Thanks!

---

### Post by rai4shu2 on 2007-05-07
The fader is there to reassure you that the dialog is geniune rather than a spoof dialog. It might be nice if it had a faster fade, though.

---

### Post by 3rdalbum on 2007-05-07
There is a way.

Press Alt-F2 and type "gconf-editor". Expand the "apps" list, and then select "gksu". Check the "disable-grab" item.

This will disable the grab on your user account, and also disable the darkening effect. Unfortunately, it's a security risk to run without the grab - even Windows Vista grabs the keyboard, mouse and screen when asking for UAC confirmation.

---

### Post by rich.bradshaw on 2007-05-09
What is there to stop a bogus window appearing with a darkened background? How is the darkening locked to gksudo?

---

### Post by Jose Catre-Vandis on 2007-05-09
[QUOTE=]There is a way.

Press Alt-F2 and type "gconf-editor". Expand the "apps" list, and then select "gksu". Check the "disable-grab" item.

This will disable the grab on your user account, and also disable the darkening effect. Unfortunately, it's a security risk to run without the grab - even Windows Vista grabs the keyboard, mouse and screen when asking for UAC confirmation.[/QUOTE]


Nice tip, thanks:)

---

### Post by mcduck on 2007-05-09
Other way is to go to System/Preferences/Assistive Technology Preferences and enable 'Password Dialogs as Floating Windows'.

This will add title bars to password windows and disable the fading effect.

@ rich.bradshaw: 'Fade To Black' is Metallica's song. 'Back in Black' is from AC/DC ;)

---

### Post by ticopelp on 2007-05-09
> **rich.bradshaw said:**
> Thought this might be about AC/DC then!

Speaking of which, how do I get rid of "Dirty Deeds Done Dirt Cheap?"

---

### Post by Ptero-4 on 2008-02-15
> **rich.bradshaw said:**
> What is there to stop a bogus window appearing with a darkened background? How is the darkening locked to gksudo?

The trick isn't just the darkish color (which is actually a semitransparent layer using true transparency and compositing if available) it's the fact that the keyboard is locked to gksudo and that if a malicious app used it it would be known by now.

---

