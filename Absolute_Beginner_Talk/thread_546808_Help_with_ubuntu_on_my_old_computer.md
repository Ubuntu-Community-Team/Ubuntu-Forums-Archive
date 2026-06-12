---
title: "Help with ubuntu on my old computer"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by TobiasDK on 2007-09-09
Hi,
I recently tried to install Ubuntu on some old PC I had, to see how it is to use it at home. I did that because the computers where I study are with linux. The computer is a pentium 3 800 mhz with 128 mb ram.

I burned the alternate install cd image from the ubuntu website and i verified it with the sum thing. Next, I put I put it in my CD drive and rebooted. This is then where the problems start. 

I started verifying the CD, and loads of weird stuff pop up on the screen, and it seemed like nothing happened, I went afk and when I came back, it apparently had verified the CD. That was great I thought and I could begin the installation. I started the installation and these weird lines popped up on the screen again (I can't remember what they said, but I willl come back to that).

At some point I thought the computer were frozen (nothing happened) and I turned it off the harsh way (maybe that was stupid, I don't know).. I tried to install again and I got these messages again, but eventually it might have installed since I was able to actually get into ubuntu.

But, and this is where my real question is, I get the same kind of messages (really many of them) when I turn on the computer. The messages are something like:
[B]
exception eMask 0x0 Sact
Buffer IO error on device data[/B]
And these go on like forever.

I can write the exact readings if you want to, but I finally got into ubuntu so I didn't want to reboot again to see them right away. 
I will of course do it if you can't help me with the info you have received so far.

And about the "errors" I got when I was installing / verifying the CD, I am not sure, but they might have been the same as those i pasted above.

Moreover, the system overall behaves very slowly and I dont know if this can be solved in some way. Maybe my old PC is simply just too old to be working properly, or maybe the installation is just ****** up in some way.

I hope someone can help me, and please ask me if some of the stuff I wrote ain't clear enough :)

Thanks in advance.

---

### Post by southernman on 2007-09-09
Your cpu spec is fine, but that little ram is a problem regardless of live or alternate cd usage.

A couple of options exist though:

Add more ram to that system (256mb is the bare minimum for Ubuntu) 
Download, burn and install xbuntu
Opt to do a minimal installation for low memory system [http://https://help.ubuntu.com/community/Installation/LowMemorySystems?highlight=%28CategoryDocumentation%29]("http://https://help.ubuntu.com/community/Installation/LowMemorySystems?highlight=%28CategoryDocumentation%29")
and be blown away at what that old computer is still capable of doing.

YMMV (your mileage may vary)

---

### Post by Amazona aestiva on 2007-09-09
Without more memory, You should use [Xubuntu]("www.xubuntu.com").

---

### Post by TobiasDK on 2007-09-09
Hi and thanks for the answers. I just found some extra ram from another old Pc, and inserted them, i now have 384 ram, but the booting is still as it was before...

You think I should still go try Xubuntu instead, or should I reinstall Ubuntu with the alternative cd, or the primary one?

At this moment my PC is showing some ubuntu startup loading screen at the beginning, and then  after some time it starts giving me these weird messages again..

Another thing I find quite weird is that I am currently having two harddisks. One of them is not working 100% properly i think (can't remember what's wrong. I can't remember which of the two is the nonworking one. The problem is that it's the smallest one  (30gb) that ubuntu apparently found when installing (didn't find the other one), and I would assume that the newest harddisk (the one working properly, maxtor 60 gb i think) is the largest one.

---

### Post by southernman on 2007-09-09
eh, well The first time I read your OP, I must have missed the fact you finally got it to install.

However, in light of your being unsure about the health of the hdd that ubuntu found could be the culprit here. Maybe not the hard drive itself but the cable attached to it. It's kind of hard to pinpoint with the uncertain errors you reported, or not being able to sit at your desk and have a first hand look-see for myself.

Try swapping out the IDE cable first. Leave the larger drive off for now. If it won't boot then, or gives the same error message you'll know of two things with absolute certainty... ;) 

1- You used another cable that's bad.
2- Your hdd has bad sectors on it or something of the sort. This could possibly be fixed running fsck, but you can't run it on a mounted drive and that's all I can tell you on that program. You'd have to Google, search the forum, or wait for someone else who knows how to use it.

If it doesn't boot at all, swap the small drive for the larger drive and rinse/repeat.

If both drives were hooked up to a properly working cable, and Ubuntu didn't find one of them... that is a good indicator it's the bad one. Maybe the jumper settings are wrong though.

Anyhow, try the above and get back to us.

ps. 384 should run Ubuntu fairly well.

---

### Post by TobiasDK on 2007-09-09
A thing I forgot to mention is that right when I turn on my computer, where the computer counts ram etc, I see that it says:
primary master: the maxtor hd (the big one)
secondary master: the IBM hd (the small one)

So it must somehow find both hd's?

Though I just tried to take the ide cable from the big one into the small one and i received this message:

Starting up...

crc error

 -- System halted

But it still finds the IBM hd at the place I mentioned before now telling me:
primary master: ibm hd
secondary master: none


And btw, I just looked at the harddisks and I see that on the IBM hd it says Sep 2000, and the other one july 2003 so logically it would be the ibm hd that something is wrong with..

edit: Don't you think I should try remove the IBM hd, and try install ubuntu on the maxtor one? If it can find it that is :)

---

### Post by southernman on 2007-09-09
Sure... might as well.

[CRC error]("http://www.computerhope.com/issues/ch000430.htm") doesn't mean that the dirve itself is bad per say, but more the file(s) are bad/corrupt.

---

### Post by TobiasDK on 2007-09-09
Hm I get a bunch load of weird errors :/ like 

<0>Kernel panic - not syncing: Attempted to kill init!

I think ill try this with another, a bit older, PC I have and see if its better in any way before I do more with this one :(

---

