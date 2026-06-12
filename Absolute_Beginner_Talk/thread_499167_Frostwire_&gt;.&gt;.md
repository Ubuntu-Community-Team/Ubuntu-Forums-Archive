---
title: "Frostwire &gt;.&gt;"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Hickler on 2007-07-12
So, I've seen, one other person complain about this but nobody answered him, I'm hoping the same will not happen to me. I installed the Linux version of Frostwire and started it up. Everything seemed fine until the actual Frostwire window opened, all white :/ like nothing... it was still responding because the bar at the top was fine and I have the right Java version. Can anyone help?

---

### Post by cAllison on 2007-07-12
Unfortunately I cant offer much in the way of help. But when I installed frostwire on my edgy install I was having some wierd stuff happen too...

After starting up frostwire it would act like it didnt save any of first run settings I put in, so it would ask everytime for them (Like each time I loaded it was the first run). Then after filling out all the settings it would go to load up the main window, and then crash.. 1 out of ten tries it would stick and work fine though. 

The wierd part... it's basically fixed itself. After this going on for about 2 weeks, it now works fine.

I would however recommend reinstall Java and Frostwire after a good uninstall and cold boot.

---

### Post by deadgobby on 2007-07-12
The java app is a ram eater. If you have like 256 megs of ram, it will run dog slow. 
Gobby

---

### Post by Frak on 2007-07-12
Like deadgobby said, JVM is a Heavy resource occupier. Just wait for it to reload.

---

### Post by randytuggle on 2007-07-12
I don't know the exact reasons for you wanting to use frostwire - but if it's music downloads you desire, use Opera. It has a built in IRC client which is really good. You could also use streamtuner and streamripper to listen to music and make mp3 files. I gave up on java apps like frostwire long ago. They usually have several bugs and just waste time when they do these things.

---

### Post by Hickler on 2007-07-12
> **randytuggle said:**
> use Opera. It has a built in IRC client which is really good.

Opera as in the web browser?? Otherwise, thanks for your replies, I will try them.

EDIT: I have 512MB of RAM..

---

### Post by Hickler on 2007-07-12
Btw, how do I uninstall Frostwire.. and Java for that matter..

---

### Post by Frak on 2007-07-12
sudo aptitude remove frostwire sun-java5-bin

---

### Post by Hickler on 2007-07-12
Sudo aptitude? O.o So sorry for the lack of pc knowledge, just started to get used to Linux.. :/

---

### Post by ThrobbingBrain66 on 2007-07-12
using aptitude instead of apt-get allows for better dependency removal, assuming you used aptitude to install the packages.

Are you using Beryl/Compiz by any chance?  There are known conflicts between Java5/6 and Beryl and Compiz that cause the symptoms you describe.

[http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java) <----temporary workaround

Java6 update 1, only available in Gutsy I believe, fixes this problem.

---

### Post by deadgobby on 2007-07-12
If you are looking for a p2p that runs off the Gnutella servers. There is GTK-gnutella. It is not a pretty app like frost, but it grabs the same data. You can install that app in synaptic.

---

### Post by Hickler on 2007-07-12
Hmm, using Compiz I believe, the desktop effects...

---

### Post by Hickler on 2007-07-12
Hehe, that would do it! I just turned off desktop effects and now it works, kinda annoying though.. 0_0

---

### Post by ThrobbingBrain66 on 2007-07-12
Yeah, the Desktop Effects are Compiz.  Have you tried the link I gave in my previous post? It works really well and once Gutsy is released in October, you won't have to worry about it anymore.

---

### Post by Hickler on 2007-07-12
I will look at it now, so once I do this, Frostwire should work fine with compiz?

---

