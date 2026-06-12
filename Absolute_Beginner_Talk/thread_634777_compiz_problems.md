---
title: "compiz problems"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by waysgoose on 2007-12-08
Hi everyone,

I am an absolute n00b, but I'm really keen to have a go at linux. I'm especially keen to get compiz up and going!

Anyway, I've got Ubuntu 7.04 installed, and it all seems to be running okay. I've installed a driver for my Radeon video card and I've downloaded updates.

I'm having problems with installing compiz. I used an install guide from the Desktop effects and customisation forum, Forlong's Blog. I've downloaded all of the packages as per the blog.

When I get to the part about configuring compiz something goes wrong. I click System, Preferences, CompizConfig Settings Manager and nothing happens. When I try to run Compiz by pressing alt-f2 and typing compiz --replace  nothing happens.

I'm not sure if this has anything to do with it, but when I run Update manager I get a message telling me
 "Error authenticating some packages-

compiz-core
compiz-gnome
compiz-plugins
libcompizconfig-backend-gconf"

I've done a bit search, but I can't find anything I can really understand.

As I say, I'm an absolute n00b at linux, but very keen to learn

All help/suggestions gratefully accepted.

Cheers,

Waysgoose :)

---

### Post by spiderbatdad on 2007-12-08
if you're running 7.04 i would highly recommend beryl over compiz. it works much better and gives you all the effects and more. i'll look for the how-to i used when i installed beryl and post back.

you can get the gist of things here:  [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

neither compiz nor beryl was included when I had fiesty, so it was necessary to add Trevino's repos to /etc/apt/sources.list

then update synaptic...then select all the packages, including emerald theme manager. Finally I had to learn how to change the windows manager from metacity to (GTK? maybe) or beryl after starting beryl. Anyway it took a bit of reading and a lot of fooling around to finally get all those cool effects going, and they were cool. I upgraded to Gutsy and got compiz going, but it was slow and jerky, seemed to use an excess of resources, no graphical settings tool for switching windows managers...in short a big let down after beryl.

---

### Post by Ub1476 on 2007-12-08
Why don't you use the latest Ubuntu which has Compiz-Fusion integrated?

---

