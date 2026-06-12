---
title: "Doom3 Serial Solution"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-03
ok i bought Doom3 from my local game shop for a bargain price!
knowing it works native on linux.

i got the doom installer and copied the .pk4 files. great! :D

but when launching the game it asks for my CD key, i entered the one loacted inside the case, it refused it!

i tried again in caps, it refused.

so i tried to install in Win XP, it worked!? it accepted the same code Linux refused.

i tried in linux again and it failed.

i found a solution. i went through the  006.pk4 and 007.pk4 files and deleted the Mainmenu files.

locaed in GUIS > mainmenu

this worked and is legal since i DO have a VALID cd key.
this can help if anyone else is having trouble with refusing CD's kleys.

i am not encouraing piracy, for use with a genunine CD key

thanks

---

### Post by skymera on 2007-10-03
little feedback on my discovery? :lol:

---

### Post by Henry Rayker on 2007-10-03
Considering your discovery is for a 3 year old game, I'd say it's more than reasonable that you didn't get a response within 30 minutes....

---

### Post by skymera on 2007-10-03
yeah well...its new to me :wink:

---

### Post by ronaldprettyman on 2008-02-09
much appriciated I lost my packaging and was starting to think my hand writing was worse then i though, tried my key in windows and it worked fine, will try this method out, thanx
EDIT: Worked!!! But it does the same thing again when I click new game

---

### Post by SnakeHips on 2008-03-01
I'm having the same problem ,have installed sudo sh ./doom3-linux-1.3.1.1304.x86.run and copied the .pak files to the default location usr/local/games/doom3/base

So........the game fires up and the CD KEY screen arrives ,no matter what i do it WONT accept my valid CD key....

any ideas anyone?

---

### Post by skymera on 2008-03-01
read my first post.

---

### Post by Anduu on 2008-03-01
A little tip....

Check the permissions of your /home/<username>/.doom3 folder.Depending on how you installed it(ie.. using sudo....)you may not have permission to write to it.

---

### Post by SnakeHips on 2008-03-02
> **skymera said:**
> read my first post.

I did!  Was rather looking for a *fix* rather than a workaround..............anyhow ,do you mean remove ALL the files in both folders?

---

### Post by skymera on 2008-03-03
AFAIK just the mainmenu files

---

### Post by ahaslam on 2008-03-03
What version of the client are you running?
With the latest version it authenticates the key with an ID server (192.246.40.244).
So surely you need to drop that connection with iptables too?

---

### Post by NR1224 on 2008-03-31
if this is still being read, what i did was to fall back to the 1.1 installer, works like a charm!:popcorn:

---

