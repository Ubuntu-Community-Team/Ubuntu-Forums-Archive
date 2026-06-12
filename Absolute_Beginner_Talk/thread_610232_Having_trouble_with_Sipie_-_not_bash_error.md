---
title: "Having trouble with Sipie - not bash error"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by brooklyn11218 on 2007-11-11
Hi,

I recently installed sipie so i can listen to sirius. I followed the instructions in different threads and patched the file to get passed the gutsy bash error.

It was working fine for a few weeks, now when i open it it opens up fine and even shows the popup of whats playing in the channel...but i can't hear anything anymore.

My speakers work fine, and I have changed anything that I am aware of..it just stopped working. can anyone PLEASE help me..I can't live without my sirius.

---

### Post by brooklyn11218 on 2007-11-11
bump

---

### Post by rubadub on 2007-11-11
I havnt got sipie to work in months but i just found this hack recently that will get it working. Go to the last page of this thread [http://ubuntuforums.org/showthread.php?t=284893&highlight=sirius](http://ubuntuforums.org/showthread.php?t=284893&highlight=sirius) to get it working.

---

### Post by daybreaker on 2007-11-12
what happened to Sipie? I'm having the same issues. Did Sirius update something a few days ago and break it?

---

### Post by pviglucci on 2007-11-12
Same problem here.

---

### Post by GMeola on 2007-11-13
Same problem here... 
I have been using Sipie for a long time.  Used it on Fedora 6 & 7, more recently on Feisty and now Gusty.  Had to do the hack rubadub posted above to get it working on Gusty.  It just stopped working the other day.  I use it on multiple ubuntu installs.  All of them are broke.

Doing a ps -ax|grep mplayer, shows no mplayer streams.  
Sirius must have changed the login procedures.

Oh well... mplayer-plugin for now.

~Gary

---

### Post by daybreaker on 2007-11-13
After some reading, I saw a few comments on the sourceforge bugs list talking about how a few days ago, Sirius switched to ASX streaming. So the stream URL is wrong in Sipie until Sipie gets updated. Thats why the song info still comes up, but the stream doesnt play.

---

### Post by redfireant3 on 2007-11-24
i found an extension the works and you can choose which program runs it
[https://addons.mozilla.org/en-US/firefox/addon/446?id=446&application=firefox](https://addons.mozilla.org/en-US/firefox/addon/446?id=446&application=firefox)
i am using vlc to handle windows media files

---

### Post by Spr0k3t on 2007-11-25
> **redfireant3 said:**
> i found an extension the works and you can choose which program runs it
[https://addons.mozilla.org/en-US/firefox/addon/446?id=446&application=firefox](https://addons.mozilla.org/en-US/firefox/addon/446?id=446&application=firefox)
i am using vlc to handle windows media files

Thanks for that.  I was trying to figure out how to listen to my favorite stations just yesterday.

---

### Post by Shrav on 2007-11-28
Found the solution here. Works fine.

[http://sourceforge.net/forum/forum.php?thread_id=1869165&forum_id=697500](http://sourceforge.net/forum/forum.php?thread_id=1869165&forum_id=697500)

---

### Post by llamakc on 2007-11-29
Thanks for the SF link. Perfect fix.

---

### Post by prosonik on 2007-12-09
What did you do to fix the problem?  I rebuilt mine from svn,
and I still getting the same exact problem. I'm using the sirius plugin for firefox right now,
but I'd love to get it working, so i can use it with mythtv.

pro

---

