---
title: "My two partitions merged during installation o.O"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by nuphanton on 2007-07-26
Hi everyone :)...recently, windows XP has been acting all strange on me, and I decided to switch to a linux based OS, so I'm fairly new with all this. I tried searching for an answer, but didn't find anything relevant(I believe...might have missed something :P)

Anyways, in the beginning I had two partitions. Partition 1 ( 20 gigs with windows XP in it), Partition 2 ( 90 gigs with my documents and files) both NTFSm, and partition 3 (10 gigs with a backup from acer). Now I installed Ubuntu, while the installation was taking place, it said it was installing Ubuntu on partition #1 and  a swap on #5. So I went ahead with the installation.

Now the problem is that it seems I did something wrong and it deleted all my partitions and made one huge 110 gig one with Ubuntu in it. Now I was wandering if something went wrong, and if it is even remotely posible I could get my documents back.

---

### Post by Rocket2DMn on 2007-07-26
I don't imagine anything went "wrong", it did what you told it to, just not what you wanted.  After reformatting, there is no way to get your files back.  Sorry dude.  
Did you read up on the install process before you started?  There are plenty of guides to help with setting up Ubuntu and still keeping other partitions.

---

### Post by skymera on 2007-07-26
so let me get this

partion 1 - XP
partion 2 - XP files?
partion 3 - backup

so...you installed ubuntu on partition 1? which overwrote windows?

---

### Post by nuphanton on 2007-07-26
> **Rocket2DMn said:**
> I don't imagine anything went "wrong", it did what you told it to, just not what you wanted.  After reformatting, there is no way to get your files back.  Sorry dude.  
Did you read up on the install process before you started?  There are plenty of guides to help with setting up Ubuntu and still keeping other partitions.

actually I read some, and I followed this guide
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
at the "select disk" stage, it only gave me a 120 gig maxtor disk, so I clicked it, resized it to 20 gigs, and right before installation it said partitions #1 and #5 were going to be reformated so I clicked "install"


> **skymera said:**
> so let me get this

partion 1 - XP
partion 2 - XP files?
partion 3 - backup

so...you installed ubuntu on partition 1? which overwrote windows?

yeah, I tried to overwrite the windows paritition only, but it seems like I overwrote everything :(

---

### Post by annda on 2007-07-26
there isn't much hope but you can try installing testdisk USING THE LIVE CD - do not do anything on your live ubuntu partition - to recover the files from lost partitions.

sudo apt-get install testdisk

more info is here:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by skymera on 2007-07-26
> **nuphanton said:**
> actually I read some, and I followed this guide
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
at the "select disk" stage, it only gave me a 120 gig maxtor disk, so I clicked it, resized it to 20 gigs, and right before installation it said partitions #1 and #5 were going to be reformated so I clicked "install"




yeah, I tried to overwrite the windows paritition only, but it seems like I overwrote everything :(


i backed up everything in case it went wrong.
luckily it didnt

however my windows started to go funny after, i thoguh 'thank god i got everything backed up'

but the windows backup utility is so shoddy it didnt back up my progs fully, it only took part of it. so i read on Microsucks website. sorry, microsoft.

so i had to reinstall all my programs manaully.

maybe thats what boat you've just hopped in :(

---

### Post by nuphanton on 2007-07-26
> **annda said:**
> there isn't much hope but you can try installing testdisk USING THE LIVE CD - do not do anything on your live ubuntu partition - to recover the files from lost partitions.

sudo apt-get install testdisk

more info is here:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

okay...so far I'm running Ubuntu from the CD, and have testdisk on a USB drive...I typed "sudo apt-get install testdisk" and I get 

"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package testdisk"

I really new at using linux, so I don't know what's wrong...mind giving me some instructions :-P

---

### Post by skymera on 2007-07-26
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install testdisk

---

### Post by nuphanton on 2007-07-27
> **skymera said:**
> sudo apt-get update
sudo apt-get upgrade

sudo apt-get install testdisk

tried that, but I get "failed to connect to ...." messages (I have some wireless connection problems I have to work out)
then "0 upgraded" messages, and finally "E: Invalid operation testdisk"...maybe I'm doing something wrong...sorry I've never used anything outside of windows :confused:

---

