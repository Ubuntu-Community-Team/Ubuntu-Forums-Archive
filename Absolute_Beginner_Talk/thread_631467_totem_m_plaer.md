---
title: "totem m plaer"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by watkinsted on 2007-12-04
How do i remove totem movie player from my system? When I try to do it through add/remove it says to go to advanced, i don't want to mess it up lol help plz

---

### Post by sethvath on 2007-12-04
Do you want to replace it with totem-xine? If so issue the following commands in terminal
sudo aptitude install totem-xine
this will remove totem movie player with gstreamer backend and replace it with xine. 

Alternatively you can use System>Adminstration>Sypnatic Package Manager to remove it.

---

