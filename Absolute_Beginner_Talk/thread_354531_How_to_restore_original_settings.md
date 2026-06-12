---
title: "How to restore original settings"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by iiker on 2007-02-06
I need to restore my ubuntu 6.06 as if it's been just installed (i have some problems and i need default settings), but i have no idea how to do this. I don't want to reinstall, just restore.
Thanks!

---

### Post by lapsey on 2007-02-06
a quick way of getting all fresh settings would be to create a new user account (sudo adduser). to remove a user account, use 'sudo deluser'

if you have done some fiddling with your installation outside of the norm, and if you cannot specifically reverse the things you did, you will have to reinstall to get an 'install fresh system'.

---

### Post by iiker on 2007-02-06
for example i have problem installing downloaded packages. (i'm really new in linux) i made some changes with what a package should open, and now i can't install things with default package installer (and i really would like to do that). maybe it's possible to make some changes to change default open settings back?
and does creating a new user and deleting old one effects root settings? if not then i don't think it'll help.

---

### Post by lapsey on 2007-02-06
If that is the problem then it's probably best to open a thread specifically about that, along with details of what you did in the first place and what happens when something does not work. 
The more we know.. :)

And no, that's a root-level change it seems, so new users would experience the same issue.

---

