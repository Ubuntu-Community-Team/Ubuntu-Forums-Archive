---
title: "A mistake?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by LostJot on 2006-10-04
How do I know if I made a mistake in installing Ubuntu? Or even in trying Linux in the first place?

Will my problems ease over time, or am I in a situation where I'll always feel this way?

I have not given it much time, possibly I do need to give it more time. At times I have enjoyed the challenge. I have managed to solve problems and learned as I did them. But it gets tiresome after a while. Something that should be relatively simple (installing a video card driver and telling the system to use it) is very unforgiving, tedious and annoying. You test something out, go wrong, and you end up with an unbootable system and have to go into recovery mode. That's annoying, but not too bad, as you can work your way through the command line and learn as you do. 

But then, another mistake and you end up with a system unbootable from either recovery mode or standard start-up. How can you even play around to try and see what's going on? You can't. You're stuck. ](*,) You can't poke your way through and try to learn as you go. You're just completely dependent on someone bailing you out. That isn't always feasible. 

This brings me onto the issue that makes me think that for ME, Linux might never be worth going for. I recognise that these days I am in the minority, as my machine does not have an internet connection. I honestly never thought this would be a problem. I should have looked into it more first. I have to say that over the past few years I got increasingly annoyed with Windows just assuming that you're connected to the internet, trying to do all these updates and automatic codec grabbing etc etc. But if you're NOT connected, it just takes the easy way out and shuts up. I should have realised that it was just responding to the times- almost every computer is now connected. 

But I assumed that on Linux it would be different, but I find that on Ubuntu at least, it is not. In fact it's easily worse. There is a great song and dance about how easy apt-get blah is, and almost every single piece of advice/help/how-to is full of lines of sudo apt get blah and "add this repository". But if you try to do it manually you end up in a difficult situation. The packages on Ubuntu.com are fine, because they are all available for manual download. Handling dependencies manually is just irritating though. I ended up spending days just downloading the entire Ubuntu repositories and burning them to DVD so that I wouldn't end up stuck needing lib-file-obscurethingy and not having it. This is just a bit inconvenient. The add on CD is very handy, but of course limited by size.
Manually installing from other sites is a different matter though, and it seems that often it is impossible, as most of the time I can't find the files there.

As far as I can tell, all the distros are like this, including SUSE, which seems to be quite popular. 
With Windows, the situation is different. I can just grab a collection of .exes and stick them on a disk and everything will work fine. 

For a free piece of software, I can't fail but be impressed so far, although I don't see any specific feature or application that is urging me to jump ship from Windows. 

I just feel that in my situation, without the computer connected to the internet, Linux may never be practical, and I should just give up until my situation changes. 

:-k

---

### Post by jordanmthomas on 2006-10-04
Unix variants *want* to be on a network because they were designed as multiuser systems.  I understand not liking constant updates, but it's your choice:  either update or don't.  

The reason you can just grab an exe on Windows is because every application includes whatever libraries it needs (generally speaking) so you end up with multiple copies of the same thing.  

You should never give up though.  It's fine to decide that Ubuntu isn't for you, but give a good reason (aka can't download software) instead of citing your reason as giving up.

Also, search around...I think there is a DVD for Ubuntu that has everything in multiverse and universe and thusly would have all the dependencies you need.

---

### Post by WalmartSniperLX on 2006-10-04
Think of it this way. Gamers have to put up with the same issue for gaming on windows xp (for serial checks, updates, etc). Also win xp is also dependent on the internet. It doesnt have repositories, so its actually a lot more difficult, as you must find what you need on the www. 

Win vista is going to be even more network heavy since (if you get a retail copy) you will NEED to connect to the internet to get updates AND CHECK your serial. Its really just how you look at it. Either way, the world of computers today is highly based on the internet. :-D

---

### Post by podunk on 2006-10-04
I backed up my Ubuntu system the other night using this command:
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /

I unmounted my Windows drives first, cleaned up my home folder a  bit before I started.

It went very quickly – it was done by the time I came back to the computer after supper. Just for the halibut, I restored last night to see what happened. I went through and deleted quite a few files here and there and opened the tarball and that was that. :-)

I feel quite a bit more adventuresome now.

I can't think of a suggestion to overcome your lack of Internet access really – with Windows of course you have the experience built up to know what to down load and where to find it, so it's not a big deal. 

For me - experience almost always comes from mistakes. :-)

I was reaching the terminal frustration point a few weeks ago and I decided to slow down. I changed my goal from having the latest and greatest geewizbang to having a stable machine I could use and enjoy. As my experience and knowledge grows I'll branch out.

I decided to look at Linux like this – I spent 25 years on the computer mountain top – but I paid a lot of people to get me there, I took a helicopter rather than climbed. 

With Linux I'm actually climbing the mountain rather than watching the scenery. :-)

---

