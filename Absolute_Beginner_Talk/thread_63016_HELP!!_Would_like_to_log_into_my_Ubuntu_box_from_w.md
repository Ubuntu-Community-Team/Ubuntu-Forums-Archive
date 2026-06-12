---
title: "HELP!! Would like to log into my Ubuntu box from work"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by thundertoad on 2005-09-06
Hey y'all,

I was wondering if there was a way for me to **log into my UBUNTU box from work**. I am on dynamic dns so I figured **[www.dyndns.com](www.dyndns.com)** would be a perfect way to always be able to find my machine online. Now I am running** Ubuntu for AMD64** and was wondering what the procedure was to log onto **the _same_ session** I have open at home ... but at work... so that I can like start a download on my amule or tweak my system or whatever.

Anybody have any ideas?
Any input would be mucho appreciated.
and please mention as many commands and or apps I have to use... I am a total n00b at this.
thanks.

ThunderToad

---

### Post by KingBahamut on 2005-09-06
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/) 

x11vnc is the best way to go about this Im thinking. 

update your repos and so forth , doing what it says in [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then use synaptic to install x11vnc 

or 

apt-get install x11vnc 

Be sure to read all of x11vnc's documentation, but it shouldnt be hard to get him going.

---

### Post by the_purulent on 2005-09-06
You can also enable remote desktop (as shown in the ubuntu guide) and then download vncviewer for windows or whatever o/s you use at work.

Type in your IP and voila! (be sure to turn off require confirmation in the remote desktop settings or else you will need to have someone click 'ok' on your ubuntu box to accesss it).  I have set this up (very easy) and it works great!

-Clayton

Edit: Here is the link with a great explanation.

[http://www.ubuntuguide.org/#remotedesktop](http://www.ubuntuguide.org/#remotedesktop)

---

### Post by thundertoad on 2005-09-06
Thanks King, Thanks Clay,

Clay I think your solution is pretty much the simplest... I will check tomorrow if there is a vncviewer for mac... that thing is a bsd box so there probably is a vncviewer somewhere in there... now if I can only figure out how to setup that stupid ez-ipupdater... dunno what is so ez about it.. then again I'm always trying to configure stuff at the end of the day after a long chunk of work... 

again thanks.. i'll give both ways a try and tell you how it worked out... muchos gracias.

ThunderToad
(protecting the true north... strong and free)

---

### Post by thundertoad on 2005-09-07
Found a VNC viewer for Mac OSX called Chicken of the VNC. I found the remote desktop client in the system > administration section... is there a specific port I have to  set up using the remote client to get this thing to work... and will this log me into the existing session so that I can check the apps already running?

this is the command I am supposed to use:
vncviewer localhost.localdomain:0 

where do I put the url or ip to get this to work

thanks,
ThunderToad

---

### Post by A-star on 2005-09-07
Install freenx on your pc, it will work faster and better then any VNC connection.
Do a search on the forums for more info.

---

### Post by thundertoad on 2005-09-07
found freenx for ubuntu amd64 and installed it but it seems a tad complicated. Like I said I am a total n00b. I mean I cant even configure Ez-ipupdater... and its got an EZ in front of it.

On a side note I spoke to a south african friend of mine who speaks a few african languages... it turns out I was pronouncing ubuntu wrong.. I was pronouncing it You-buntoo... where as its proper pronunciation is OObuntOO... interesting.

I will try to connect to my computer from another computer today... I will try vnc just for convenience and speed but if freeNX is faster then I'll definitly give it a try.

Thanks you guys... you've been alot of help... and I hope I get this thing to work soon... It would save me tons of time.

ThunderToad

---

### Post by bugmenot on 2005-09-07
There's a howto on the wiki about freenx. Usually it should be enough to install the package. You wont be able to connect to the same session that's running at home with plain NX though. It will spawn its own sessions.  [There's](http://www.nomachine.com/download.php) also a native OSX client from the creators of NX.
Another thing you can do is combining VNC (even x11vnc) with NX for a sizable speed boost. But thats a step away. Actually, again x11vnc is a tad slower than VNC running in its own session.

But get VNC to run first.

---

### Post by thundertoad on 2005-09-07
Well the thing is that the thing I need most is to connect to an existing session at home. cause I usually leave amule downloading and most of the time I have to wait till I get back home before I can install something on my machine that I found out about at the forum... This way I can test it without having to go home...

Thanks for all the great advice you guys.
I will let you know how it works out... but if someone else has any more suggestions... please ... by all means... increase the knowledge base.

again... thanks for all the help.
ThunderToad

---

### Post by bugmenot on 2005-09-07
As you wish. I would drop amule in favor of mldonkey. The crucial difference is that mldonkey downloads with its "core" running as a daemon in the background. You then connect to the core with a "GUI" running on another system. Or, in your case, through its "web interface". No need to have the GUI on the same machine. It also connects to other networks and supports BT.

---

### Post by thundertoad on 2005-09-07
[QUOTE=bugmenot]As you wish. I would drop amule in favor of mldonkey. The crucial difference is that mldonkey downloads with its "core" running as a daemon in the background. You then connect to the core with a "GUI" running on another system. Or, in your case, through its "web interface". No need to have the GUI on the same machine. It also connects to other networks and supports BT.[/QUOTE]
 Yeah I have MLdonkey or is it MIdonkey... whichever.. I have it installed but havent used it... I am going slowly but steadily. 
I tested the Remote desktop thing and it works fine... I actually got a friend to log onto my machine from his place... and that was quite the freaky experience... but the thing is that he got discoed after a while... so we spent some time trying to set up ssh but it was too late to get any progress ... so now I'll go and try to figure out this ez-ipupdater...  went and got me a ups today.. wanted one of those intelligent ones that will shut your system down before the battery dies... got one but its some freaky italian make. anyway... thanks for the p2p tip... I am still recovering from their shutting down [www.the-realworld.de](www.the-realworld.de)... very upset.... 

ok i'll tell you how well it works tomorrow from work... and thanks for all the input
ThunderToad

---

