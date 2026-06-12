---
title: "Enabling extra repors in sources.list"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-16
Hello,

I've just installed Ubuntu 7.10 with Xubuntu... did the repro update and updated all software thru Xubuntu.

I know that I need enable extra repros... I have found  the procedure to open the terminal and edit the sources.list.

When I issue the this command:
gksu gedit /etc/apt/sources.list

Nothing happens.  It either:
1)  sources.list do not exit
2)  I'm using the wrong command
3)  gedit not installed

Can someone tell me what I might be doing wrong?

Thanks!

---

### Post by banewman on 2008-03-16
In xubuntu it is 
gksu mousepad /etc/apt/sources.list
gedit is the ubuntu text editor - mousepad is the text editor that comes with xubuntu
:)

---

### Post by housam on 2008-03-16
did you followed this steps [[COLOR="Red"]_http://www.psychocats.net/ubuntu/sources#gutsy_[/COLOR]]("http://www.psychocats.net/ubuntu/sources#gutsy")

---

### Post by bumanie on 2008-03-16
Follow this guide [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Also enable repositories via System--> Administration--> Software Sources Tick the first 4 boxes and check out the third party tab and tick anything that is in there.
Also type in terminal
> sudo apt-get install build-essential
The above should sort out the majority of problems you are experiencing.

---

