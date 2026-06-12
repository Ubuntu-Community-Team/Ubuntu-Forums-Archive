---
title: "synaptec bandwith problem"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by natirips on 2008-01-19
Is there a way to stop synaptec from using all my bandwith when downloading packages?

---

### Post by Paulmd on 2008-01-19
> **natirips said:**
> Is there a way to stop synaptec from using all my bandwith when downloading packages?

Maybe if you asked this in the networking forum, you may get a complicated answer. Bandwidth throttling is something only people with large networks even bother with.

Certainly not easily. How much bandwidth do you have? (dialup or highspeed?)

Usually with highspeed, you can still surf more or less normally.

---

### Post by natirips on 2008-01-19
> **Paulmd said:**
> Maybe if you asked this in the networking forum, you may get a complicated answer. Bandwidth throttling is something only people with large networks even bother with.

Certainly not easily. How much bandwidth do you have? (dialup or highspeed?)

Usually with highspeed, you can still surf more or less normally.

It's 2048Kbits download, but it's shared with 4 other computers. So when someone is trying to watch a youtube video for example, it gets blocky and their downloads are slow too, it's not like I really need 200Kbytes trasfer all to myself just for synaptec

---

### Post by gerscht on 2008-01-19
Someone mentioned Trickle in debian forums:
[http://forums.debian.net/viewtopic.php?t=275](http://forums.debian.net/viewtopic.php?t=275)
You might want to give it a try (I haven't used it yet, but I might try that as well...)

---

### Post by natirips on 2008-01-19
lolz, I installed trickle and went to test it, but it turns out I've allready installed ALL availible packages greater than 500k there are :S. Thanks anyway...

---

### Post by natirips on 2008-01-19
I tested it at last, it works, but the application still ate a little bit more bandwith than I specified, and it ate my CPU while downloading, but at least it didn't take over all the bandwith.

For those who might be interested: the program is called Trickle (I installed it via synaptic), open up console and type "trickle" to get usage discription. It's rather simple though:
for example:
"sudo trickle -d 50 synaptic" will run Synaptic with 50-80 KBytes/sec download speed.

---

### Post by smartboyathome on 2008-01-19
By the way, System > Administration > Software Sources (Also available through synaptic via Settings > Repos) > Download from dropdown > Other > Select best server should help.

---

### Post by natirips on 2008-01-20
> **smartboyathome said:**
> By the way, System > Administration > Software Sources (Also available through synaptic via Settings > Repos) > Download from dropdown > Other > Select best server should help.

The problem was it was too FAST, not to slow.... :S

---

