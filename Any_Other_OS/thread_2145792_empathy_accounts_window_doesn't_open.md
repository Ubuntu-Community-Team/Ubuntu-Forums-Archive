---
title: "empathy accounts window doesn't open"
date: 2013-05-16
forum: Any Other OS
---

### Post by terry_gardener on 2013-05-16
when i open empathy and click accounts it flashes up and then closes straight away.

this started to happen when i removed the account for connect to local people.

i have tried reinstalling empathy and telepathy-mission-control

any ideas. 

i use nvidia gtx460 with non free driver 
gnome 3.8.2 + gnome shell 
Linux manjaro 3.9.2-1

---

### Post by terry_gardener on 2013-05-16
i have just figured out why this happens. it is the google online account that causes it.

goto the online accounts within gnome settings and turn of the chat function within the list.

then you will be able to go into the accounts tab again within empathy.

the why it happens is when the google chat is connected and you click on it within the empathy accounts screen in closes the window, so when you remove the account to connect to local people the google account goes to the top of the list and when open the empathy accounts window it is auto selected by default which closes the empathy accounts window.

so disable the chat function or remove the account it solves the problem.

hope this makes sense

---

