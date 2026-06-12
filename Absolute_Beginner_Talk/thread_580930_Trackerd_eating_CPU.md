---
title: "Trackerd eating CPU"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by DCboi on 2007-10-19
Hello,

I upgraded my OS from Festy to Gutsy today and now a process called "trackerd" is consuming fair share of my CPU. Is it a bug ? Is there anything that can be done to prevent it ?

---

### Post by mivo on 2007-10-19
It is a file indexer, and theoretically it should only put stress on your system in the first few minutes after starting the computer. You should be able to turn it off, though.I don't have a Gutsy install here right now, but there should be a "Sevices" option in System -> Administration where you can toggle it.

---

### Post by Paqman on 2007-10-19
It'll calm down eventually. It's just chewing a lot of CPU because it's new and is building up it's index. Once it's done that'll you'll be able to use it to do lightning fast searches of your system. It integrates into the deskbar applet really well.

Beagle is another alternative that does the same thing.

---

### Post by davidshere on 2007-10-19
I'm also seeing this problem.  Hopefully it will go away.

---

### Post by Steveway on 2007-10-19
Again, this is no problem nor a bug.
It indexes your whole Pc and this takes up a lot of CPU-time.
It will calm down if it has indexed everything.
That's perfectly normal, it's not like it is as heavy as Vista's indexer.
And I wouldn't recommend Beagle, it uses Mono, wich makes it much slower, tracker is a wise choice.

---

### Post by glotz on 2007-10-19
Give it a lower priority or disable it if you don't need it.

---

### Post by FredB on 2007-10-19
> **DCboi said:**
> Hello,

I upgraded my OS from Festy to Gutsy today and now a process called "trackerd" is consuming fair share of my CPU. Is it a bug ? Is there anything that can be done to prevent it ?

Trackerd is the daemon of tracker, a file indexer lighter - not really difficult - than Beagle.

[http://www.gnome.org/projects/tracker/](http://www.gnome.org/projects/tracker/)

First indexing will take about 10 to 20 minutes. After it, it will index from time to time.

And you can tweak it using Indexation preferences in system / preferences menu.

---

### Post by DCboi on 2007-10-19
Thanks for all the reply. I've killed the process for the time being as it was interfering with my routine work. It would have been better to give a low prio for such process by default so that it doesn't hinder the performance, especially on low end hardwares.

---

