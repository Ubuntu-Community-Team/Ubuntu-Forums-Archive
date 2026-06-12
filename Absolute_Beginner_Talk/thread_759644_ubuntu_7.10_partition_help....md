---
title: "ubuntu 7.10 partition help..."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by stylechild on 2008-04-19
hey hey guys an gals..

i need your wisdom..

i have the ubuntu live 7.10

its awsome, decided to ditch xp for it :)
an never using linux before im having a few problems..

i dont understand the partitioner
an im ripping my hair out lol
 
heres what i want..

my lappy has 40gig..
i want 5gig for ubuntu
1 gig swap
then 2 17gig for my junk..

ive reloaded millions of times now. tryin diferent options but cant 
quite get it to work..
ive just gone to manual an set up system 5gig
an got my self in the systems folder 2 17 gig folders :confused:

how can i tell the partitioner i want linux on the 5 gig
an then the 2 useable drives..that are picked up as drives..


ill share :popcorn: with ya, for the help..

---

### Post by TeoBigusGeekus on 2008-04-19
To tell partitioner to use the 5gigs as the main Ubuntu partition you need to specify its mount point as
/
Tell it also to use the one 17gig partition as your home folder. Mount point
/home

It's always good to have a separate home partition in case of a system upgrade.

As for the other 17gig partition, leave it as it is - Ubuntu will recognise it as free space and you will be able to store whatever data you need.

---

### Post by stylechild on 2008-04-19
ill give that a bash..

thats pretty much the only option i havent tried lol

thank u

:)

---

### Post by stylechild on 2008-04-19
well that didnt go to plans..
it did set up 5gig for ubuntu
5gig /home
1 gig swap..

but the remainder was dead space.. perhaps i forgot to mount it.. hmm
anyway

just got the gnome partition editor an set it up..
so at least its useable...


i like how this is sooo much quicker than any windows product..

anyways, im off to smoke an play..

---

