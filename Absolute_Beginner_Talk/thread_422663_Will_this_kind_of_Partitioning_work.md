---
title: "Will this kind of Partitioning work?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Tulx on 2007-04-25
Hi

Im making second Feisty clean install. Last time I were not wise enough to put Home directory on seperate partition. Please look at the screenshot and tell me will it work. Basically I have almost no idea what I am doing. Also the harddrive is pretty small - 20 GB. I gave swap 880 MB and for the root system 5 GB. 

I do not know where to put the mount points? I hope they are correct. I dont know either what should be the types of partitions? I set them both to ext3. I searched for the HOWTO-s of partitioning and did not find any what could give me an solution. Maybe you just can post a link?

-Tulx

---

### Post by rich.bradshaw on 2007-04-25
Looks fine... You probably want as much swap as you have RAM, so you can hibernate properly. 880 is more than enough for most people.

Looks fine apart from that. What are you thinking might be wrong?

---

### Post by BaffledMollusc on 2007-04-25
The partitions, mount points and file system types are all fine as you've chosen them.

The only problem might be that the root partition might be a bit small. 5 gig might be enough or it might not. This partition is where all the system software is installed, so I guess it depends on how many additional packages you install.

Edit: Just noticed the text at the bottom where it says you need "at least" two gig for the root file system. So I guess 5 gig should be fine.

---

### Post by Tulx on 2007-04-25
I chose 880 MB for swap because so many swap had my previous Feisty. I think I then give the root system 9 GB. That should be enough. I have made many stupid mistakes while wildly guessing. I thinked that I will just ask this time. After starting to use Ubuntu I am gone a little bit paranoid in the good way.:) 

Thanks for the answer - Tulx

edit: I just readed your edit... I then give it 7 GB. Again, thanks for the answers.

---

