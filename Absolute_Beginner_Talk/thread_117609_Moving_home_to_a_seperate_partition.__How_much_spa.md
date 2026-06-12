---
title: "Moving /home to a seperate partition.  How much space do I need?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Nameless on 2006-01-15
I've decided that it's probably a good idea for me to move my /home directory to a seperate partition, because I would like to give a try to Dapper and a couple of other distros a try.  

My question is: how much room do I need for my partition that is only going to have the system files (Ubuntu) on it.  I intially set set up a partition of about 10GB for Ubuntu.  I noticed my /home folder is about 4.5GB of that.  If I move the /home folder I'd like to resize the 10GB for Ubunutu, but I'm not sure how much I'll need.  

Here's the break down of the drive:
40GB total

24.5GB NTFS for Windows (I can't make this smaller yet)
10GB EXT3 for Ubunbtu
5.5GB EXT 3 newly created for /home
Some for a swap file

Here's what I'm thinking would be good:
24.5GB NTFS for Windows 
5GB EXT3 for Ubunutu
10.5GB EXT3 for /home
Some for a swap file

So, does the above new allocation make sense.  Will Ubunutu be OK with only 5GB if I make the seperate /home partition?

---

### Post by Arktis on 2006-01-15
Yeah, sounds good.  My root partition is 5 gigs and only 3 gigs of that is being used.  My /home is 13 gigs and 7 gigs of that is currently used after installing a buncha big 'ol first person shooter games.  Swap should probably be around 1.5 times the amount of ram you have, btw.

---

### Post by Arktis on 2006-01-15
Whoops, double post!  ugh...

---

### Post by Nameless on 2006-01-15
[QUOTE=Arktis] Swap should probably be around 1.5 times the amount of ram you have, btw.[/QUOTE]

Thanks for the help.  Out of curiosity why should the swap file be so big?  

Mine is probably about the same size as my ram is now.  Maybe I should up it a little?

---

### Post by Arktis on 2006-01-15
Maybe this will help:  [http://www.tldp.org/LDP/sag/html/swap-allocation.html](http://www.tldp.org/LDP/sag/html/swap-allocation.html)
Until I came across that, I was using about 3 times my physical ram... lol  Anyways, it depends on your needs.

---

