---
title: "[SOLVED] Partitioning drive in GParted"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-16
Ok I'm trying to partition my drive in GParted, and I'm having an issue.

I have the first section of my drive (75 gig) for Windows

Then I have the following:

sda2 20 gig(ext3)
sda3 49 gig (having issue formatting)
sda4 2 gig (linux swap)

I was able to create sda2/3 no problems, but when I try to format the sda3 drive it's giving me an error message:

> Format /dev/sda3 as ext3    ( ERROR )
     	
set partitiontype    ( SUCCES )
create new ext3 filesystem    ( ERROR )
     	
mkfs.ext3 /dev/sda3
     	
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda3 is mounted; will not make a filesystem here!

What's strange is that it's not mounted when I try to format it, because it's not an option.  
Anyone have any tips?

---

### Post by dmorand on 2007-07-16
The issue I'm having is from the Ubuntu LiveCD, which I know works because I've already installed Ubuntu using this cd, I just screwed up too much stuff so I want to start fresh.

I have GParted LiveCD as well, but when it boots it goes into a console.  Is that what it's supposed to do?  I don't know what I'm supposed to do at the prompt.  I am booting in GParted LiveCD using Automatic.

---

