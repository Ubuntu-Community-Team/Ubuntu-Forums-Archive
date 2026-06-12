---
title: "Kubuntu Dapper Dual Boot Partition Resize"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-05-19
I just installed Dapper on a 10 Gb Partition, all went lovely.
I,ve got Kubuntu on the other partition and it has 30 Gb of free space.
What's the easiest way to resize the partitions so that I can steal 20 Gb more for Dapper ?
It's Like this:-
Mbr 10 g Dapper |70 g Kubuntu | Swap |

I want to :-
Mbr 30 g Dapper |40 g Kubuntu | Swap |

Is this possible? I need some more space to play with Dapper without changing the Kubuntu setup.

Any help would be apreciated
Thanks

---

### Post by richbarna on 2006-05-19
Just wanted to add that I have read the other posts, and I remember aysiu saying that you can add space at the end but not at the beginning of a partition.
The actual thing is, I could wipe kubuntu after backing up 30 gig of files, redoing favorites, saved logins, emails, server settings etc., and installing Dapper on the WHOLE drive, but I,m trying to avoid starting from scratch again.

---

### Post by slimdog360 on 2006-05-19
You can just install the kde desktop from within synaptic and get kubuntu and dapper on the same partion. When you go to login you select options or something (I cant remember what its called) then fromthere you can select to boot into  kubuntu(KDE) or dapper

---

### Post by richbarna on 2006-05-19
Thanks for the reply, but I haven't got a problem with the KDE desktops, I just need to make the Dapper Partition bigger, and the Kubuntu partition smaller.

---

### Post by slimdog360 on 2006-05-19
oh sorry, i didnt read all of the second post.

---

### Post by aysiu on 2006-05-19
Why don't use use PartImage? Make a copy of the partitions, repartition and resize as you like, then restore the images?

The images are of the partition space that's used, not the entire *empty* partition.

For example, I did a partition image of my Xubuntu partition. It's a 10 GB partition, but only 2 GB of it is used. The image was only 2 GB.

You can also compress the image, too.

---

### Post by richbarna on 2006-05-20
Cheers aysiu,
I will remember that for future reference.
Last night I backed up everything I had, and wiped the whole disc and did an install and upgrade following your instructions from a previous post.
I am now the proud owner of a fresh, windows free system running Dapper.
Everything went smooth as a babies bum.
Thanks :)

---

