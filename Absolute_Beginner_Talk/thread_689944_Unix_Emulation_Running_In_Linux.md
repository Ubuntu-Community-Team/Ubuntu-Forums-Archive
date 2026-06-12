---
title: "Unix Emulation Running In Linux??"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by SwampDonkeyCanada on 2008-02-06
Hi.  I am a relative newbie, so please bear with me.  I did search the forums, but did not find an answer for this question.

I run a specific business program at work, which is written and runs from a SCO UNIX server.  In order for me to be able to work from home, I have been using a program called Tinyterm, running under Win XP pro,  which allows me to dial into the server, and emulates my workspace perfectly.

I assume that there are also programs in linux that would allow me to do the same.  Does anyone have or know of specific programs that are available in linux?  Are they open-source?  Are they in the current repositories, or will I have to download them?

I thank you for your time.

Linux Newb

---

### Post by jordanmthomas on 2008-02-06
How does tinyterm connect?  Is it ssh?
```
ssh username@hostname
```
in a terminal may be just what you're looking for.

forgive me if I'm way off here (got a feeling that's the case).

---

### Post by wirelessmonkey on 2008-02-07
minicom or gtkterm will probably do what you want. Just make sure to read the documentation and make sure your term connection settings are the same as you use in Tinyterm.

---

