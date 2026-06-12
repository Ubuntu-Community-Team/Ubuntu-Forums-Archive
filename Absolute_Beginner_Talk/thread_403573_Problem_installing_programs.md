---
title: "Problem installing programs"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by FerBatista on 2007-04-07
I'm a new Ubuntu user and been trying to install new aplications, somehow the "add remove aplications" option doens't work, the synaptic manager doesn't also, in both situations they start downloading the packages but they just hang at that moment, never making the download. 
It's like my net connection had some problem, but it isn't that as firefox works very well.

Any thoughts?

I'd really appreciate the help.

BTW I'm using Edgy on a AMD64 if that's any help.

---

### Post by jvc26 on 2007-04-07
Do you get any errors? (Messages wise?) What are you trying to install?
Il

---

### Post by FerBatista on 2007-04-07
Thank you for the reply.

What it says is that the repository may not be available anymore, or that due to a network problem it may not be possible to connect (this is a portuguese message so I'm translating as best I can).
I changed the repository in synaptic, but the result is the same.

this is the adress it tries to connect and the message
[http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Não foi possível ligar a archive.ubuntu.com:80 (1.0.0.0), a conexão expirou

it also doesn't work when I try to update the applications list.

I also think this must be more a connection problem than a repository problem, because GAIM also isn't able to connect. I haven't tried other things yet so I don't know what else.
Is there anything that prevents some applications from connecting to the net?
I ask because I had to use the tutorial to disable IPV6 to be able to use firefox, maybe there's any other thing I need to do for other programs.

Thanks again

---

### Post by zvacet on 2007-04-07
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by FerBatista on 2007-04-07
Thanks, but it doens't go any further than 0%. Than after a while there's an error message saying that it couldn't connect to archive.ubuntu.com

---

### Post by FerBatista on 2007-04-08
It's working now, I find another post describing my problem. Turns out it's a common thing. 
Here's the thread:
[http://ubuntuforums.org/showthread.php?t=401598&page=2&highlight=synaptic+problem](http://ubuntuforums.org/showthread.php?t=401598&page=2&highlight=synaptic+problem)

Thanks everyone.

---

