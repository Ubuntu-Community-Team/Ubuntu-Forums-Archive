---
title: "Trying to slim-line my HP nc8000 running on Gutsy"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-11-15
Hey folks. I'm having a hard time figuring out why my system is lagging so much. I'm typing this and then  watching it come up on the screen a minute later. 
I've tried removing a lot of useless packages, and nothing seems to work in that regard. I'm looking at Top right now, and it shows me that Xorg is running very lightly, as it should. Java is taking up 21% of my mem, and Firefox is taking 12%, and the rest looks about right. When I ran this machine with Feisty and Edgy and Dapper, everything waws lovely. Everything is peachy with Gutsy also, but the speed of things is horrendous. The CPU itself is fine, I believe. It's just that it takes so long for things to type, and load. 
I'm hearing different things from different people, so I thought I would start my own thread and see for myself. Some people say disable Tracker and some people say it's Mozilla.till others say that it's just that I run with HP. HP isn't the problem, I believe. Everything "works" It's just dirty-slow. I want this fixed ASAP. Any thoughts?

---

### Post by Arthur Archnix on 2007-11-17
It's not HP. That much is clear. Was this an upgrade or a clean install? Is it just typing that you're noticing problems? Any other strange behaviour? 

I'd have two questions at this point:

1. Is the correct driver being used for my video card?
2. Is the computer running very hot, or is the fan very loud?

One thing you might try is posting the output of dmesg to see if we can spot any errors.

---

