---
title: "Hard Drive super noisy after Gutsy - Never stops!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by randalotto on 2007-10-21
I just did a fresh install of Gutsy, and everything seems to be working fine.... 

HOWEVER, the computer is constantly accessing the hard drive. The hard drive is making a TON of noise, much like when I used to do something HDD intensive, but now it never stops.

I was previously running Feisty and my drives were nice and quiet.

Also, I've checked system monitor, and it doesn't seem like any processes are out of control, on either memory or CPU - I can't figure out what's so active.

I'm sure this isn't enough info to actually get an answer, but let me know what else is needed and i'll gladly post it...

Thanks.

---

### Post by Niniel on 2007-10-21
Maybe your drive is just ready to blow and it has nothing to do with Ubuntu?

---

### Post by duanerobertson on 2007-10-21
I've noticed a lot of drive activity at times after my fresh install last night. My drive isn't noisy, but it's noticeable. I don't think I was doing anything that required a lot of disk access, but it's hard to quantify that sort of thing.

---

### Post by nrfool on 2007-10-21
Could it be the indexing service? I heard it is quite aggressive.

---

### Post by Niniel on 2007-10-21
Oh yes, that's most likely it.

---

### Post by nite owl on 2007-10-21
Does this indexing service eventually stop after a while?

---

### Post by swoll1980 on 2007-10-21
Yes when all the files are indexed it will only start again as you add new files

---

### Post by Niniel on 2007-10-21
It can be switched off, too.

---

### Post by randalotto on 2007-10-21
That was actually my first thought, that it might be indexing. However, it's been going for quite a while; I kind of assumed it would be done after 48 hours...

So how can I turn it off?

---

### Post by Super Nade on 2007-10-21
No problems here. Curiously, my Raptors were more noisy under Windoze.

---

### Post by jaybombalous on 2007-10-21
Have u thought about setting ```
vm.swappiness=0
```? Could it be trying to write to the HDD to  free up memory? How much memory do u have installed?

Just a thought.

---

### Post by randalotto on 2007-10-21
I have 2 GB of memory, of which about 500 mb seems to be used at any time.

Why would firefox suddenly, and consistently, be using 100 mb of memory?

---

