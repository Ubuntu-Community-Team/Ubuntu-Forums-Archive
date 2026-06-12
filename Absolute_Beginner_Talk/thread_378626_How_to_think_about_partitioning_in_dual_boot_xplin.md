---
title: "How to think about partitioning in dual boot xp/linux machine?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Uridian on 2007-03-07
i'm very new to ubuntu/linux and i'm very well versed in the world of windows that i want to break out of...  anyway, i've taken the plunge and installed ubuntu and xp in a dual boot configuration, but i'm having some trouble wrapping my brain around how to organize it all.

in windows, it's all very clear to me how to organize parititions/drives, etc...  but when i introduce that logic into linux it seems to break down.

typically, i use one partition for OS (C: - 15 gigs), then one partition for swap/virtual space (D: - 3 gigs) one partition for playing around (this one turned into my linux playtime, but i'll get to that), then one partition for programs, apps and games (F: - 50 gigs), then one partition for all other data such as music, videos, in progress projects, etc... (G: - 170 gigs)

it just so happens i have another drive that thats one partition for more swap (I: - 3 gigs) and another animation only data partition (j: - 30 gigs)

so my mindset is separate partitions for system, programs, data.

how should i think about making linux work in a similar fashion, or should i even do that at all?  when i first partitioned to dual boot linux, i made an 8 gig system partition, a 1 gig swap partition and a 15 gig data/programs partition.  it appears, though, that programs get installed in the root file system and i can't write to the data partition as myself (i've been using 'sudo nautilus' to even do anything on the data partition)

should i have a much larger root linux partition to make space for all the programs i need to run and then somehow make that data partition accessible by my user and, idunno, make a link/shortcut from my user's home directory to the data drive?  or can/should i make my user home directory on the larger data drive?

i require large amounts of data/project storage as i do animation and illustration, and i'd like a way to keep all that separate from everything else somehow...


sorry for such a long first post, but thanks in advance for any help anyone can offer...

-uridian

---

### Post by gezus on 2007-03-07
By no means am I an expert user at all, but I would think for sure that you are going down the correct path.

My setup on my Linux box is similar except that I have a seperate partition for boot.

so I basically have 72gb for /
2 gb for /swap
200mb for /boot

Keep in mind that if you have for instance multiple drives that you can mount ntfs drives (windows drives) that you can store things on to keep in sync with your storage needs.

---

### Post by mikewhatever on 2007-03-07
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

