---
title: "A Wiki Setup"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Blue Dwarf on 2007-10-07
I would like to set up a Wiki for limited public use. I have an AMD 64 computer and Ubuntu running like a dream. I have read some most of the help stuff on setting up a Wiki but as a complete novice I cannot make head or tail of it. 

Many of the things that are written do not seem to relate to my setup. Along with this it also seems to assume some knowledge of Python and Apache which I have none of. I am willing to learn but have no idea of how it all fits together. I assume that those that do know how this works were at some stage in the same position.

Can anyone give me a start please?

---

### Post by n3tfury on 2007-10-07
take a look [[COLOR="DarkOrange"]here[/COLOR]]("http://en.wikipedia.org/wiki/List_of_wiki_farms").  you should find what you need.

---

### Post by frup on 2007-10-07
If you want it set up on your own computer first you need to install Apache Mysql and PHP.

Then you move to /var/www, this will be owned by root so chown it or symlink it to home or something, hopefully someone else will offer the best solution for this because I don't know.

Then install the wiki, this is easy if you have ever set up any scripts before but first you need to set up a mysql user and password which is a little tricky (This is all well documented in these forums)

Once the wiki is setup anyone on your home network will be able to access the wiki through [http://your_internal_ip/](http://your_internal_ip/) if you have the wiki as your sites index. also [http://name_of_your_computer/](http://name_of_your_computer/) should work.

on your computer you can access it as [http://127.0.0.1](http://127.0.0.1) or [http://localhost/](http://localhost/)

If you want to have this available over the internet you need to allow port 80 in your router to have external access and forward that to your internal ip, make sure you read some of the security threads too etc,etc.

If you need more help please ask a more specific question :)

---

