---
title: "Multiple users"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by ainsworth on 2007-04-07
Hi,

I realise this has probably been asked a few times but I'm having trouble finding any documentation on this or examples of where people have done this successfully already. Basically my girlfriend and I have one pc that we're often both wanting to use, the pc has two graphics cards and I have spare monitors, keyboards and mice kicking around. So is it possible to have us both using the pc at the same time? I've heard anecdotally that it's been done but can't find any specifics. Thanks

Ainsworth

---

### Post by irwa82 on 2007-04-07
Hi,

Linux can certainly have multiple users running on the same machine. I am not aware of away to connect multiple monitors and mouse keyboard etc to the same machine but it can probably be done.

I would pick a a really cheap computer box, something really crappy that won't run much by it's self you may even be able to get something for free that someone was going to throw away and then set up you main machine as a terminal server. That way you can use the old crappy box as a dumb terminal and it will work quite well the crappy machine does not even need to have a hdd, just some ram and a graphics card.

I have set up terminal servers in the past with tltsp and you can't tell the differents on the dumb terminal it really does work really well.

---

### Post by mac.ryan on 2007-04-07
> **irwa82 said:**
> I would pick a a really cheap computer box, something really crappy that won't run much by it's self you may even be able to get something for free that someone was going to throw away and then set up you main machine as a terminal server.

Hello, what irwa described goes under the name of [thin client]("http://en.wikipedia.org/wiki/Thin_clients"). Nowadays there is a renewed interest in this type of architectures. If I am not mistaken, edubuntu comes with an installer for this kind of architecture already.

I also anecdotally heard about two monitors and keyboards connected to the same computer but - like you - I could not find (yet!) any documentation on this. Knowing a bit how linux works - though - it sounds very much possible... If you find any interesting link, please post them! :)

---

### Post by mac.ryan on 2007-04-07
Gotcha!!! :)

Still not an how-to under ubuntu, but at least a keyword to look up on google! What the system is called is *multiterminal* or *multiseat*. Both the terms on wikipedia point here:

[http://en.wikipedia.org/wiki/Multiterminal](http://en.wikipedia.org/wiki/Multiterminal)

[COLOR=Red]**EDIT:**[/COLOR] ...and somebody already did it with ubuntu: [http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

---

### Post by lej on 2007-04-25
hi ainsworth,

i've had such a setup (2 monitors, 2kbds, 2 mice, 2 graphic cards, and hence 2 logins, on 1 pc) working quite well on 6.06 for awhile.  I got it setup using this tutorial in the community docs:

[https://help.ubuntu.com/community/MultiseatX?highlight=%28multiseat%29](https://help.ubuntu.com/community/MultiseatX?highlight=%28multiseat%29)

I pretty much followed the instructions verbatim without any problems, but be prepared for a broken xorg.conf file just in case!

Unfortunately, i have just upgraded to ubuntu 7.04 and copied over my custom xorg.conf file only to find that my mouse buttons are now mismapped...  probably requires only a line or two in the xorg.conf but i haven't figured what it is yet!

---

### Post by lej on 2007-04-26
After making a few changes on the xorg.conf without success on 7.04, i found that i could get multiseat with properly mapped mouse buttons by not logging into the primary account but rather into 2 new accounts... anybody know what's going on here?

---

