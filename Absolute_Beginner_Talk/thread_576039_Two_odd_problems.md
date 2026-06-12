---
title: "Two odd problems"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Spook27 on 2007-10-14
I've been searching for answers to these issues for a bit now and can't find a thing via the forums or Google in general, so here goes...

1) When I install Feisty as a command-line system, it works pretty much as expected.  However, when I install kubuntu-desktop, I can't do a console login anymore - this has been the case on three seperate installs on two machines.  How can I fix this and has it been adressed in Gutsy?

2) This problem is a little more obscure and specific...  I run a program called sound-recorder to copy raw .wav data from my line in port so that I can record a radio show that airs when I'm not home.  I have it set up on a cron job to start at midnight and terminate after 240 minutes of recording.  However, for several nights in a row it has recorded for exactly 5 minutes and 23 seconds and then come to an abrupt end.

Thanks for your time!

---

### Post by Scunizi on 2007-10-15
I'm not sure about #2 but #1 leaves me with a couple of questions.. do you mean to say that after installing kubuntu you don't have an opiton for booting directly into a console? or that you can't get to a different TTY console screen?  Typically to boot into a console mode choose rescue during the grub prompt.. If you want a different tty as opposed to opening Terminal in the gui, then CTRL+ALT+F2-6.  I hope that helps. :)

---

### Post by anaconda on 2007-10-15
If yo install other konsole programs do they work?

eg.
xterm gnome-terminal tilda

---

### Post by Spook27 on 2007-10-15
I should have specified - it's the TTY logins I can't do.  Anything else (including SSH) and I can log in fine, but the F1-F6 terminals tell my that my login is incorrect.

---

