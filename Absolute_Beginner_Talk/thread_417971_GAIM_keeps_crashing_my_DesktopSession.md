---
title: "GAIM keeps crashing my Desktop/Session"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-04-22
Hi Guys,

I installed Feisty(i386) a day or two ago, and more or less everything's been fine, even GAIM. But yesterday for no reason, my desktop just crashed, and the mouse/keyboard wouldn't respond, not even to ctrl+alt+backspace.

After poking around a bit, I traced the problem to GAIM, it kept prompting me for some error. Something along the lines of a problem synchronizing contacts with the server. kept saying something like "xxx@hotmail.com" is not on your contacts list on the server.

The point is that  [email]xxx@hotmail.com[/email] is an existing contact. And i think its prompting me for every contact in my contact list, but I can't determine that, cause the moment that pop up comes up, the computer slows to a crawl, and if I ctrl+alt+backspace immediately, I can go back to the login screen, if I wait a couple more seconds, the whole thing just freezes up :(

Any suggestions on how to determine whats causing this, or how to fix it guys? Cause I really miss chatting to me friends, lol :p

Cheers,
Kinson

---

### Post by SOULRiDER on 2007-04-22
Try purging GAIM and reinstalling.

```
 sudo aptitude update
sudo aptitude purge gaim
sudo aptitude install gaim
```

There may still be some files in your come dir after purging so i suggest you look for any gaim config files.

---

### Post by kinson on 2007-04-22
Thanks. It seemed to work (so far :p ).

I dunno why my mind switches off sometimes, and I don't think of this. Owells....I guess its just getting used to Linux :)

thanks again :) ...Kopete was beginning to irritate me, haha.

Cheers,
Kinson

---

