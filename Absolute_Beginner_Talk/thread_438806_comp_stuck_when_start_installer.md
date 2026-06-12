---
title: "comp stuck when start installer"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by rick_2047 on 2007-05-10
when i start the install program (after waiting for 10 mins for the live cd to start) the comp gets stuck 
is this bcoz i m on 256 mb ram and no swap:oops: 
if so how can i create a swap
when i am on the live cd and try fdisk -l i dont get ne results 
do i have to mount my partitions first to make the appear here
plz help
i desperatly wanna install ubuntu 7.04
:biggrin:

---

### Post by deadgobby on 2007-05-10
Please help us help you. What are your system specs? Like CPU and ect..
Gobby

---

### Post by blackened on 2007-05-10
Have you tried using the alternate install cd? I have 1GB of ram and the live cd is still pretty cumbersome, so I tend to use the alternate cd instead.

---

### Post by Ozeuss on 2007-05-10
> **rick_2047 said:**
> when i start the install program (after waiting for 10 mins for the live cd to start) the comp gets stuck 
is this bcoz i m on 256 mb ram and no swap:oops: 
if so how can i create a swap
when i am on the live cd and try fdisk -l i dont get ne results 
do i have to mount my partitions first to make the appear here
plz help
i desperatly wanna install ubuntu 7.04
:biggrin:

if this is a fresh install, then you don't have swap yet. usually when you load the liveCD it mount your partitions automatically, and it shouldn't interfere with the install. i think 256 ought to be enough for install.
my advice is- download the iso. file again, check it's hash (look for 'howtomd5sum' in the community wiki), and then burn it at low speed. when done, check the CD for defects.
if the problem persists, you can try to do a manual install- for that you have to setup the partitions manually. or you can use the alternate cd. for both i suggest you read up a little before.

---

