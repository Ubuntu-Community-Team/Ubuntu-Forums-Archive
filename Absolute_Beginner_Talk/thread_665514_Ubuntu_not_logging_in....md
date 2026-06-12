---
title: "Ubuntu not logging in..."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by DecemberWinds on 2008-01-12
I've installed 7.1 gutsy on my laptop dual booted with XP.

On my first logging in everything worked fine and so I installed the updates. But it stopped during the installation of this one update (it was almost finished too). And my computer froze, so I had to force shutdown (hold down the power button). Now when I log in the screen goes black, and the cursor displays an X momentarily and then turns into a normal cursor. And it just sits there.

When I press ctrl alt f1 or f2 I get this thing similar to terminal, but I cannot get my desktop to display.

Also when I press the power button in this terminal type thing it shows all this text and then it just stays at "will now halt...". 

Any help will be appreciated!

---

### Post by PmDematagoda on 2008-01-12
Boot Ubuntu in Recovery Mode, then enter:-
```
dpkg --configure -a
```
after that is done, enter:-
```
startx
```

---

### Post by DecemberWinds on 2008-01-12
Well now i have a desktop! THank you very much! HOwever i'm logged in as a "priveleged user"? and its not suggested?

So basically I'm running in recovery mode right now? If i were to reboot and boot up in normal ubuntu would it work?

THanks a lot! :)

---

### Post by PmDematagoda on 2008-01-12
Yes, it would. Just execute:-
```
reboot
```
and that should do:).

---

