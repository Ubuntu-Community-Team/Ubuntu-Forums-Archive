---
title: "Problems - Real Player - streaming video"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-12
I have Firefox 1.5 installed and working perfectly
I also have Real Player 10 (gold) installed.
When I attempt to play streaming audio that requires Real Player (ie ram or ra) - from - for example - [http://www.bbc.co.uk/radio4](http://www.bbc.co.uk/radio4)
I get an error message :

"Could not find an appropriate hx play or real play in the system path to use as an embedded player"

This is becoming very frustrating as I go round and round trying this and that and any help would be gratefully appreciated.

---

### Post by philipacamaniac on 2006-04-12
It is caused by the Firefox 1.5 installer putting Firefox in a non-standard Debian/Ubuntu location. See this thread (the 3rd reply) for how to get it working:

[http://ubuntuforums.org/showthread.php?t=153281]("http://ubuntuforums.org/showthread.php?t=153281")

EDIT: In Dapper, which has Firefox 1.5 installed in the correct /usr/bin/firefox (and settings in /usr/lib/mozilla), installing RealPlayer 10 and using it as a plugin should work without hassle.

---

