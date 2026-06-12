---
title: "Help with partitioning!"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Dieselguts on 2008-02-23
i am a total ubuntu noob and i need help with the installation!
i have got to the partitioning section and i don't really understand any of it! I have Vista Ultimate installed on my hard drive and about 55% of the hard drive is taken up. If someone could just walk me through it that would be a great help

---

### Post by taurus on 2008-02-23
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Dieselguts on 2008-02-23
it's really annoying because it only ahs 2 options

Guided use entire disk
&
Manual

I want to choose how much with that sliding bar but it isn't there

---

### Post by (((X))) on 2008-02-23
Choose manual:)(blue pill)
Merge vista if there is a need to do that.
Create / and swap, if you would like to have home on separate partition create third one /home and format them in ext3.

---

### Post by rolnics on 2008-02-23
As the previous have said go manual! 

As already suggested you need a / (root) partition make it about 10Gb, swap partition about 3gb and the rest as a /home partition.

---

### Post by candtalan on 2008-02-23
because you were not offered any other choice but whole disc or manual i conclude there is something about your HD which prevents easy resizing. I had a case like that recently with win2000. 

First backup any data you dont want to loose, because you might loose it....
I suggest doing partitoning before using the install CD in this case. Shrink vista, create a 1GB partition for swap, and have the remainder as ext3 for /  (that is system).

Then when you choose manual install it will be easier to decide what to allocate and where

good luck

---

