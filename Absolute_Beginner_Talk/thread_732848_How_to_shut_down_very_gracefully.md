---
title: "How to shut down *very* gracefully"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Giacecco on 2008-03-23
This definitely is a thread for the "Absolute beginner talk" space.

My Ubuntu 7.10 shuts down fine, but does not close nicely the applications that are running at the time, for example Firefox, or JungleDisk Monitor, or Azureus. I realise I sound very naive, but perhaps there is a solution for this.

Any help is appreciated,

Giacecco

---

### Post by skymera on 2008-03-23
well you can close them before shutting down?

---

### Post by Giacecco on 2008-03-23
Haha thanks. Let's put it this way: if Windows can do it, Linux must do it better.

---

### Post by nick_h on 2008-03-23
Ubuntu should terminate applications at shutdown.  Firefox will give you the option to recover the previous session rather than starting a new one if you leave it running at shutdown.

---

### Post by Lacrimstein on 2008-03-23
Lol, I don't think Windows shutdowns are graceful at all... It can't even end its own system processes and you have to do it manually XD

Also I don't quite understand your problem... Could you give us more information?

---

### Post by Oldsoldier2003 on 2008-03-23
*shrugs* FF3B4 on Hardy opens up in the state you had it when you logged off. you only get the option to restore the session if you actually crash FF, and is saves tabs on closing ...YAY!

---

### Post by diablo75 on 2008-03-23
I went into my power settings and told it to shutdown (not "ask me") when I hit my power button.  System is powered down in less than 20 seconds after I hit that button, and it is as graceful as ever.  Never once has a shutdown snagged or hanged on me because a program was frozen.  I've had programs stop a shutdown because I needed to save my work to an open file, but other than that, nothing stops it from killing every process by force on its own.  Windows can't do that.  So yes: Linux does it better.

---

### Post by Giacecco on 2008-03-23
Let's talk about one application at a time, then, starting from one of the most common: Firefox. 

When X shuts down you cannot say that it does kill Firefox gracefully, otherwise we would not have the "recover session" message when starting Firefox again.

When I shut down Windows or MacOS, Firefox has no problems of this kind at all: you may not like this but it is true.

Which of the two do behaviours you call a "graceful" shut down?

G.

---

### Post by Oldsoldier2003 on 2008-03-23
> **Giacecco said:**
> Let's talk about one application at a time, then, starting from one of the most common: Firefox. 

When X shuts down you cannot say that it does kill Firefox gracefully, otherwise we would not have the "recover session" message when starting Firefox again.

When I shut down Windows or MacOS, Firefox has no problems of this kind at all: you may not like this but it is true.

Which of the two do behaviours you call a "graceful" shut down?

G.

thats a firefox issue. nautilus and tons of other apps shut down fine.  Firefox three shuts down fine. Firefox 2's linux implementation doesn't support it well.

---

### Post by ghost_ryder35 on 2008-03-23
> **Giacecco said:**
> Let's talk about one application at a time, then, starting from one of the most common: Firefox. 

When X shuts down you cannot say that it does kill Firefox gracefully, otherwise we would not have the "recover session" message when starting Firefox again.

When I shut down Windows or MacOS, Firefox has no problems of this kind at all: you may not like this but it is true.

Which of the two do behaviours you call a "graceful" shut down?

G.
I can not shutdown Firefox with tabs open in any OS.  I always get asked **"Closing now will close 3 tabs.  Do you want to continue?"**
Might want to check your FireFox settings

---

### Post by nick_h on 2008-03-23
> Which of the two do behaviours you call a "graceful" shut down?
As far as I can remember Ubuntu sends a SIGTERM signal to the application at shutdown.  Firefox handles this with no problem and remembers that it was closed because of a shutdown rather than a user closing it.

When Firefox starts again it has a choice - start a fresh session or continue the old one.   I'm not sure which option the user is most likely to want or which is the most "graceful".  It looks like the application developers even change the behaviour between versions.

---

