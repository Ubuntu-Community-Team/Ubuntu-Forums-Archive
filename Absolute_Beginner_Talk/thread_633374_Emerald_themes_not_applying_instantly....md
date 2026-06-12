---
title: "Emerald themes not applying instantly..."
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Sand &amp; Mercury on 2007-12-06
Greetings all, I'm four days into my Ubuntu Gutsy experience and I'm nearly ready to drop my old XP installation in favour of it. I've been having a ball with Compiz-Fusion and its bells and whistles, but I've run into an annoyance when I try to apply themes with the Emerald theme manager; Themes don't apply as soon as they're selected in the theme manager, and so far as I've figured I have to apply them by restarting emerald via the "emerald --replace" command. Is there any way to get this set up properly, so it applies themes instantly?

If its of any relevance, I possess an ATI X1300 and am rather fresh to all of this Linux insanity. Please forgive my ignorance if this has been answered elsewhere, I've looked and didn't see anything.

Cheers. :D

---

### Post by vikramsharma on 2007-12-07
I am assuming that emerald replace is not in your startup.  Goto System_>Preferences_>Sessions in Sessions look for 'Startup Programs' click on add and in the name field write down 'emerald' in the command field write 'emerald --replace' (without the quotes).  This works for me, I had problem similar to yours before and this solved it.

---

