---
title: "another dual-boot question"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by mindworm on 2006-10-11
i'm using linux for the first time, and i'm trying to be able to have a dual-boot of xp and ubuntu on my hard drive, so that i could pick which one to go to at startup

now, i tried installing ubuntu yesterday and got about as far as the partition tool, here's what i did:

i shrinked the windows partition, then i tried to install the linux partitions in the unallocated space - i was told that you need a root partition, a boot partition, and a swap partition. so i tried making a 100 mb primary boot partition, then another extended partition in which to put the root and swap logical partitions, as this is what i was told to do. i kept running into problems with there being too many primary partitions, though, and wasn't able to make all the partitions. when i finally got it kinda going, the partition tool crashed.

so, basically, what i'm asking is how do i set up the partitions on the unallocated space - like what partitions do i need to set up, how big should they be, and just generally how do i go about it

any help would be very appreciated, sorry if this doesn't make too much sense, i'm very new to ubuntu and linux

---

### Post by PriceChild on 2006-10-11
You only need a root partition.

You are advised to have a swap partition, especially if your RAM is less than 1Gb.

You can only have 4 primary partitions on your disc. Any more and you will need to use logical ones.

Check out: [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by bulldog on 2006-10-11
How much space have you available for Ubuntu?

---

### Post by mindworm on 2006-10-11
right now i have about 25 gbs, but i'm expecting to increase it later when i get around to moving some more stuff off my c drive

---

### Post by bulldog on 2006-10-11
Well when you install Ubuntu and come to gparted,create a / [root] partition of about 10GB
Then create a swap about twice the size your fysical RAM.

And the rest of your space you can create /home.

This will do nicely,when you have to do a reinstall you can mount your home without loosing the data on it.

---

### Post by mindworm on 2006-10-11
how do i designate which partition is which, such as which is / or root, etc.

---

### Post by bulldog on 2006-10-11
That's done in gparted when you do the install of Ubuntu.

You will be told you have to create a / and a swap you can see them in a pull down menu.

Create them and give them the right size [gparted counts in MB's,watch it!}
If done make the rest of your space /home and apply.

You shouldn't make the partitions on forehand,just be sure you have unallocated space without any partition.

---

### Post by mindworm on 2006-10-11
thank you, i will try again

---

