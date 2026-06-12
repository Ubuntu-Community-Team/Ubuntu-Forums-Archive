---
title: "fiesty upgrade memory hog"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by snkiz on 2007-07-17
so I just upgraded to feisty from dapper. so far so good, except for a few 3rd party apps being broken but I expected that. What does suprise me however is how much hard disk space this used.  I went from using about 40% of my root partition to 70% It look to me from those numbers that the upgrade does not delete the old files. further evidence of this is the fact that my grub now show six diffrent kernnels at boot! plus my win install (B.T.W havn't touched it in weeks) so here is the million dollar question where do i find an  idiot proof disk cleanup utility and is there a defrager? does linux even need to defrag?? since many want to know this kind of info I have a pIII 600 in the box and 256M ram.

---

### Post by snkiz on 2007-07-17
bump! some one must know the answer to this.....

---

### Post by Al3xK3aton on 2007-07-17
> **snkiz said:**
> does linux even need to defrag??

Yes.

---

### Post by snkiz on 2007-07-17
come on people this isn't that stupid I realy do want to clean the old stuff out but I fear deleting something I really need... a little help please

---

### Post by snkiz on 2007-07-17
yes doesn't tell me where to find the tools been searching since day one I've seen no mention od clean up utilities except kleansweep witch is no good to me I'm not running kde but thanks for the reply :)

---

### Post by snkiz on 2007-07-17
what do I have to say to get a decent answer?? I thought we were here to help each other this is the third time I've come here for help and got nothin :confused: some community, you know I used to pay to get treated like this.

---

### Post by digital_sabotage on 2007-07-17
not sure what you did on your upgrade ...kinda sounds like you should do a re-install ...as for cleaning up all i worry about is clearing my browser cache and maybe emptying my tmp folder once in a while

 ...i have an 80 gig hdd ...10 gig swap and 58 gigs remaining  ...that means 12 gigs of data ...and i have a lot of pics ...movies etc  ...not sure what a default install plus upgrades equals but it can't be much ...7 or 8 gigs maybe

...i heard linux doesn't need defrag programs  ...puts data where it's supposed to be in the first place or something?  ...i know ...crazy concept and hard to believe

---

### Post by bradmayne on 2007-07-17
try removing your kernel headers by going to synaptic manager and deleting what you don't need from there search for 386 or 486 etc. also go to your bash and do a sudo apt-get autoremove or sudo apt-get autoclean or both! Let me know if this helps!

---

### Post by snkiz on 2007-07-17
> **bradmayne said:**
> try removing your kernel headers by going to synaptic manager and deleting what you don't need from there search for 386 or 486 etc. also go to your bash and do a sudo apt-get autoremove or sudo apt-get autoclean or both! Let me know if this helps! 

I'll try that be back soon.... I hope..

---

### Post by snkiz on 2007-07-17
that helped got me down to 50% usage about a gig more than before the upgrade I'll have to test it more tomorrow and see what else can go. I gotta get up in three hours... ick i hate work but thank you very much.

---

### Post by jordanmthomas on 2007-07-17
I know it's not your major concern, but I'd suggest giving this a read:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

It's why you don't need to defragment as long as you use ext3 or reiserfs

Also, give this a read so you'll know what you can delete to grab some of your hard disk space back:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

