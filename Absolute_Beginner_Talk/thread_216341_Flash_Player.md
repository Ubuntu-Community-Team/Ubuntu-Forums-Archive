---
title: "Flash Player"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2006-07-15
Anybody knows when a flash player upgrade will be available for linux.  There some site I can see because of the player version?

---

### Post by Teddy_P on 2006-07-15
Someone suggested this in another thread in a different site.
I tried it and it works for the sties my kids go to and I have not seen any problems.

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

This gets past the "check" for the version but of course does not help if they are using newer features than 7 provides. 


Hope this helps
Teddy

---

### Post by kurniawands on 2006-07-15
download it from adobe...

---

### Post by InuyashaDuelist on 2006-07-15
@kurniawands, don't you think that's a little too obvious?;) 

Adobe doesn't offer a version of the flash player over version 7.

However, if I can recall correctly, a third-party source was developing an open-source version of flash player. I may be wrong, though.

---

### Post by %hMa@?b&lt;C on 2006-07-15
are you thinking of gnash?
[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

---

### Post by InuyashaDuelist on 2006-07-15
It's possible. I cannot recall much about it, though.

---

### Post by crispy_420 on 2006-07-15
I think that linux project you are thinking of is here:

[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

And I did read (not sure where) that adobe is discontinuing linux support. Don't count on future updates.

On a side note, even on my windows box certain websites don't want to work unless I use internet explorer. A good example is Gnarls Barkley's website. Maybe it is some sort of activeX controll, I don't know.

---

### Post by Bloch on 2006-07-15
Adobe is committed to a Flash 9 for Linux. 
The developer working on it at Adobe keeps a blog:
[http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

---

### Post by synacktion on 2006-07-15
I wouldn't get my hopes up - there was about the same amount of talk for Flash Player 8 a while back and I have yet to see it released... Let alone a 64-bit version 7.  At least I see that they are acknowledging this fact in the linked blogs.  So tell all your friends to stop supporting flash.

---

### Post by duva on 2006-07-15
Well, this did the trick for being able to play game trailers in ign.com

> **Teddy_P said:**
> Someone suggested this in another thread in a different site.
I tried it and it works for the sties my kids go to and I have not seen any problems.

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

This gets past the "check" for the version but of course does not help if they are using newer features than 7 provides. 


Hope this helps
Teddy

---

### Post by deanlinkous on 2006-07-15
ROCKS doesnt it :)the proper quote 
> **deanlinkous said:**
> Here is what I do on debian etch.

download flash, unpack flash, install to /usr/lib/firefox

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

This gets past the "check" for the version but of course does not help if they are using newer features than 7 provides.

Works for a good number of sites, my kids games sites...

...working on something else but I am afraid it is going to end up a failure....wait and see...

---

