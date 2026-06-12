---
title: "Automatic Updates Won't stay checked?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-13
For some reason my update-manager icon disappeared, I tried making it come back by checking updates automatically but when i close the window it un-ticks itself :(. ANyone got a solution?

---

### Post by bapoumba on 2007-01-13
hello,
just run **sudo apt-get update** or **sudo aptitude update** from a terminal. If updates are available, update-manager icon should show up.

If running GNOME, go to > System > Preferences > Sessions > Startup Program tab. update-notifier should be there, first position.

---

### Post by rj686 on 2007-01-13
It is there in start up programs, but for some odd reason when ever i check automatic updates in software sources it's automatically unchecked :(

---

