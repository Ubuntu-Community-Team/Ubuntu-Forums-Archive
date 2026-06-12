---
title: "Ridiculously slow download speeds in Synaptic"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-03-10
When I am browsing the web, I easily get around 8 MB/s. 2.5 while downloading a file.

 It seems that on Synaptic, however, my downloads do not go over 25 KB/s. Is this a problem with the Synaptics server(s)? If not, how could I fix this?

---

### Post by mikewhatever on 2007-03-10
From my experience, 25 KB/s is very good. I remember it being less then 1 KB/s, like when I tried to install Amarok on Ubuntu. It said it would take hours, so I aborted. It seems that a lot of Ubuntu users need to get updates or install stuff.

---

### Post by ZeroWing on 2007-03-10
> **mikewhatever said:**
> From my experience, 25 KB/s is very good. I remember it being less then 1 KB/s, like when I tried to install Amarok on Ubuntu. It said it would take hours, so I aborted. It seems that a lot of Ubuntu users need to get updates or install stuff.


 Ack! Is this some kind of sick joke?!? Are you saying that the *only* way I could easily install programs is by using a very slow downloader? What if I want to install something that's say, 10MB? I have to wait over half an hour?! I've upgraded to cable to go *faster*!

 /sigh

 Alright. Is there any way at all that I could speed this up? Choose a closer server or something?

---

### Post by rolando2424 on 2007-03-10
hum... That's strange

I knew there was a part of the Ubuntu site where you could generate your source.list and that used the link that where close to you.

I'll see if I can find it.

EDIT: [FOUND IT!!!]("http://www.ubuntu-nl.org/source-o-matic/") :D

---

### Post by ZeroWing on 2007-03-10
> **rolando2424 said:**
> hum... That's strange

I knew there was a part of the Ubuntu site where you could generate your source.list and that used the link that where close to you.

I'll see if I can find it.

EDIT: [FOUND IT!!!]("http://www.ubuntu-nl.org/source-o-matic/") :D

 Uh... and how do you use this, exactly?

---

### Post by astrolabio on 2007-03-10
Don't use the archive.ubuntu.com standard american servers.

Try something closer to you or even on the other side of the world, just don't use them. 

I use the italian ones and i get 400K/s, the most i can get from my connection.

Use the link provided by the above poster to generate a new list.

---

### Post by ZeroWing on 2007-03-10
> **astrolabio said:**
> Don't use the archive.ubuntu.com standard american servers.

Try something closer to you or even on the other side of the world, just don't use them. 

I use the italian ones and i get 400K/s, the most i can get from my connection.

Use the link provided by the above poster to generate a new list.

 Again, how can I use the data provided by the link to my advantage?

---

### Post by rolando2424 on 2007-03-10
> **ZeroWing said:**
> Again, how can I use the data provided by the link to my advantage?

First, you choose your country from the list, choose the release and the architecture of the pc. Tick the box if you want to have access to the source code repositories.

Then, on the second screen, you have the first two option tick by default. You should those tick. Then you scroll down, choosing the repositories you want.

Then click on the "create sources.list" button.

Now some text should appear, just copy it add it (you can remove the ones that already are there, but make a backup of the sources.list) to your sources.list file (should be on /etc/apt/sources.list).

Then just type sudo apt-get update, and you should be good to go :D

---

### Post by MkfIbK7a on 2007-03-10
i get around 80 kbs/s on synaptic and apt-get so this is apparently a problem with your hardware or connection

or most likely as others have suggested your sources.list

---

### Post by mikewhatever on 2007-03-12
I thought the installer takes care of that, otherwise, why enter your location.

---

### Post by astrolabio on 2007-03-12
You're right. The problem is that when you choose you country the local repository are used. And sometime they are undersized for the traffic they receive.

So sometime is better pick another nation with bigger servers or less congestionated servers.

---

### Post by ZeroWing on 2007-03-12
Alright, now that I've put some local servers into synaptic, I'm getting downloads at around 250 KB/s.

 Thanks, all.

---

### Post by lancerocke on 2008-03-14
that source-o-matic is down

---

