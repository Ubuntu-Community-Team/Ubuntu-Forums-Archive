---
title: "N3WB Questions"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by fr33zypop on 2007-12-13
So I looked, and cant find what I want exact so i am posting. I don’t care if i get flamed. That’s your business to talk down to someone who needs help. My name is Jason, I am new to the Linux world and I got a copy of UBUNTU 7.10 from school and I have been playing around with in on the live cd and I really like what I say. I want to be able to install it on a drive I have split in half with WINXP Pro. This is what I did, when I installed xp last i split the drive to handle both OS's. xp works fine. I load into the cd on UBUNTU and went into the install program. I went thought all the location for time zone and all that jazz. When I got to the choice to where i want to install it, there options are to just install all over the entire drive or guided which chooses the drive that has more free space and the last one is manual. I go manual and delete the partition that i want then add a new one. I setup it up as a (ext3 or ex3 I don’t know off hand which one I am not at home) then it has the mount something i think it said mount point. I put it as / for the location of that. Then I run through the install. Did I do it right or should I get more exact info. I am sure you all know what I am talking about.

---

### Post by TheLions on 2007-12-13
If I understanded you right everything looks fine except swap file. Had you created swap file?

---

### Post by fr33zypop on 2007-12-13
No I havnt yet, someone at work here was telling me about SWAP file. So I will need help on that.

---

### Post by the Didey on 2007-12-13
I agree. that seems to be right except for the swap...but it might be on there.

I'm sure there's a more exact way, but if you  run gparted (the gnome partition editor) it should show the swap. You can run gparted from the Live CD or you can get it for the new install in add/remove programs

On a side not, I'm really new too. but from what I've read a lot of the cats around here seem to like to make sure they have a separate partition for /home which is like your documents and setting folder.

I believe that this make it easier to save a lot of your settings when you upgrade to the next release.
Confirmations anyone?

Having said that, there should be no immediate problems with the way you did it.....it's more like down the road stuff.

EDIT: you should be able to add the swap with gparted without having to reinstall. I believe that  the SWAP is suppose to be 2 times the amount of RAM you have. but everyone say you'll never need that much

---

### Post by TheLions on 2007-12-13
to create swap just resize one of your partitions (i recommend windows partition:twisted:) with gnome partition editor

how much swap do you need?
amount of RAM + SWAP =2GB (my estimation)

if you have >=1GB RAM then probably swap isn't must have

---

### Post by erfahren on 2007-12-13
.. don't worry about the /home partition yet, when you need to reinstall eventually you can worry about that then.

pop that LiveCD in again and once you're booted into it go to the terminal (Apps > Accessories) and type in 
```

sudo gparted

```
you should see something like what I attached here. Resize the ext3 partition leaving a bit over 1GB free. Then create a swap file out of that one GB.

note: there's good info on dual-booting Windows and Ubuntu at (amongst other things):
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
and hermanzone has comprehensive info as well:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Note: the screenshot is from my own partition table. To understand why I have an extended partition you can reference: [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

---

### Post by erfahren on 2007-12-13
> **TheLions said:**
> 
how much swap do you need?
amount of RAM + SWAP =2GB (my estimation)

there was a guideline that said you should have twice the amount of swap than you have RAM. That was really applicable back when PCs had 256, 512 MB or so. 1GB is enough.
> **TheLions said:**
> 
if you have >=1GB RAM then probably swap isn't must have
you need to have swap

---

### Post by TheLions on 2007-12-13
> **erfahren said:**
> there was a guideline that said you should have twice the amount of swap than you have RAM. That was really applicable back when PCs had 256, 512 MB or so. 1GB is enough.

you need to have swap

[[IMG]http://img162.imageshack.us/img162/3862/prikazzaslonacs3.th.png[/IMG]](http://img162.imageshack.us/my.php?image=prikazzaslonacs3.png)
no you don't!

---

### Post by erfahren on 2007-12-13
> **TheLions said:**
> [[IMG]http://img162.imageshack.us/img162/3862/prikazzaslonacs3.th.png[/IMG]](http://img162.imageshack.us/my.php?image=prikazzaslonacs3.png)
no you don't!
:roll:  that's just showing the swap not being used. The swap still needs to be present. Read what it says on the bottom part of *Ubuntu's LiveCD patitioner* (attached).

---

### Post by erfahren on 2007-12-13
now that you mention it though, it seems like the LiveCD partitioner/installer would've spit out an error message if a partition for swap wasn't created. 

I'm curious as to whether or not the OP created one when installing.

---

### Post by fr33zypop on 2007-12-13
Yeah it never gave a error when I installed without last night. Can I ask what does  "swap" do. I am trying to get the full understanding of this install process..

---

### Post by erfahren on 2007-12-13
swap is like "virtual memory" in Windows.

---

