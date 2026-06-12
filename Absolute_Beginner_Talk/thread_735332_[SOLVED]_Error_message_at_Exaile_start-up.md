---
title: "[SOLVED] Error message at Exaile start-up"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-25
When I start Exaile, I get the following error message: 

"Shout library could not be loaded. You need libshout 2 and shout python bindings. Streaming will not be available"

I looked out for both in Synaptics but couldn't find them. Does anyone know what I should do?

Thanks.

---

### Post by kellemes on 2008-03-25
Please type the following in the terminal..
```
sudo apt-get -f install
```

How did you install exaile?

---

### Post by al.adab on 2008-03-25
thanks. This is what I get: 

~$ sudo apt-get -f install
[sudo] password for daniel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I still get the same message when I open Exaile. What could the reason be?

---

### Post by al.adab on 2008-03-25
sorry I've forgotten to say that I installed Exaile through Synaptics

---

### Post by Paqman on 2008-03-25
Looks like the version of libshout in the repos is [libshout3](http://packages.ubuntu.com/gutsy/libshout3).

Shoutcast support is a plugin, isn't it? Have you tried reinstalling that plugin? (I might be thinking of Amarok though...)

---

### Post by al.adab on 2008-03-25
That's right, shoutcast is a plugjn. I tried to re-install it, but nothing changes. Here's a screenshot of my synaptics if I search for libshout

---

### Post by FrozenFox on 2008-03-25
shout python bindings

..are what you need. You have the shout libraries. I looked for the shout python bindings for some time to no avail, and compiling them failed miserably too, for reasons that showed no relation to dependencies. Debian doesn't have it in their repos either. You might as well install xmms and the xmms-liveice plugin instead and save yourself the trouble until an appropriate package is released.

(Fortunately, arch has this dealt with :p)

---

### Post by al.adab on 2008-03-25
I've got XMMS. Can I at least get rid of the error message on Exaile in any way?

---

### Post by FrozenFox on 2008-03-25
Try going to the plugin manager in exaile and "uninstall" the ice/shoutcast plugin. Then close the program via file->quit ("the right way") and it shouldn't nag any more.

---

### Post by al.adab on 2008-03-25
Uninstalled Icast Streamer, Shoutcast Radio, and Python Console. Error message is gone. Does this mean I won't be able to listen to the radio through Exaile?

---

### Post by FrozenFox on 2008-03-25
Er, the icast plugin is for streaming yourself (ie send your currently playing stuff to a shoutcast or icecast-server or icecast2 server or whatnot so someone else can listen in), not receiving streams. I'm not sure if the others (that allow you to receive streams) need the shout bindings. Please try installing them one by one and see if they do yourself. I haven't re-added ubuntu hardy to my arch boot menu yet to go see myself, hehe.

---

