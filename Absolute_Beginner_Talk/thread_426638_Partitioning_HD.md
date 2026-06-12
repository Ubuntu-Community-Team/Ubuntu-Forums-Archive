---
title: "Partitioning HD"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by parradux on 2007-04-28
I know how to partition ubuntu, however, I was wondering what is the best way to set up the drive? I know some of the basic guidelines that swap needs twice your amount of ram, etc. 

How would one partition a 40 gig hard drive to obtain the most use?

---

### Post by Metacarpal on 2007-04-28
I'd suggest giving Ubuntu at least 10GB of breathing room in the root ( / ) directory.  That should be plenty for most stuff you'll want to install.  Unless you're a hard-core gamer and don't want all of your games installed in /home.  If you're going to install tons and tons of stuff, give it more space.

/home can have almost all the rest - especially if you're going to be storing your lifetime mp3 collection there.

The swap = 2xRAM is a good rule of thumb, unless your system has 1GB of RAM or more.  If you have upwards of a Gig of RAM, and you're not going to do a lot of heavy audio/video post-processing, you're really not going to need 2GB of swap space.  It's a waste of storage.  I'd say that regardless of your system (again, unless you're a major video editor), having more than 750MB of swap space is a waste.

This is all assuming a clean install of Ubuntu, not dual-booting to Windows.

---

### Post by [S|G] on 2007-04-28
I would recommend leaving about 4-8 gigs for the system root ( / ), twice your RAM (to the limit of 1 gig, I personally have 1gig of ram + 512mb of swap and never even used that swap) and the rest of the space to your /home partition.

---

### Post by nickpaton on 2007-04-28
Hav e a look at [this article]("http://www.psychocats.net/ubuntu/partitioning") on the excellent Psychocats website.

---

### Post by parradux on 2007-04-28
I dont need anything for boot?

So just: 

/swap - 2gigs 
/root  - 10 
/home -  rest

---

### Post by Bachstelze on 2007-04-28
The best way is the one that suits your neeeds. This will work fine for a basic desktop install, though.

---

