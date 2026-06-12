---
title: "VCD help"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by zgrw on 2007-02-22
I can't play vcd discs, totem says something like that "the source file couldn't readed" (i can't remember the exact sentence). How can i play vcd discs?

---

### Post by netkid91 on 2007-02-22
You are missing necessary GStreamer codecs, open a terminal and type:
sudo apt-get install gstreamer0.10*
It will ask for your password, type it in, this will install codecs for just about any media format out there, including VCD's (not DVD's though, that requires some separate libraries)

---

### Post by zgrw on 2007-02-22
tahnks for your help but still it doesn't work :(
now, it says "No URI handler implemented for "vcd"." :)

---

### Post by netkid91 on 2007-02-22
Do you have the Universe and Multiverse repo's enable (System->Administration->Software Sources)?

---

### Post by zgrw on 2007-02-22
I had universe but not multiverse. I have selected multiverse now.
Should I execute same command again?

---

### Post by netkid91 on 2007-02-22
Yes, select multiverse and run it again.  Multiverse contains thing that have potential legal issues (such as copyright violations), which the MPEG codecs fall in (and VCD's use MPEG 1 or 2 encoding).

---

### Post by zgrw on 2007-02-22
Still it doesn't work. It says same thing :(

---

### Post by netkid91 on 2007-02-22
Odd.....I'm not an expert with GStreamer/Totem, so I'll need to do some more research.  I need to go do something for a few hours, so I'll help you as soon as I can if no one else does.

---

### Post by zgrw on 2007-02-22
Ok, thanks for your help :) I have searched on google and I have tried something but I couldn't be succesful :)

---

### Post by zmr on 2007-03-08
I am basically having the same problem as zgrw. I am using vcds made in China, not sure that really makes any difference...

---

### Post by wunian on 2007-05-07
I am having the same problem. The video cd that I used to auto-run under Windows could not even be detected at my cdrom. I think this is one of the issues that make the Windows user shy away from Linux!!! Real help is needed.

---

### Post by zmr on 2007-05-07
As a related anecdote, I live with a bunch of Tibetan monks in rural TIbet/China. We're working on computers on an archival project. The systems they have use a "non-genuine" version of Windows XP (like most versions of XP in China) that are virus prone and difficult to get updates for. I'd like to switch some of the computers to Ubuntu to make management easier but the monks REALLY like to watch VCDs. Living in a small rural village all their lives, VCDs are a window to the larger world outside. I couldn't take them away from that! So, yes, I'd entirely agree that better support for VCD content is an obstacle to leaving Windows. Perhaps there's a work-around? Anyone suggestions out there?

---

