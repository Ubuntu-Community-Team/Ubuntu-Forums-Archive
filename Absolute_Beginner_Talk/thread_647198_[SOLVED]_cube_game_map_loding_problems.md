---
title: "[SOLVED] cube game map loding problems"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-12-22
dont know if this is the right place to ask or not.

i have managed to install the game "cube" from the get deb web site

[http://www.getdeb.net/](http://www.getdeb.net/)


there is some games i connect to and the maps are all over the place.
 i have asked fellow players how to get the maps and i need to do a /clearsecuremap

i can do this and then they tell me i need to do a /getmap

when i do this it says it can not connect to the sever to d/l the map.

it does this in no matter what game im in.
file permissions perhaps???

any ideas?

---

### Post by stinger30au on 2007-12-22
i found the answer!!!!

after much reading. i was correct. it is to do with linux file attributes.

after assault cube is installed i fired up terminal and do this

cd usr

cd share

cd games

cd assaultcube

cd packages

 sudo chmod 777 -R maps

cd maps

 sudo chmod 777 -R *.*

now run asault cube and it will be fixed!!!


yee-haw!

---

