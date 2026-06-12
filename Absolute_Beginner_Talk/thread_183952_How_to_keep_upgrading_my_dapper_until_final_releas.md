---
title: "How to keep upgrading my dapper until final release?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by guitarded on 2006-05-29
i upgraded my breezy to dapper release candidate a few days ago.  what do i need to do to keep up my dapper up to and including dapper final?  do i just sudo apt-get update daily?  do i sudo apt-get dist-upgrade when the final release comes out (or do i use sudo apt-get upgrade at this point on?  i just want to make sure i follow the correct procedures to ensure that i get the final version when it is released.

---

### Post by nanotube on 2006-05-29
update just brings the repo indexes up to date. upgrade is what actually upgrades stuff. dist-upgrade is kinda a more thorough upgrade (upgrades dependencies and things). 
if you jsut keep upgrading, you will get the dapper release when it's out.

---

### Post by morgs on 2006-05-29
[QUOTE=nanotube]update just brings the repo indexes up to date. upgrade is what actually upgrades stuff. dist-upgrade is kinda a more thorough upgrade (upgrades dependencies and things). 
if you jsut keep upgrading, you will get the dapper release when it's out.[/QUOTE]

If you run into bugs now and want to see if they are fixed before the release, then daily dist-upgrades are good. However there's no real need to upgrade every day. You could simply wait for the final release and do a single dist-upgrade then.

---

