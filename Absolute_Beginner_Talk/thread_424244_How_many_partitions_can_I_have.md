---
title: "How many partitions can I have?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-26
Going to install Ubuntu tonight.  Here is what I have so far:

C:\ Vista (Primary)
E:\ Programs (Primary)
 :\ Media Direct (Logical Drive)

I'd like to add a partition for Music first, then leave 10GB for Ubuntu.  Will it let ma have that many?  I'd like this final setup:

C:\ Vista (Primary)
E:\ Programs (Primary)
M:\Music
 :\Ubuntu
  -Ubuntu Swap
 :\ Media Direct (Logical Drive)

I know Windows likes only 4, but I've seen more before when also booting Linux, so hopefully I can have these 6 with no ill effects.  Any issues you all can see?

---

### Post by indytim on 2007-04-26
I believe you will need to create an "extended" partition for all unallocated space beyond your 3 partitions.  Once that is done, they you can carve up as you need to (within the extended partition) to support your new install of Ubuntu.  My recommendation is to pre-configure your partitions with GParted Live before doing the installation.  Then pick the manual setup in the installer to put things where you want them to be.

Hope this helps,

IndyTim

---

### Post by gohanssjn on 2007-04-26
Hmm, and by extended, you mean a logical one, right?  Because, unfortunately, MediaDirect uses that type of partition; so I can't creat a second one.  Or am I wong on this and there is a way outside of Vista?

---

### Post by st33med on 2007-04-26
You can create exactly 4 partitions, but you can have an extended partition with, I think, infinite amounts of logical partitions (as long as it fits, however). There is a thing in which you can have as many as 50 partitions, but I forgot what that was...

---

### Post by gohanssjn on 2007-04-26
Maybe I'll just uninstall all my programs tonight from E:\ and expand C:\ to combine them, and reinstall the software.  Seems it may be my easiest route right now to get both OS's and MediaDirect.

---

### Post by Duck2006 on 2007-04-26
I beleve you can have up to 63 partitions, but only 4 can be primary, the rest have to be extended

---

### Post by gohanssjn on 2007-04-26
By "extended" do you that I can have my 4 windows partitions and then a bunch of ext3 ones?  Kind of lost here in the wording.

---

### Post by Cypher on 2007-04-26
There are two partition types, Primary and Extended. If you create 4 Primary partitions, you cannot create anymore partitions of any kind.

What you want to do is create 3 Primary partitions and with whatever is left out create an Extended partition. Now within this Extended partition you can create many logical partitions..

Did that help?

---

### Post by gohanssjn on 2007-04-26
Sort of.

Unfortunately, MediaDirect is in an extended partition.  It's a logical partition within an extended one, and you can't really modify it or it breaks.  Ugh.

---

### Post by Cypher on 2007-04-26
Well..you currently have 2 Primary partitions and the Extended. You could create a single Primary partition for Ubuntu and install everything in there. You won't have a swap, but as long as you have enough RAM, that shouldn't be an issue..

---

### Post by Duck2006 on 2007-04-26
Ubuntu will create a swap partition, it will be an  extended partition. Make the extended partition that you want to install ubuntu in and when you install ubuntu point it to the extended partition and it will do the rest for you.

---

### Post by gohanssjn on 2007-04-26
Well, i tried last night to install Ubuntu, and here's what happened...

I had 5 partitions!  But MediaDirect broke.  I am assuming that was from Grub though, not anything else.  it was really weird, but Vista definately saw 5 partitions.  C,E,(blank),(blank),Mediadirect is how it went.  and the 2 blanks were Ubuntu partitions that were created when I chose a guided installation into the largest free space.

Weirdness.  But both OS's loaded fine aside from the MD problem.

---

### Post by Duck2006 on 2007-04-26
From the live CD in the termial type

sudo fdisk -l

and post the out put

---

### Post by gohanssjn on 2007-04-26
I will do that as soon as I get home and get it all loaded again!

---

