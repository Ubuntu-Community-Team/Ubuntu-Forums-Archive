---
title: "Automatic gamma correction + problem with &quot;~&quot;-key"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2006-04-21
My old CRT-screen is broken, so I have to manually adjust the gamma. In linux, I'm able to do this with "xgamma -gamma 1.7". How can I make Ubuntu do this on startup?

Second, I have some problems with the "~"-key, it won't work most of the time and gives a loud computer-beep. Speaking of beeps, is it possible to disable those beeps, replacing them by actual speaker sounds? I get those loud beeps even when backspacing in an empty textbox. :/

Tnx in advance,

---

### Post by unnes on 2006-05-01
Bump, I have to adjust the gamma every time I start up Ubuntu as well (I also have a crappy CRT). While it's not a huge issue to go to the terminal and change it, it would be more convenient to have it done automatically at startup.

---

### Post by unnes on 2006-05-01
Literally 5 minutes after I posted my bump, I found the answer:

Go to the System -> Preferences -> Sessions

Under the Startup Programs Tab -> Add/Edit/Delete, add "xgamma -gamma 1.7"

That should do it!

---

