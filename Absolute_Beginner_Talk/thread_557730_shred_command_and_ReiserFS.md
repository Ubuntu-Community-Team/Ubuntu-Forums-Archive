---
title: "shred command and ReiserFS"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Runningflame570 on 2007-09-23
I'm not sure if this actually belongs in beginner talk but I think it may so I'm posting it here. If its the wrong forum please move it to a more appropriate one.

My question is how effective is the shred command under ReiserFS and other journaling file systems and also since I was unable to find this with a brief search on scroogle, where does Firefox store it's temp files?

While theres nothing really necessitating my usage of shred on temp files, etc. I may still want to have it run regularly over them (and perhaps even run as an automated script further down the line). This is all dependent of course on how effective it is on journaling file systems and ReiserFS in particular.

---

### Post by Pelham123 on 2007-09-23
Plenty here:
[http://www.google.co.uk/search?hl=en&q=shred+reiser+journaling&meta=](http://www.google.co.uk/search?hl=en&q=shred+reiser+journaling&meta=)

and here:
[http://www.google.co.uk/search?hl=en&q=ubuntu+mozilla+temp+internet+files&meta=](http://www.google.co.uk/search?hl=en&q=ubuntu+mozilla+temp+internet+files&meta=)

---

### Post by Runningflame570 on 2007-09-23
Hmm, thank you..I used a number of different searches which didn't seem to bring up any relevant data on the Reiser question, admittedly I probably should have tried harder on the temp files issue.

Thanks again.

---

### Post by Runningflame570 on 2007-09-23
Ehh, unfortunately after having looked at that some more they don't specifically address the issues shred might run into with ReiserFS, some suggest the man file is incorrect in some respect, others copy it verbatim, one is actually discussion from what seems to be RFS developers.

The man file doesn't seem to have changed much in years so even if it was accurate before its hard to be certain it is now..difficult.

---

### Post by Pelham123 on 2007-09-23
Have you read the Wiki on Shredding?

[http://en.wikipedia.org/wiki/Shredding](http://en.wikipedia.org/wiki/Shredding)

Very useful...

---

### Post by Runningflame570 on 2007-09-23
> **Pelham123 said:**
> Have you read the Wiki on Shredding?

[http://en.wikipedia.org/wiki/Shredding](http://en.wikipedia.org/wiki/Shredding)

Very useful...

Yes, but there remains a certain degree of uncertainty out there about some of the claims made about different journaling file systems. I'll just have to figure out a way to see if theres remnants of a shredded file on the system afterwords at some point here..thanks again though.

---

