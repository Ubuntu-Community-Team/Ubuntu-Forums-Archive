---
title: "[SOLVED] Problem with package manager"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Coppper on 2007-12-31
Hi , 

I have a problem with Package Manager , I think it cannot reach the server . It pops up 
the window saying downloading 1 out of 17 , but it never finishs.

No problem with mozilla to access to internet and from terminal I can ping google.com.

When I type  sudo apt-get update I just get :

0% [Connecting to archive.canonical.com (1.0.0.0)] 

and nothing more

---

### Post by mikewhatever on 2007-12-31
How are you connected? Proxy? Router?

---

### Post by Coppper on 2007-12-31
Router

---

### Post by mikewhatever on 2007-12-31
Well, have you tried pinging archive.canonical.com? If you get a reply, post your sources list <sudo cat /etc/apt/sources.list>

---

### Post by SOULRiDER on 2007-12-31
Its possible that the server is down at the moment. Try in a few minutes.

---

### Post by Coppper on 2007-12-31
Yes , and no response.

Yesterday I  saw my source.list and i had almost everything commented  (#) . 

I made a backup of the file and create a new one with all the sources uncommneted. ( the ubuntu one's)

With this change I get the message 5 out of 37 and then .. hanged

---

### Post by Menthol on 2007-12-31
Have you enabled everything in synaptic ?  I had a problem with sources once and I went here : [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

It makes you a new one

---

### Post by Coppper on 2007-12-31
I installed Gutsy a week ago and i have tried several times and nothing. 

I had a problem with the ipv6 stuff , changed fierefox , create a bad_list & and blacklist it , and 
since then no problem with firefox but no update manager !!

---

### Post by Coppper on 2007-12-31
Menthol, i have been watching it and  mine is like the one you mention ....

---

### Post by Menthol on 2007-12-31
hmm, may just be a server problem at the moment.  Unfortunately I cant check for you becasue I'm at work.  Maby just give it an hour or so and check it again.

---

### Post by Coppper on 2007-12-31
The first day I  thought it was the server , but i try every day and never managed to connect  !!!

---

### Post by Menthol on 2007-12-31
Have you tried changing the area/server you connect to ? 
I think theres an option in synaptic to change where you download from.  Again I cant walk you through where because I'm at work but if you dig about in synaptic I'm sure you can change the area to global somewhere

---

### Post by Coppper on 2007-12-31
I will try that this evening . It's only adding  the country name , i.e. 'es.' , before the server name ??

---

### Post by Menthol on 2007-12-31
I think so.  There should be a selection box in synaptic to change it, just select another one and see what happens :-)

---

### Post by Coppper on 2008-01-01
Ok, solved , It was a DNS problem. Everything working fine with OpenDNS !! 

Thanks all !!

---

