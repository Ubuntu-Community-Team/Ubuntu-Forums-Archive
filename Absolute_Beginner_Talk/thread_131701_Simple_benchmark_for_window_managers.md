---
title: "Simple benchmark for window managers?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by johnraff on 2006-02-16
What's a good way to easily compare the speed of window managers?
Right now I'm comparing the time Firefox takes to load up to an empty window ("about:blank").
On my (old) machine this varies from 25sec. with Gnome to 7sec. with Openbox.

Is there a better benchmark to use?

---

### Post by PhilipGanchev on 2007-03-20
There may be some automatic way to record the time that it takes to start up, but it may be better to time it manually using a stopwatch because you are interested in the user experience of seeing a window and being able to interact with it.

Perform 10 or 20 starts where you start Firefox and close it, timing each one, and take the average.  These are warm starts.  Then repeat with 10 or 20 starts of Firefox but before each one, open and close some other programs like Abiword and Gimp.  These are cold starts.  The startup speeds may differ for cold starts and warm starts.

---

