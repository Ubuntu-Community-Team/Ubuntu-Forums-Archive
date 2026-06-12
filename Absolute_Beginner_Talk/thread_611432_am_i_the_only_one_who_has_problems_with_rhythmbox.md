---
title: "am i the only one who has problems with rhythmbox?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by creperum on 2007-11-12
Okay, am I the only one who has problems with rhythmbox?

I used to use it fine, but it stopped working, oh, ages ago.  The not-working has lasted through two upgrades and at least a year.  Judging by the form, other people are using it, so it must work at least some of the time.

I can sort music, make playlists, and everything -- everything except actually play a song.  If you hit the "Play" button, it thinks for several long seconds, then the window completely disappears.  I get an error message:

[INDENT](rhythmbox:7259): Rhythmbox-WARNING **: Couldn't find an x overlay

[1]+  Segmentation fault      (core dumped) rhythmbox
[/INDENT]
if it's running from the command line.

Any suggestions?

---

### Post by Hospadar on 2007-11-12
have you tried purging it and re-installing?
```
sudo apt-get remove --purge rhythmbox
rm -rf ~/.gnome2/rhythmbox
sudo apt-get install rhythmbox
```If that's not working, have you tried other players like banshee or amarok (which most consider to be more full-featured anyways)?

---

### Post by ohjeez99 on 2007-11-12
well if you want the easy cop out, i quit using rythembox becasue i didnt like it, and just switched to amarok, which is way better in my opinion.  Idk how to fix the problem listed but i just switched when i encountered problems.

---

### Post by Frak on 2007-11-12
Just stop using rhythmbox and use Banshee or Amarok instead; rhythmbox is a bad media app IMHO.

---

### Post by creperum on 2007-11-13
Aha!

I was wondering if there was some better app that I should be using.  Thanks a bunch -- I'll try one of those.

---

### Post by white_sox_fan_82 on 2007-11-13
I'm with the above two posts.  I tried using Rhythmbox and had the same issues as you have.  I've found Amarok to be a good iTunes replacement.

---

