---
title: "Show Desktop Bug"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2008-01-05
I assume I have some setting selected that I shouldn't.  When I push the show desktop button on the bottom left of my screen, I get the funky alt-tab display (only partly though) until I hit it a second time.  I have attached a screenshot to demonstrate my problem.  Any thoughts?

---

### Post by voteforpedro36 on 2008-01-05
> **brandoncolorado said:**
> I assume I have some setting selected that I shouldn't.  When I push the show desktop button on the bottom left of my screen, I get the funky alt-tab display (only partly though) until I hit it a second time.  I have attached a screenshot to demonstrate my problem.  Any thoughts?

If you remove the button from the panel and add it back in, do you have the same problem?

---

### Post by RomeReactor on 2008-01-05
Hi. Does this happen with other themes (Human, Clearlooks)? Have you made any recent changes to Compiz in 'System->Preferences->Advanced Desktop Effects Settings'?

---

### Post by brandoncolorado on 2008-01-05
> **voteforpedro36 said:**
> If you remove the button from the panel and add it back in, do you have the same problem?

Yes, same problem after doing this.

---

### Post by brandoncolorado on 2008-01-05
> **RomeReactor said:**
> Hi. Does this happen with other themes (Human, Clearlooks)? Have you made any recent changes to Compiz in 'System->Preferences->Advanced Desktop Effects Settings'?

This does happen with other themes too (I tried clearlooks, I am currently using custom).

I have made recent changes to Compiz, including these changes:
[LIST]
[*]Change on desktop cube zoom
[*]Turned off sticky windows setting in wobbly windows
[*]Changed Emerald Theme
[*]Other random things when I installed about 1 week ago.
[/LIST]

---

### Post by brandoncolorado on 2008-01-05
Also, fade to desktop plugin is installed (but not changed) and show desktop is disabled in compiz.

However, after trying the other way around, the problem still persists (with just show desktop enabled).

---

### Post by RomeReactor on 2008-01-05
If you're using the 'Custom' or 'Extra' settings in 'System->Preferences->Appearance', try going back to 'Normal' and see if the problem is still there; you can also try reverting the changes you made to Compiz and see if that is the cause. It might also be a bug in Emerald, so you could try changing to gtk-window-decorator:
```
gtk-window-decorator --replace
```

---

