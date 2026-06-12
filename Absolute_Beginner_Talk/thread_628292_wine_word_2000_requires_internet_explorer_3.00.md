---
title: "wine word 2000 requires internet explorer 3.00?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by terryeden on 2007-12-01
I've installed MS Office 2k using Wine-0.9.33. Running Feisty.

Word installs fine and I can open and edit documents.  Whenever I copy anything, I get a pop-up which says

"This feature requires Microsoft Internet Explorer 3.00 or greater."

I've installed IEs4Linux - I can run IE, but it doesn't stop Word from complaining.

What's interesting is that after I've dismissed the pop-up (several times) I can paste without problem.

Yes, I can and do use OOO, but there are some complex documents which only open correctly in Word.

Any thoughts?

---

### Post by lightstream on 2007-12-01
I don't use Word so I don't have direct experience I'm afraid. 

Have you tried changing the Windows version which Wine uses? No idea if it would make a difference though...

Certainly there should be some way around this because plenty of apps use IE DLLs but still run on Wine without a problem! good luck...

---

### Post by DezSP on 2007-12-01
IEs4Linux doesn't do a proper installation of IE as a system component, only the browser itself. Thus other programs that depend on it won't run. You need to install IE natively, which nowadays is bloody hard since Microsoft don't offer downloads of anything below IE6 now. Still, might be possible if you can hack it enough.

---

### Post by SunnyRabbiera on 2007-12-01
ehh you can try to install IE6 on wine, IEs4Linux simply has its own thing in the system so installing it and expecting office to work wont happen...
from what I know IEs4Linux installs things in its own private directory away from the wine core.

---

### Post by maniac_X on 2007-12-01
I have an old magazine disc that has IE 3.0 on it. link below

edit: [http://www.sendmefile.com/00598917](http://www.sendmefile.com/00598917)

On a side note, I have run across [**[COLOR="Red"]this site[/COLOR]**]("http://gaming.gwos.org/doku.php/wine:winestuff") that discusses installing the 
**Wine Gecko IE engine** instead of IE since IE can mess things up.

---

### Post by terryeden on 2007-12-22
> **maniac_X said:**
> 
On a side note, I have run across [**[COLOR="Red"]this site[/COLOR]**]("http://gaming.gwos.org/doku.php/wine:winestuff") that discusses installing the 
**Wine Gecko IE engine** instead of IE since IE can mess things up.

Just wanted to say, I followed the instruction in that link and it all worked perfectly!

Many thanks

T

---

