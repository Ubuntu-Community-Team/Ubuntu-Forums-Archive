---
title: "Wine"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-16
hey guys, I seem to be having trouble with wine. I installed it through automatix but now I can't get it going.

---

### Post by chuckyp on 2006-10-16
Automatix is not officially supported and there are many reasons why NOT to use it.  

For instance why didn't you just install wine from the repos? 

sudo aptitude install wine

Would have worked just fine.

---

### Post by familyjules74123 on 2006-10-16
so should I uninstall it and reinstall it using the repos?

---

### Post by chuckyp on 2006-10-16
Well that is completely up to you.  But what do you mean by I can't get it going?


i.e. What is happening exactly?

---

### Post by familyjules74123 on 2006-10-16
Well I installed it, but now I can't find it on my computer and therefore can't run it.

---

### Post by chuckyp on 2006-10-16
Well wine does not have a gui interface installed by default.  So to run wine you would type in a terminal window "wine nameofprogram.exe"   To run the windows program.  You may want to search for some howto's on wine to get the general idea.

i.e.  "wine calc.exe"   "wine Steam.exe"   etc....

Hopefully you understand.

---

### Post by familyjules74123 on 2006-10-16
hmm, I think that helps me out. I'll post back here if I screw up.

---

### Post by arochester on 2006-10-16
I found [http://frankscorner.org/](http://frankscorner.org/) very helpful with Wine

---

### Post by 3rdalbum on 2006-10-16
Automatix adds the official Wine repository to the sources.list, so you get a more up-to-date version of Wine than you would from the normal Ubuntu repository. The latest Wine has much better support for some programs than the stock Ubuntu one.

---

### Post by familyjules74123 on 2006-10-16
alright I think I'm good with that.  But if anyone knows how to get the game counterstrike to work using WINE and could help be I would be most grateful.

---

### Post by bodhi.zazen on 2006-10-16
Go to [[color=darkred]WineHQ AppDB[/color]](http://appdb.winehq.org/), enter your game in the gray search box on the Left.

---

