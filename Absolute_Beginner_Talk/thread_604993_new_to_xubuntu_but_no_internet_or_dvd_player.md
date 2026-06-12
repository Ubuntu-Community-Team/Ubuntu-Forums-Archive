---
title: "new to xubuntu but no internet or dvd player"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by bevicruising on 2007-11-06
Hi, just installed xubuntu 7:10.  can't get dvd player to work and can't connect to internet.  Have plugged my ASUS wl-167G wifi adapter in and it picks up hotspots but won't connect.  Any ideas please. Jan:confused:

---

### Post by mivo on 2007-11-06
The DVD playback problem is easy to solve:

[LIST]
[*]Install the **totem-xine** package from the repository (*System -> Administration -> Synaptic*).
[*]Add the Medibuntu repository as explained [here]("https://help.ubuntu.com/community/Medibuntu") (read the "Adding the Repositories" section).
[*]Install the **libdvdcss2** package.
[/LIST]

And that's all! :)

---

### Post by mivo on 2007-11-06
Oh, I see that you use Xubuntu! Synaptic may be in a different location, but it should be close. There are also other media players available that should work. I just happen to like the Xine-version of Totem. :) It is small, fast, easy to use, and it supports DVD menus and such. There may be other lightweight media players with DVD support, too. (Totem-xine only uses 40 MB RAM while playing Fellowship of the Ring in 1680x1050 fullscreen.)

---

### Post by Grafster on 2007-11-16
Wireless has taken a step backward in Gusty. You're going to need to identify your card and run some diagnostics to get started.

There are (lots) of threads about it in the wireless forum.

---

