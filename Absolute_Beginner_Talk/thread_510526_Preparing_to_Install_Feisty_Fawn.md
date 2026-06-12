---
title: "Preparing to Install Feisty Fawn"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Zeppelin! on 2007-07-26
I'm an XP user, and I have been for several years on my HP Pavilion 700(hardware unaltered).

In the past few days, I've gotten my hands on a Feisty Fawn disc, cleaned out my disc space, from 2% available, to 55%, and have puzzled over damage I indubitably caused with my brutal deletion methods(It's nothing to worry about, just some leftover scraps from programs in my Add/Remove Programs box).

Anywho, when I defragment, I am left with only about 30% of my disc space for the largest contiguous free space. The reason is that at about 60% there is a cluster of Unmovable files, and at about 90% there are some normal files that simply *won't* move. My eventual plan is to devote more and more of the drive to Ubuntu as I am able to phase out XP.

Anyway, I heard from a friend something about partitioning the drive. Should I just let Ubuntu figure that out(there's a step in the install process that deals with this, as I recall), or should I work on some way to create a good partition, hopefully into one space, or fragmented amongst my three chunks of files? If so, how?

By the way, my defragment shows my hard drive like this:
/=fragment
|=contiguous files
!=Unmovable
-=free space

/||||||!!||||||||||||||||||||||||||||||||||||||-------!!!!---------------||||--------

With hundreds of snippets of free space interspersed in the contiguous files.

OR------------------------------------------OR---------------------------------OR

Am I worrying about the wrong things entirely?

Someone help me out, confusion and panic have my eyelid twitching.

---

### Post by Hayl on 2007-07-26
Hey gratz on deciding to upgrade to fawn, I did it on tuesday (3days ago) and already I feel like im really getting to know the OS.  The paritiioning of your drive will be if you want to still use XP (dual-boot) I didnt do this so I dont know if ubuntu will do it for you or not, I do know that there are alot of very good apps out there to assist in parting a drive though.  To set up dual boot id say have at least 100gb I may be off, but I wouldnt go much smaller than that.  On Fiesty installation, it was pretty seemless, I had some video issues, but they porvided me with a chance to use gedit and the linux terminal right away (two skills that I think are going to be very important as my linux life progresses) neways gl with your install, if you have questions these forums will have the answers gl gl gl

---

### Post by Zeppelin! on 2007-07-26
100GB?

This computer *used* to have 80GB, it's down to 69GB now.

This isn't good...


Edit note: The idea is to phase Windows out, and eventually delete it entirely, making Ubuntu the sole OS of the computer.

So, Windows doesn't need any more space than it has.

---

### Post by davidjmayo on 2007-07-26
I would be worried about the unmovable space.

Have you tried to defrag the drive a few times (once is not enough)
Can you run a disk check from windows and check your hard drive is Ok
If you get any errors especially about bad blocks it's time for a new hard drive

looks like you could be getting into problems whether it's ubuntu or staying with windows

---

### Post by Zeppelin! on 2007-07-26
I've defragged it about six times. Are you speaking about the normal files that refuse to move? They'll move a tiny bit, but not in any significant fashion, and I think some of them don't move at all.

---

### Post by skymera on 2007-07-26
what i did was get a really good defragger. a trila

i used Diskeeper.

i set it over night to constant defrag, one it was near done it moved like 2 - 20 files.

over a sleep tha i have, 9-10 hours, it cleared up over 10gb of crap !

so i reccoemd that idea.

or leave it for couple hours then shutdown after say 5hours?

```
 sudo shutdown -P 300 
```

---

### Post by davidjmayo on 2007-07-26
you have more than enough space to defrag (55% you said)

Can force a disk check to run on next boot ?

Problem is I used W2K not XP or Vista and don't remember how to do it. Should be in the menus somewhere

---

### Post by loserboy on 2007-07-26
I wouldn't worry about what defragment shows when it's done as long as no real errors come up.
If you plan on dual booting (having XP and ubuntu), just defrag a couple times and then when you start the Ubuntu livecd there will be an option to let Ubuntu do all the partitioning or to do it manually.

if this is your 1st time I would say let it do the automatic partition, although it's really pretty easy to do it manually, when your nervous or getting into something new it makes it seem kind of difficult.

now that I think about it you should be able to choose the manual option just to take a look at it and if you don't like what you see just go back

---

### Post by loserboy on 2007-07-26
you don't need 100GB, I'm dual booting and I have a 40GB with like 8 gigs free

---

### Post by Zeppelin! on 2007-07-26
I'd like to try that disc check bit just once before I take the plunge, thank you for your reassuring words previous poster.

Unfortunately, I have no idea how to do a disc check.

---

### Post by loserboy on 2007-07-26
if you have your XP disc it will allow you to do to rescue mode  command prompt or whatever it's caled and you can run chkdisk/scandisk from there.
 I just forget how to get to it, google is your friend :)


edit: recovery console thats what it's  called, when you get in there run chkdsk

you can also run it with the "/p" or "/r" parameter to force tests or force tests and repair respectively

---

### Post by skymera on 2007-07-26
a simple way to do a detailed XP boot check

start > my computer > right click C:\ > tools > disk check > check BOTH boxes > restart

this will run CHKDSK without the disc

---

### Post by loserboy on 2007-07-26
oh cool I didn't know that

---

### Post by Zeppelin! on 2007-07-26
Ran a disk check.

No errors appeared, the whole thing took about 20 seconds.

Now, one last question.

What internet service should I use when I switch?

---

### Post by alex_anthony on 2007-07-26
by the way, the 69gb thing was actually 69 GiB. Its down from 80GB because of different maths -
69 GiB= 69*1024*1024*1024
80 GB= 80*1000*1000*1000
those sums should be roughly the same

---

### Post by Zeppelin! on 2007-07-26
Thank you for telling me that! I had worried over it for some time.

Anyway, I guess I should rephrase my latest question thus:

What ISPs work with Ubuntu, and in turn, any suggestions for what one I should use?

---

### Post by loserboy on 2007-07-26
from what I've seen and experienced cable is the easiest, DSL is pretty easy, and dialup can be a pain, depending on your modem and ISP, but for high speed ISP shouldnt matter

---

### Post by Zeppelin! on 2007-07-26
I used to have Verizon DSL, but I had to give it up for a month, and when I was ready to subscribe again, they were out of slots. They've never opened up another one. So, I've been using AOL for the past several eons, and I'm bloody tired of it.

I'm thinking ClearWire.

Edit: Scratch that, ClearWire isn't available here.

Hmm...

---

### Post by Old Pink on 2007-07-26
Format it and take the leap big time. 

You won't regret it. ;)

---

### Post by Zeppelin! on 2007-07-26
You're speaking to one of the most panicky people on the planet. The only reason I'm still on windows is I'm covering all my bases.

Can anyone give me an answer as to what ISP companies work with Ubuntu?
I am *NOT* installing AOL again. No way. Never.

---

### Post by Zeppelin! on 2007-07-26
This is my last attempt with this thread to get the answer I need.

What ISP -companies- work with Ubuntu?

You know, like AOL.

But, *NO* AOL.

Can I get an answer?

---

### Post by Old Pink on 2007-07-29
All of them?

---

### Post by upthelum on 2007-07-29
Your auto dhcp will pick up network settings for you. If you can, back up files you need to dvd and run the ubuntu disc to set up a dual-boot, the grub will pick up xp so you can choose between both. There's lots of links to setting it up on the boards but it's straight forward enough, use the ubuntu partitioner to erase the space you want to free up, Bob's your auntie's brother...

---

