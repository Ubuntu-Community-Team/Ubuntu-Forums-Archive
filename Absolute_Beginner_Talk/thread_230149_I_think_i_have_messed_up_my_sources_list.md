---
title: "I think i have messed up my sources list"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-05
I removed all the # marks from the univers and multiverse lines in /etc/apt/sources.list and when i want to sudo apt-get update it says
E: type 'uncomment' is not known on line 9 in sources list etc/apt/sources.list

---

### Post by _simon_ on 2006-08-05
so what does line 9 of your sources list look like?

---

### Post by steve.horsley on 2006-08-05
Whoops!

It's only the lines that begin with the word **deb** that you should remove the # signs from. Re-edit and insert a # in front of any lines that don't start with the word deb.

---

### Post by robins_web on 2006-08-05
You *did* make a back-up copy of your [FONT="Courier New"]/etc/apt/sources.list[/FONT] before mucking about with it, didn't you?

No? Shame on you! It's always a good idea to back up system files before messing with them.

Next time: [FONT="Courier New"]sudo cp sources.list sources.list.bak[/FONT]

As your mother once told you, "You'll thank me for this later." :p

---

### Post by Jagot on 2006-08-05
If you want a ready made sources.list that you can copy over to yours then use this:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by lamego on 2006-08-05
There is a nice page which allows you to generate a new sources.lst :
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

