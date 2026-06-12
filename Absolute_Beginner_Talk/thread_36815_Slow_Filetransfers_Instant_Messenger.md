---
title: "Slow Filetransfers Instant Messenger"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by granite230 on 2005-05-24
Hi, I use Gaim and ever since I installed Ubuntu the file transfers to/from other people are extremely slow!! It's not acceptable! It realy pisses people off and they're aborting the transfers because it takes forever! They even say that Linux sucks...

I tried google and I searched the forum but I couldn't find much useful info about this problem.

1- Anyone has any idea why the file transfers are so slow? It's an Instant Messenger problem only. 
2- Anyone know how to fix this?

---

### Post by Mez on 2005-05-24
It's probably because you're using an old version of it, or are working through a proxy.

Try using backports ([http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)) to upgrade to the latest version of gaim

---

### Post by granite230 on 2005-05-25
Well, that didn't work ;)

Thought so because aMSN also has this problem and I think all the Instant Messengers have it. But I'm still wondering what's the cause of this.

---

### Post by Sionide on 2005-05-25
I use Gaim 1.3.0 AND I connect through a proxy and file transfers are faster than on normal MSN. I don't know why yours would be going slowly, I believe the major slow down is when the file hits the Microsoft servers - they're the slow bit. Get your friends to download xchat and DCC the file to them, then you're getting a literal direct connection rather than connecting across the Microsoft servers. If you do that, the only thing which will affect speed is your upstream and their downstream.

---

### Post by sas on 2005-05-25
As a stab in the dark - do you need to open certain ports on your router? Or have the person on the other end configure theirs (if they're using gaim, msn messenger does it automatically)

---

### Post by granite230 on 2005-05-25
There are no routers, it's a fresh install, no proxies, no nothing... it's just slow as hell and I realy have no clue what's causing it. The only thing I can think of is that Microsoft is somehow slowing down my file transfers (maybe they want me to get back to Windows and use MSN Messenger again?).

One of my friends also uses Linux and has the same problem. I read some stuff on the internet but found nothing useful. 

Is nobody else here experiencing the same problem?

People here are complaining almost every day and my friends don't know much about computers. They realy don't want to install Xchat just to send me some files. They just want this to work the way it should, and so do I.

---

### Post by poofyhairguy on 2005-05-26
[QUOTE=granite230]. 

Is nobody else here experiencing the same problem?

[/QUOTE]

Yep. In fact when I read your post I thought "wow, this person actually gets file transfers in GAIM to work at all? I assume they never did."

No matter if the fault is MSes or Gaims this is a problem that I think no one has the answer to.

Time for you to decide what you value, what you need and chose that. We won't hold it against you.

---

### Post by Roberto75 on 2005-06-16
The rpoblem would come from the code inside gaim.... from what i gathered in google
gaim client can't create a direct link to another msn client, and file transfer has to go throught the msn server, therefore slow ul / dl.
on another thread someone said that they upgraded to the latest version of gaim and that solved this problem.... only he had to go manual on the instal... maybe worth the effort.
I am looking into alternate options to gaim and will revert with good leads if I find some.

cheers!

---

### Post by Roberto75 on 2005-06-16
by the way here what gaim team has to say about that on [http://gaim.sourceforge.net/summerofcode/](http://gaim.sourceforge.net/summerofcode/)

***** QUOTE
MSN File Transfer
The MSN protocol supports several different file transfer methods which are used under different network conditions. Currently, Gaim only supports a method that transfers through the MSN servers. While this is guaranteed to work under any network condition (even if both sides are behind NAT devices, for instance), it is unbearably slow.

Your task this summer is to implement at least one other MSN file transfer protocol: one that directly connects the two clients. You will also need to provide a mechanism that will easily fallback on the slow through-the-server method in case your new method fails. This may involve reverse engineering, but there are other free software implementations you may use as a reference.***** END QUOTE

it is what they call their summer project linked with google.... anyone up for the job? :)

---

### Post by mariosx on 2007-07-07
well... i had the same problem, (i know this reply is a little late lol), but i used to use GAIM, for my msn messenger account, and transfer rates were too slow... 

but when i used aMSN messenger, i noticed that tranf. rates were normal, and i got full speed of my Internet connection ;)

i definitely  recommend it :)

---

