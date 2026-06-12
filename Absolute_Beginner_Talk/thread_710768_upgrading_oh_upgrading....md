---
title: "upgrading oh upgrading..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by kamasabi on 2008-02-28
Gents,

I have several questions I would like to ask ya'll, as I am going to be making some major changes to my systems over here.  The time has come where am going to need a new file server, and my current gaming computer, while not out of date, is getting on its way out.  So, my plans are to take the stuff from the game computer, which is more than capable for the file server, and just build a new gaming computer.  Now my question lies in support for the motherboard and onboard RAID.

Anyway, current specs on stuff to be transferred (current game rig):

A8N-SLI Premium
AMD Opteron 170 @ 2.7GHz
2GB Corsair XMS
2x 7800GTX (only 1 will be in the file server, or maybe both, who knows :p)
DVD-RW, DVD-ROM, CDRW...

Does anyone have experience with ubuntu on this board, or with the deluxe or vanilla version?  I would like this to be a smooth transition, considering it is probably going to take a day or so to get everything all running again properly. 

I plan on having 4x 750GB drives in RAID 5, as well as one smaller drive for the OS separate from the array.  I've been using Ubuntu for about 4 or 5 months or so now somewhat regularly, but I still consider myself a nub, so please be patient with me :).  

What tools will I need as far as ubuntu to set this up (as far as software is concerned)?  Anything I should take into consideration or major driver problems that are known?  The way up until now, my current file server has been just simply a different drive for different file types.  I want raid for the performance, but raid 5 specificially so that 1 drive dies, I'm not SOL, I can swap in a new drive, and let it rebuild itself, even if I have to sacrifice 1 drive's worth of space :p.

Please let me know your suggestions and thoughts.

Thanks!!!

Kama

---

### Post by paultag on 2008-03-01
> **kamasabi said:**
> Gents,

Does anyone have experience with ubuntu on this board, or with the deluxe or vanilla version?  


No.

> **kamasabi said:**
> 
I would like this to be a smooth transition, considering it is probably going to take a day or so to get everything all running again properly. 

Don't we all :P

> **kamasabi said:**
> 

I plan on having 4x 750GB drives in RAID 5, as well as one smaller drive for the OS separate from the array.



I am not sure that you can....
As for setting up a 5xRAID, that is OK. What you can do is set up some smart partitioning to work around this:

Primary Partition Boot (128MB)
Primary Swap ( == to RAM )
Logical Partition / ( 3 gigs is more then enough )
Logical Partition /usr ( depending on how much software, etc )
Logical Partition /home ( if this is where data is stored, make it BIG)

This way, you can make sure that your file system is not hogging the whole drive, and vise versa.


> **kamasabi said:**
> 

I've been using Ubuntu for about 4 or 5 months or so now somewhat regularly, but I still consider myself a nub, so please be patient with me :).  



Welcome!

> **kamasabi said:**
> 
What tools will I need as far as ubuntu to set this up (as far as software is concerned)?



Sure: If this is a Windows Domain, consider making it the Domain Master, as well as a client using Samba. For HTTP ( if you need it, Apache, PHP etc ). MySQL and Postgres are both awesome SQL databases, as well as NFS ( I think this is stranded on Ubuntu )

All of these take some time to learn and configure, so don't think this is a single day kinda thing.

> **kamasabi said:**
> 
 Anything I should take into consideration or major driver problems that are known?  The way up until now, my current file server has been just simply a different drive for different file types.  I want raid for the performance, but raid 5 specificially so that 1 drive dies, I'm not SOL, I can swap in a new drive, and let it rebuild itself, even if I have to sacrifice 1 drive's worth of space :p.



I am not sure here, I have never had a problem with my drives, and RAID has been integrated as long as I've been with Linux ('03).

Cheers,

Tag

---

### Post by kamasabi on 2008-03-01
thanks for the response / info!

I don't plan on doing any as far as SQL, PHP, etc are concerned, it is just for simple file sharing.  I use samba on my current server, and it does the job quite well.  What I wasn't sure of is the setting up of the array itself, how to do it, where to do it, etc.  For instance, my board came with a utility I could use for setting it up on XP,  I just wasn't sure what I should use for setting it up on Ubuntu....

---

### Post by paultag on 2008-03-01
Ubuntu should be able to set up a RAID out of the box. if there is no data that is important on the cluster now, then wipe it and give it a shot. You will find that most drivers etc. are completely obsolete with Linux ( meaning that its supported out of the box, like Wireless cards, Ethernet cards, Sound Cards etc )

Give it a shot, and let us know

Cheers,
Tag

---

