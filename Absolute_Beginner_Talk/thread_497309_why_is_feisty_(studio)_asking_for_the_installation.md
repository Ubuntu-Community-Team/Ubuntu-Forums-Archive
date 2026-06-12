---
title: "why is feisty (studio) asking for the installation cd on synaptic?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by sameoldude on 2007-07-10
ok, so i'm on studio, i added a bunch of packages to pimp my ubuntu experience but once i clicked on apply (on synaptic) it asked me to insert the cd. i cancelled that and poof, no installations. i then put the cd in and no problemo. my cd-dvd drive is really messed up and most of the time it won't read (burning is out of the question) so pretty much rite now i have to try and retry until the cd is loaded.
what the raddish? how do i tell ubuntu it don't want it to ask me that stool? :confused:

---

### Post by clitmaster on 2007-07-10
go to System > Admin > software sources .... then untick CD drive in there

---

### Post by RomeReactor on 2007-07-10
Hi. That's probably because you have the Installation CD as part of the repositories (meaning Synaptic will ask you to insert the CD instead of searching the on-line repositories for certain packages). To remove the CD from the available repositories, open Synaptic and go to "Settings->Repositories" and un-check the CD form the box below. Next click the blue **Reload** button (or enter **sudo apt-get update** in the terminal) to bring the repositories up to date.

---

### Post by sameoldude on 2007-07-10
thank you, i no longer have this problem

---

