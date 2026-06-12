---
title: "Streaming to shoutcast"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by TheFluff on 2006-11-29
Hello,

First of all, I'm very new to Linux/Ubuntu.
I'm trying to find a solution to stream audio to a Shoutcast server. 
On the site of Shoutcast I could download a plugin for linux/macosx... I've done so, but I don't know what to do with it, or how to run it whatsoever...

Then I searched some more and tried IceCast... 

so I downloaded the tarball and extract it on my Ubuntu desktop, open up a terminal, navigate to that folder and typed what was in the readmea: 

./configure

That did not work. I am logged in as root but i get an error saying that the compiler cannot make an executable or something. 
I looked in the logfile, but don't get anything what's in there.

so the rest of the commands won't work as well (make, make install) 

Is there an easy way like in Windows (Winamp => Shoutcast pluging => ready)?

on a sidenote: where should I put my programs and stuff? Is there a standard folder like in Windows Program Files?

---

### Post by KingBahamut on 2006-11-29
sudo apt-get install xmms-liveice I think. 

Thats the icecast plugin for XMMS media player.

---

### Post by TheFluff on 2006-11-29
didn't find that... :/

Do i have to download something before that? or is it supposed to work none the less?

That linux stuff is getting me scared of it :(

---

### Post by KingBahamut on 2006-11-29
nope. 

sudo apt-get install xmms-liveice 

then configure it in XMMS via the plugins manager.

---

### Post by John.Michael.Kane on 2006-11-29
This may help 
[http://www.ubuntuforums.org/showthread.php?t=76658&highlight=streamtuner](http://www.ubuntuforums.org/showthread.php?t=76658&highlight=streamtuner)

---

### Post by TheFluff on 2006-11-29
weird

second time it worked!

I changed the server to the masterserver instead of the server for belgium...

anyway, I'll check it out!

thnx!

---

### Post by TheFluff on 2006-12-01
I wasn't able to find out how to stream my Line In with it to a shoutcast server!

Any help would be apprecieated...

---

### Post by Kratos on 2007-01-01
Use Aptitude/Adept/Synaptic to install idjc (Internet DJ Console) it allows you to stream to any shoutcast, icecast, or ice2 server and it works pretty darn good! It has some funny dependancies, (namely Jack Audio Connection Kit) but it's worth it. :)

EDIT: It seems I was confused in my sources. IDJC isn't in the repositories [yet]. I am, however in talks with the local MOTU to have it added. In the meantime, here is the [site]("http://www.onlymeok.nildram.co.uk/"), where you can download the source code and compile it yourself.

---

