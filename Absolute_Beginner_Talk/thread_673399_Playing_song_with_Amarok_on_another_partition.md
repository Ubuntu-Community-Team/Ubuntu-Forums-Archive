---
title: "Playing song with Amarok on another partition"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by jimbojimbo on 2008-01-20
I have a dual boot setup with Vista and Ubuntu (7.10).  Since I only have 15gb dedicated to the Ubuntu partition, all of my music is on the Vista partition.  When I first try to play a song in Amarok it says "local file not found".  To fix it, I need to go into my other partition and enter my password (it says it needs administrative priviledges to access that partition).  After logging in, it works fine.

The problem is that I have to do this every time I log into Ubuntu and want to play music.  It also breaks my NowPlaying Screenlet, because that only works if Amarok is opened first (I have them both set to startup on login, which also works fine).  

So if I want to get it set up the way I want, each time I log in I have to go into the Vista partition, enter my password, then go into the screenlets application and activate that... kind of a pain to do every time I turn on my computer, amplified by the fact that I can't hibernate Ubuntu (which is another problem altogether).

So... the only way I could think of avoiding this is to log in as some sort or administrator to avoid needing to enter my password, but since I'm pretty new to linux, I'm not sure I want to do that.  I'm not sure how to do that anyway.  

Is there a way to just avoid inputting my password when trying to access another partition?

---

### Post by forestpixie on 2008-01-20
it could be that the vista partition doesn't mount with the right permissions - although I'm not completely sure

can you post these
cat /etc/fstab
sudo fdisk -l

---

