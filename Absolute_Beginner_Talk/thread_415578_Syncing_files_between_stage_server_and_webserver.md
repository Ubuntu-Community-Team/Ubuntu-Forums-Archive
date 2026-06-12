---
title: "Syncing files between stage server and webserver"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-04-20
I have a development environment and a production environment, both machines on the same lan.  I'm looking for a sync or transfer solution to deploy updated files from the dev server to the prod server.  Both machines are standard ubuntu lamp installs.  Would anyone be familiar with a way to do this via the command line?

---

### Post by earobinson on 2007-04-20
rsync is the command you are looking for.

man rsync for more info

---

