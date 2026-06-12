---
title: "X-Box live"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by aetheist on 2005-10-03
Alright,

I've only just really started using linux, two days ago.  It took me a fairly long time, setting up my Speedtouch 330 USB modem to work well on ubuntu, but I made it happen.

However, I'm not exactly sure how to get x-box live working, as I've got a direct cable from my pc to my x-box.    How would I set this sorta network up?

Any help would be greatly appreciated. (Im using hoary hedgehog)

---

### Post by nitricacid on 2005-10-03
This is a linux forum. NOt an X-Box Tech Support line.
Read the X-box manual or call the X-box support line.

Unless you are putting linux on your x-box i don't see why you posted asking for help on how to get onto x-box live.

~I am not Flaming i am simply stating the Obvious~

---

### Post by aetheist on 2005-10-03
well, I believe the actual configuration on the x-box is set up.  All I really need to know is, how to set-up the ethernet so it picks it up and allows to use my running internet connection on the PC.

I'm not really asking for x-box assistance itself.  I mean, the x-box essentially could be another pc, linked to mine, via the cable for the same purpose.

---

### Post by Ken.Lank on 2005-10-03
Yes, it sounds like he needs to know how to setup his Ubuntu box as a NAT router so that his XBox can connect to the internet.  I don't know how to do this, but someone here should be able to once they grasp what you are trying to do.

---

### Post by aetheist on 2005-10-03
"Yes, it sounds like he needs to know how to setup his Ubuntu box as a NAT router so that his XBox can connect to the internet. I don't know how to do this, but someone here should be able to once they grasp what you are trying to do."

Yes,  exactly.  

Im not too familiar with the terminology for linux etc. but I believe it would be the same principle of setting up a direct link between two computers via a ethernet cable.

xbox ------------- PC 

When the PC is switched on and connected to the net, the XBOX should be able to leech my connection via the cable.  Thats, basically what Im trying to setup.

---

### Post by nitricacid on 2005-10-03
y are you linking it to the computer, Are doing some Dev work with your x-box and linux ?
If you are connecting to X-box live you want the x-box connected to the Router\modem.

maybe i should just shut up since i really don't know what you are getting at with trying to connect to x-box live.

---

### Post by DrMoxie on 2005-10-03
I think that aetheist is looking to do is Internet Connection Sharing; [here's a thread on these forums]("http://www.ubuntuforums.org/showthread.php?t=65900&highlight=internet+connection+sharing") and [another one over at Fedora]("http://fedoranews.org/ghenry/gateway/") that should help get you started.  Though, it might be easier to throw money at this problem and pick up an el cheapo router. ;)

---

### Post by PsyberOneZero on 2005-10-03
```
sudo apt-get install firestarter
```
When you first set up firestarter Just follow these steps
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=2692&stc=1&d=1128362930[/IMG]
Select your incoming port (whatever you have setup right now to get internet access, also you might want to check the DCHP box on the bottom)
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=2693&stc=1&d=1128362930[/IMG]
Now here you pick which device will be connected to the XBox
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=2694&stc=1&d=1128362930[/IMG]
That should get you going, just save it and start.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=2695&stc=1&d=1128362930[/IMG]

---

