---
title: "[SOLVED] Best Torrent Program:Your Opinion"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-26
[SIZE="3"]Hi[/SIZE]!:)
[SIZE="3"]
I am looking for a good torrent client which does not require port forwarding and is really fast. Utorrent made me mad. I couldn't forward the port properly. Oh and yes, encryption support would be great!

Thanks[/SIZE]:popcorn:

---

### Post by jan quark on 2008-03-26
what about deluge??
[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by TeoBigusGeekus on 2008-03-26
What steps did you take to forward the port? I use &#956;torrent without any trouble, in fact I prefer it from all other bittorrent apps...

EDIT:
[http://ubuntuforums.org/showthread.php?t=700571]("http://ubuntuforums.org/showthread.php?t=700571")
This thread would be of interest to you.

---

### Post by Google Spider on 2008-03-26
> **TeoBigusGeekus said:**
> What steps did you take to forward the port? I use &#956;torrent without any trouble, in fact I prefer it from all other bittorrent apps...

I followed the guide at portforward.com . I tried to get a static IP by configuring my router, but then was unable to pull webpages, so changed all settings back. 

Is it worth to run Utorrent in Wine when we can get other torrent programs which will run natively in Linux ?

---

### Post by TeoBigusGeekus on 2008-03-26
Some say it isn't, I say it is... Depends on you actually - for me &#956;torrent has been more stable than deluge, azureus, ktorrent, etc.
About port forwarding: have you installed Firestarter?

---

### Post by Google Spider on 2008-03-26
> **TeoBigusGeekus said:**
> EDIT:
[http://ubuntuforums.org/showthread.php?t=700571]("http://ubuntuforums.org/showthread.php?t=700571")
This thread would be of interest to you.

awwe...I'm a bad member. I didn't use the search feature:(

---

### Post by Google Spider on 2008-03-26
Yes I have firestarter. [I also posted a thread about it here yerterday]("http://ubuntuforums.org/showthread.php?t=734742")

---

### Post by notwen on 2008-03-26
I personally use KTorrent, but have also had really good experiences w/ Deluge and Transmission.  It can't hurt to try each for yourself.  Search the forums for suggestions and see which clients you can find in the repos.  Best of luck.  =]

---

### Post by waspbr on 2008-03-26
Ktorrent had never let me down, it reminds me of the utorrent interface. 
there used to be a bug with deluge a while back that it wouldn't start the download and another bug in azureus that it would not start it all, I reckon they should be fixed by now, but because of them I started using Ktorrent and I am very pleased with it.

---

### Post by TeoBigusGeekus on 2008-03-26
> **notwen said:**
> It can't hurt to try each for yourself.  Search the forums for suggestions and see which clients you can find in the repos.  Best of luck.  =]
+1
Try everything you can find and decide for yourself.

---

### Post by hyper_ch on 2008-03-26
rTorrent -> fast, lightweight, powerful torrent client (however cli/ncurses based)

as reference for it I can say the guys at The Pirate Bay use it also ;)

---

### Post by Google Spider on 2008-03-26
Is Utorrent the **only** program which requires port forwarding ? I don't want to mess with another program which tells me to follow those port forwarding guides:mad:

---

### Post by TeoBigusGeekus on 2008-03-26
Sorry mate but I'm afraid you can't escape it....

---

### Post by hyper_ch on 2008-03-26
you could enable UPnP on your router - but that is not good practize... better to set port forwarding on your router...

---

### Post by TeoBigusGeekus on 2008-03-26
> **hyper_ch said:**
> rTorrent -> fast, lightweight, powerful torrent client (however cli/ncurses based)

as reference for it I can say the guys at The Pirate Bay use it also ;)

I have no doubt that rtorrent is tip top, but just by looking at its guides it gives me the creeps... Not sure if a newbie could get the hang of it.
I prefer nuclear physics...

---

### Post by Confuzius on 2008-03-26
Port forwarding is a good idea no matter what client you use, helps you get the best speed out of any of them.
I use deluge, I used to use KTorrent, but on gnome i'm trying to use as few KDE apps as possible, but I have found Deluge to be actually faster than Ktorrent. (Although this is entirely anecdotal)

---

### Post by michaelzap on 2008-03-26
I've come to prefer Transmission over all the other torrent clients (and I'm glad that it will be the new default app in Hardy). It's simple enough to stay out of my way, but works well and has all of the options I need when I need them. Like most torrent clients, it does automatic port forwarding if your router is set up to allow it.

---

### Post by Google Spider on 2008-03-26
> **michaelzap said:**
> . Like most torrent clients, it does automatic port forwarding if your router is set up to allow it.

That's a good news. But how do I do that ?

---

### Post by michaelzap on 2008-03-26
You just enable UPnP on your router and make sure that your firewall is not blocking the ports that you plan on using. UPnP is a protocol that the torrent client app will use to configure your router to allow its traffic on the ports it needs. This is not the most secure or efficient way to set up port forwarding, but it's definitely the easiest.

---

### Post by hyper_ch on 2008-03-26
> **TeoBigusGeekus said:**
> Not sure if a newbie could get the hang of it.
I prefer nuclear physics...
Sure you can... I did also ;) I thought kTorrent was great before I moved to rTorrent ;)

---

### Post by Google Spider on 2008-03-26
> **michaelzap said:**
> You just enable UPnP on your router and make sure that your firewall is not blocking the ports that you plan on using. UPnP is a protocol that the torrent client app will use to configure your router to allow its traffic on the ports it needs. This is not the most secure or efficient way to set up port forwarding, but it's definitely the easiest.
where do I find that option :confused:

---

### Post by hyper_ch on 2008-03-26
on your router's config somewhere

---

### Post by michaelzap on 2008-03-26
> **hyper_ch said:**
> on your router's config somewhere

That's pretty much the only reply that anyone can probably give you. You have a clunky router with a branded interface, so only someone with the exact same thing will know just where to find it. I googled the model number and upnp and it's definitely capable of doing it according to various posts out there, but I have no idea where you'll find the checkbox.

---

