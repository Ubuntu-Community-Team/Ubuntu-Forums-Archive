---
title: "Compiz-Fusion, Emerald and Avant Windows Navigator... Erratic Behavior! Please help?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by clickboom on 2007-08-09
Hi!

I'm a recent convert to Ubuntu. Coming from Windoze, I am still learning. However, I'm so happy that I made the right decision.  Having a super-fast OS compared to the clunky XP has given a new life to my 8 year old Tecra laptop. Thanks Ubuntu community!

So I just re-vamped my desktop following some good posts about compiz-fusion. I have a couple of questions for which I haven't been able to find an answer in the forums. Here goes:

1) I am running Emerald Theme Manager. However, the top panel NEVER changes color (or appearance for that matter) when i change a theme from Emerald. It remains in the theme set by the default theme manager program (System>Preferences>Themes). It should right? And if it normally does then what is wrong with mine? (I have the "Use System theme" enabled in the properties).

2) How come the Avant Windows Navigator is so unreliable? I have auto-hide enabled and the thing **sometimes** gets stuck and doesn't come out. No amount of restarting the program helps and I always end up restarting the OS to fix the nuisance.

Thanks and regards.

P.S. Girlfriend is so jealous of the ubuntu awesomeness! and she just got a Vista equipped HP Dv6500t!

---

### Post by DSn0wMan on 2007-08-10
The command to run compiz fusion with emerald should look something like this ```
compiz --replace -c emarald & 
```

I am not sure about AWN that thing allways craps out on me too.

---

### Post by mcduck on 2007-08-10
> **clickboom said:**
> Hi!

I'm a recent convert to Ubuntu. Coming from Windoze, I am still learning. However, I'm so happy that I made the right decision.  Having a super-fast OS compared to the clunky XP has given a new life to my 8 year old Tecra laptop. Thanks Ubuntu community!

So I just re-vamped my desktop following some good posts about compiz-fusion. I have a couple of questions for which I haven't been able to find an answer in the forums. Here goes:

1) I am running Emerald Theme Manager. However, the top panel NEVER changes color (or appearance for that matter) when i change a theme from Emerald. It remains in the theme set by the default theme manager program (System>Preferences>Themes). It should right? And if it normally does then what is wrong with mine? (I have the "Use System theme" enabled in the properties).

2) How come the Avant Windows Navigator is so unreliable? I have auto-hide enabled and the thing **sometimes** gets stuck and doesn't come out. No amount of restarting the program helps and I always end up restarting the OS to fix the nuisance.

Thanks and regards.

P.S. Girlfriend is so jealous of the ubuntu awesomeness! and she just got a Vista equipped HP Dv6500t!

1. Are you talking about Gnome Panel, or window titlebar? Compiz/Beryl/Emerald only affects window frames & titlebars, panels are still controlled by your GTK theme. If you want nice loking panels try using some picture as panel background.

2. AWN is still not finished software, so I'd say some problems and certain unstability are just normal. But you still don't need to restart the computer, even in the worst case restarting X should fix it (Ctrl-Alt-Backspace).

---

### Post by clickboom on 2007-08-10
Thanks for the quick replies!

Mcduck,

You are absolutely right. I was actually referring to the Gnome panel and it is indeed controlled by the GTK theme manager.

As for AWN, the more I read about it on various forums the more I learn that it is in fact a WIP. Anyhow, AWN is really very awesome... and so is the whole Compiz-fusion setup.

Regards

---

