---
title: "Internet conniption"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by ncappel1 on 2006-04-09
Hi everyone, I am connected to my colleges LAN through an ethernet connection. Just last year my school went through some internet issues. long story short, to save money they decided to outsource the internet stuff to a company, Apogee. The result is a faster, more reliable internet connection, and unfortunately a subscription fee. You can either buy the faster connection, or be like me and complain about the free "basic service" which is "the equivolent of a 56k modem"

The thing is, while local inTRAnet traffic is unnaffected, (I can still get transfer speeds between two campus computers of up to 1000 kb/s), connecting to the outside internet is much slower. I have never gotten more than 7 k/s. (which is a flashback experience to when I actually had to use a 56k modem. that was way back in the 20th century).

My question is two fold. 
1) why, back in the day, would a 56 k modem never connect at 56 kb/s?

2) The more relevant question: why can't I connect at 56kb/s if I have an ethernet connection which I presume is capable of it (and indeed far more)? It isn't a phone line, so it shouldn't be affected by the traffic of nearby users (or is it?). Is my basic package of free internet a big, twisted joke in that an ethernet connection capable of a full 56 kb/s at all times is literally set to only be able to handle 7 k, thereby faithfully reproducing the 56k modem experience? ](*,) Is there anything I can do?
Are the executives at apogee laughing at me right now--**as you read this thread**?


any help (or counseling) is appreciated

---

### Post by joshrobinson on 2006-04-09
well 56k rarely connected as 56k because of line static, poor lines, and distance to a telephone switching station.. way back in the day i never got over 34k, but at work i got 56k but the phone company switch station was right down the road

now on to your slow ethernet connection

my guess is that they have a cap on you so that you cant get higher speeds then 56k
the way internet works is there is  whats called an overhead
with 56k you connect at say 56k line speed, but transfer rates are just a portion of that, which is the 7k that you are getting.. thats the overhead

my 8mbps connection can download at a transfer rate of 1024kbps or 1mbps
the higher your line speed the higher the overhead

---

### Post by eriefisher on 2006-04-09
Well I don't have an answer for you because I don't know how that network is set up BUT I would kill for 7Kb/s. The best I ever get on my dial up modem is about 3.5Kb/s. I'm about 5 miles away from the nearest high speed connesction.

eriefisher

---

### Post by joshrobinson on 2006-04-09
[QUOTE=eriefisher]Well I don't have an answer for you because I don't know how that network is set up BUT I would kill for 7Kb/s. The best I ever get on my dial up modem is about 3.5Kb/s. I'm about 5 miles away from the nearest high speed connesction.

eriefisher[/QUOTE]

the phone line you are using, is it split to run to multiple phones? have you tried running a direct line from your computer into your phone box?

---

### Post by eriefisher on 2006-04-09
[QUOTE=joshrobinson]the phone line you are using, is it split to run to multiple phones? have you tried running a direct line from your computer into your phone box?[/QUOTE]

Thank for the tip, I'll give it a try.

eriefisher

---

### Post by ncappel1 on 2006-04-10
joshrobinson, is there anyway to change the proportion of overhead that I can use as transfer rate? Is something else using up the remaining 49 kb/s that doesn't really need it? Or is it out of my hands?

---

### Post by Mark_in_Hollywood on 2006-04-10
The TelCo is prevented from allowing all of 56K. The absolute max is 53K and I have never gone over 51666, top speed.

The rule has something to do with "cross-talk" or so I've heard.

I hope this helps.

---

### Post by joshrobinson on 2006-04-11
[QUOTE=ncappel1]joshrobinson, is there anyway to change the proportion of overhead that I can use as transfer rate? Is something else using up the remaining 49 kb/s that doesn't really need it? Or is it out of my hands?[/QUOTE]

you cant change the overhead it is how it is.. it sucks :-(

the other 49k is misc information, headers, requests, and other things you really dont see but have to happen

oh yeah.. and just tcp ip loss in general

---

### Post by steve.horsley on 2006-04-11
56k was only attainable on short good lines. Bad lines or long distances or interference from other nearby electricals all reduced the top speed.

Don't confuse bit/Sec and Byte/Sec. A modem does 56kbit/Sec. Given 8 bits in a byte, that's 7kByte/Sec. The numbers seem right.

This cap will be imposed by the network providers. There is probably nothing you can do about it - their kit is set up to limit your throughput, and clearly does so. But I guess you can do that rate 24*7 without them complaining. 

Yes, they are probably laughing all the way to the bank. But if you want the better service, you'll have to pay.

---

