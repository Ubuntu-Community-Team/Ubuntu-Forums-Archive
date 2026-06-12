---
title: "problem accessing gmail/hotmail"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Patrissimo on 2006-03-11
i was unable to access gmail from firefox in ubuntu. i dual boot, and i could do it in firefox in xp.  someone suggested i try another browser, so i installed epiphany and still couldn't get to my email. 

i then installed kubuntu ( i figured i'd be installing dapper drake in a few weeks, so why not play around with KDE in the meantime) and i could open my emails with konqueror, but not firefox. 

i didn't really like KDE, so i'm back to gnome, with the same problem.

any idea what's going on here?

please don't assume that i've done all the basics. it could be something fundamental that i've overlooked.

---

### Post by Klaidas on 2006-03-11
Was there any error messages? What happened?
I use Ubuntu w/ Firefox and it works for me :-k

---

### Post by Patrissimo on 2006-03-11
no error messages. it just times out.
sometimes i can get to the home page, but after that nothing happens.

---

### Post by NeghVar on 2006-03-11
I don't think it matters, but are you using the Gmail checker extension are signing in from web page?

Like I said I don't think it would matter but I don' know.

---

### Post by Patrissimo on 2006-03-11
[QUOTE=NeghVar]I don't think it matters, but are you using the Gmail checker extension are signing in from web page?[/QUOTE]

I don't think so, I don't know what that is.

---

### Post by BoyOfDestiny on 2006-03-11
I think I have a solution... I've noticed this happens often (for me anyway)...

When gmail times out... look at the url... if it's [http://blah](http://blah) blah
change http:// to https:// and hit enter

---

### Post by Patrissimo on 2006-03-12
boy of destiny, i tried what you suggested and no luck.

then i googled gmail and found a proxy called 'browse at work.' it had a url that started with https://   so i tried it and got to the gmail page!!! 

then it wouldn't let me access my email because my browser cookie settings aren't set correctly. i checked in firefox and my cookies are enabled. but i suspect i have to do something else about my cookies to get gmail/hotmail.

i'll search around in a firefox site, but if anybody knows anything in the meantime, i'd appreciate any help i can get

---

### Post by seshomaru samma on 2006-03-12
I think it has something to do with the settings in Firefox.
Check out edit>preferences>advanced>Validation -make sure its set to 'Do not use OCSP for cetificate validation' 
and in security 'use SSl.3.0' and 'use TLS 1.0' but not 'use SSL 2.0'
Does that help?

---

### Post by Patrissimo on 2006-03-12
no it doesn't. firefox was already set to those settings. i also get timed out trying to get to the ubuntu wiki site. can there be a connection between the two?

can any of this be due to my clock? (i'm grabbing for straws here). i live in thailand, about 7 hours off GMT.

---

