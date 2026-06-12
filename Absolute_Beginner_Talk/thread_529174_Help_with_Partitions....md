---
title: "Help with Partitions..."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Migrating Snail on 2007-08-18
Alright I'm trying to install Ubuntu 7.04 (I'm using an ati x1600pro 512mb.. I saw something in the stickies that says "if you're using an ati x graphics card...".. not sure if that applies to me YET)

... I'm trying to install it and when I get to the part where it asks what partition do you want to install it I'm not sure what to do.

I have 1 hard drive, it's 120GB NTFS and Windows XP Pro is on the only partition there is. (Actually there is 1 more but it's like 8mb I think it's for system files or something only?...)

so anyways the main question is:
Do I install Ubuntu on a NEW PARTITION or do I install it in the same partition as XP? (is that even possible?)

I've tried messing around with different options and if I click something like use the remaining free space or something like that I get an error message saying "blah blah.. this might have happened because there is not enough free space on the hard drive"

..  I have 34.3 GB left over on this 120GB hard drive although I'm not sure that's what it means by "free space"...

So bottom line  question I guess.. Do I install Ubuntu on a NEW PARTITION or do I install it in the same partition as XP?



Sorry if this post is confusing.. I'm really confused about all the little codes and stuff that are used for the partitions section...

Edit: I'm trying to dual boot.

---

### Post by raja on 2007-08-18
You have to install it on a separate partition. 
You will have to shrink the windows partition, maybe leaving about 20 GB to create a new partition for installing Ubuntu. You should back up important data in that partition and defrag the windows partition before you do this. Once you have done that, you can use the automatic option, or if that did not work for you, just choose to shrink the partition and then create a new partition in the empty space.

---

### Post by Migrating Snail on 2007-08-19
How would I go about shrinking the partition?.. do you mean with a program or just getting rid of some files?

---

### Post by raja on 2007-08-19
No - you shrink with gparted (the partition editor).

---

### Post by daveshields on 2007-08-19
Snail,

The nature of your questions suggests you are new to Linux and Ubuntu, so I suggest you proceed a a snail's pace.  A false step can lead to the loss of the existing data on your hard disk.

Although Raja is right in his suggestion, doing a full data backup can be a chore, and there is still the possibility that the existing software could be lost, which would require reinstalling Windows and any additional programs you have installed.

I have done many Ubuntu installs with an operating system in place, but you may wish to investigate some more so you can proceed with confidence. Two useful entries are that for "partition" in wikipedia, and the informative -- and entertaining -- "illustrated dual boot site" at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Migrating Snail on 2007-08-19
I have nothing to lose that's important on my computer.. I know pretty much what I need to do but I'm stumped because the thing gives me an error for every option I choose other than "use the whole partitoin" .. or whole hard drive whichever it says..

---

### Post by carloslosgrande on 2007-08-19
[FONT="Comic Sans MS"]Hi, try downloading GParted live cd, burn it the same way as the ubuntu cd, and boot up with it. You can get your partitions ready with this tool. Its quite simple to follow, even I can do it.
You can use it to shrink the windows partition so that the ubuntu cd installer can do the rest automagically for you.
I've used this tool many times, its very useful to have.[/FONT]

---

### Post by Paul133 on 2007-08-19
You can't use the free space because you have no free space if XP is taking up everything. You'll have to choose "manually partiton" and then shrink XP, which will be the NTFS filesystem. Once you have some free space, you should be able to go back and install using the free space on your HD.

---

### Post by Lithium17 on 2007-08-19
I thought there was a partitioner built into the ubuntu installer?

---

### Post by raja on 2007-08-19
> **Lithium17 said:**
> I thought there was a partitioner built into the ubuntu installer?

There is .., but as someone suggested, sometimes the gparted live cd works better to make your partitions.

---

### Post by Lithium17 on 2007-08-19
Ah, ok.

---

### Post by Aishiko on 2007-08-19
Snail, you sound like I did 10 years ago (OK, I never sounded that way I just took classes at the CC when I was High school aged, I graduated a few years early) and learned what a partiaton and every basic thing about computers and windows, dos, and unix. 

The free space you are seeing is part of the windows partion Windows "owns" that space, the 8MB yourseeing is as you assumed a part of the Overhead needed by the drive for the formating and tracking of files on the drive (if I'm remembering right).

I've not found a good program (for free) that works, though if these users say those programs work, I'd give them a shot since you said that there is noting on there that you can't afford to lose, though with 90 gigs used on a 120 gig hard drive I find it hard to believe that you don't have some data files that you'd want to save.

---

### Post by Migrating Snail on 2007-08-19
^.. cool I guess I'm on the right track.. 'cause I'm in high school right now...

Edit:.. 90 gigs?.. theres only like 73 gigs used lool... as i said I'm in high school so there's nothing that will hurt me if I lose it..

---

### Post by Migrating Snail on 2007-08-19
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi, try downloading GParted live cd, burn it the same way as the ubuntu cd, and boot up with it. You can get your partitions ready with this tool. Its quite simple to follow, even I can do it.
You can use it to shrink the windows partition so that the ubuntu cd installer can do the rest automagically for you.
I've used this tool many times, its very useful to have.[/FONT]

alright so far the gparted live cd seems to work and I made a new partition approx 6 gigs big and i formatted it to what "swap-linux" or something like that... Just b/c I have no idea which one to format it as...

But when I go to install ubuntu it still doesn't give me the option of installing it on the blank partition.. it just tells me the default stuff...

Edit: Oh yeah and I"m not really sure if I'm getting all the options of the gparted live cd because when I start it up and the window pops up the entire thing is offset and like 1/3rd of it is cut off b/c it's running off the top left of the screen... is there a way to re-position that so I can see all the options?.. 

oh and yes I did click "apply" to make a new partition/format it

---

### Post by Aishiko on 2007-08-19
> **Migrating Snail said:**
> ^.. cool I guess I'm on the right track.. 'cause I'm in high school right now...

Edit:.. 90 gigs?.. theres only like 73 gigs used lool... as i said I'm in high school so there's nothing that will hurt me if I lose it..

Sorry I was up late and up early so I'm not thinking as critally as U should be I thought you said te drive was 120 gigs and had about 30 free 120-30=90.

As for me I have alot of files that I can lose, but I'd rather not.  But then some I've spent hours and or weeks getting or getting just right.

But let me know how it goes I'm intrested in hearing how it works out for you.

---

### Post by Migrating Snail on 2007-08-19
> **Aishiko said:**
> Sorry I was up late and up early so I'm not thinking as critally as U should be I thought you said te drive was 120 gigs and had about 30 free 120-30=90.

Ah.. actually it IS I think technically 120 gb but it only 'registers' (either that or the OS takes up the space..) as 111gb

.. i'm still waiting for a response/looking for a solution to my previous post/problem :(...


basically I think the only thing I'll have trouble with as far as this whole install/and actually using linux goes is this damn partition stuff... i swear I'm doing it right though maybe it's just the installation part I'm confused with..

Edit: alright now I know for sure I created a new partition because this one's size is reduced by 6 gigs... i created the new partition to be 6 gigs... but when I go to install ubuntu it doesn't recognize the new partition.. what does it have to be formatted as?

---

### Post by Aishiko on 2007-08-19
ahhhh it should not be formated so go in and delete the 6 gig partion and then run the CD it will find the 6 gigs of space and then properly format it to the 3 partitations it needs to run Linux.

and the OS is included in the 111 gigs of space it sayes the drive is, well 105 now, the diffrence comes from accounting of all things, it is 120,000,000,000 and it goes a kilo byte is 1000, a mega is 1000 kilobytes, and a gig is 1000megabytes but the filesystem uses a base 1024 not 1000 and so it adds up a 500gig comes out to being like 480 formated.

does that help?

---

### Post by Migrating Snail on 2007-08-20
wow ok that was easy.. i have it installed now.. all I did was mess around in the "manual" section and got it done...


now I have a nother question while I'm here.. i read somewhere that there's a problem with ati x series cards.. i have x1600pro 512mb is there anything i should look out for.. like some issues or something?..

---

### Post by ozzyprv on 2007-08-20
Wow, that was easy for me too.
Less than 24 hours playing around with Ubuntu and I have it installed up and running.

Thank you. I got the info I needed about partitioning from this thread. I went and read the information provided in the link posted by daveshields.

O.

---

### Post by dptxp on 2007-08-20
To the OP-

Maybe you just carryout disk defragmentation first, run live CD next, install with it using guided auto mode for partitions.

If you have created any partitions so far, you have to delete them in manual mode first.

---

### Post by Aishiko on 2007-08-20
> **Migrating Snail said:**
> wow ok that was easy.. i have it installed now.. all I did was mess around in the "manual" section and got it done...


now I have a nother question while I'm here.. i read somewhere that there's a problem with ati x series cards.. i have x1600pro 512mb is there anything i should look out for.. like some issues or something?..

One of the forums has a sticky on how to installl the ATI X series cards that should be place to get the information you need to get it up an d running.

And congrats!  I tried linux back in the days when you had to complie every program you were going to use, unlike today where you can download and go no compiling required.  However back then I was working part-time and taking 18 credits in college with 20 contact hours each week, so I didn't have the time (or the patience even with meds) to learn how to use Linux or fix the mydrad little problems that kept coming up.

---

### Post by carloslosgrande on 2007-08-20
[FONT="Comic Sans MS"]Hi, sorry I was away for a while. Glad to hear you got your partitions setup. If your screen is offset maybe you can change the screen resolution when GParted starts...it asks that as you go thru the screens.
Also you can use GParted to tweak your partitiion setup later on as you understand more what your needs are in this, this is what I do as I find it easiest and simplest.

As to ATI cards, I have an ATI X600. I've tried the various setups and I usually find it causes more trouble than I need.
That is, I don't actually need to do anything, my card just works.
If your having some trouble try the 'restricted drivers' in >system>administration>restricted drivers manager.
I find it works best if you use the 'supplied with system' fixes first.[/FONT]

---

