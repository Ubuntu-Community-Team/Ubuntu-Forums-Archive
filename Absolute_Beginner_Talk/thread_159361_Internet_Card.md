---
title: "Internet Card"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-04-12
I have a Linksys wireless internet card installed in the PC on which I run Ubuntu Dapper.  When I open "Networking," my card is recognized but when I click "activate" it still won't work.  I don't get any errors attempting to activate the card, but for some reason my internet won't work.  I had a similar problem in Breezy, except there my card wasn't even recognized.  I figured since Dapper recognizes the card, I'm at least one step in the right direction.  Any ideas on this?  Thanks a lot.

---

### Post by sn123 on 2006-04-12
[QUOTE=amcavoy]I have a Linksys wireless internet card installed in the PC on which I run Ubuntu Dapper.  When I open "Networking," my card is recognized but when I click "activate" it still won't work.  I don't get any errors attempting to activate the card, but for some reason my internet won't work.  I had a similar problem in Breezy, except there my card wasn't even recognized.  I figured since Dapper recognizes the card, I'm at least one step in the right direction.  Any ideas on this?  Thanks a lot.[/QUOTE]
open a terminal (Applications->Accessories->Terminal), run dhclient and post any error messages that you get.
```

$ sudo dhclient

```

S

---

### Post by amcavoy on 2006-04-12
I have attached a screenshot of my terminal.

---

### Post by amcavoy on 2006-04-12
Also, I am fairly confident that this is a problem in Dapper rather than with my wireless card.  It works fine when I boot up in Windows instead of Ubuntu, so hopefully there's a quick fix (I have yet to find one though :( ).

---

### Post by sn123 on 2006-04-12
[QUOTE=amcavoy]Also, I am fairly confident that this is a problem in Dapper rather than with my wireless card.  It works fine when I boot up in Windows instead of Ubuntu, so hopefully there's a quick fix (I have yet to find one though :( ).[/QUOTE]
Do you have the windows' drivers with you? If yes, then you might want to install ndiswrapper to get it to work on dapper, take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=81461](http://ubuntuforums.org/showthread.php?t=81461)

HTH,
S

---

