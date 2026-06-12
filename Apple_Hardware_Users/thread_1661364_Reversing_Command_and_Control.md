---
title: "Reversing Command and Control?"
date: 2011-01-06
forum: Apple Hardware Users
---

### Post by Sugoi48 on 2011-01-06
Is there a way to reverse the functionality of the cmd and ctrl buttons? I'm used to the Mac layout and am often hitting cmd instead of ctrl. Thank you!

---

### Post by conundrumx on 2011-01-06
> **Sugoi48 said:**
> Is there a way to reverse the functionality of the cmd and ctrl buttons? I'm used to the Mac layout and am often hitting cmd instead of ctrl. Thank you!

[http://www.emacswiki.org/emacs/XModMap](http://www.emacswiki.org/emacs/XModMap)

---

### Post by SwarfEye on 2011-01-06
hey,

So I'm working on this same problem.  I just installed Ubuntu 10.10 on a macbookpro.

Anyway, I started out with the instructions here...

[https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Keyboard](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Keyboard)

This is not macbookpro specific, and should work with just about anything.  I just cut and pasted the file and ran the commands and viola!

That said, I'm not entirely happy.  I also want to get the right command button to work like a crtl button so that I can use tabbed browsing in fire fox the way that I am used to from OSX.  This feature is not included.

So, in my quest for that, I found your thread and tried out approach taken explained in...

[http://www.emacswiki.org/emacs/XModMap](http://www.emacswiki.org/emacs/XModMap)

Basically, this solution seems much more straight forward in that suggests (or at lest I understood) that you could run xev, figure out what the keycodes and keysyms were and then just write an .xmodmap file that looked like this...

keycode 133 = Control_L
keycode 134 = Control_R
keycode 37 = Super_L

run it with...

xmodmap ~/.xmodmap

and everything would be dreamy.

I have not found this to be the case.

While xev shows that the keys appear to be mapping correctly, they still perform in the same old way.

Still hacking away!!!

Good luck!

---

