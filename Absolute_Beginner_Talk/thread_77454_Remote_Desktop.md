---
title: "Remote Desktop?"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by ComradeF on 2005-10-16
Hi there! I'm completely new to Linux, so be patient with me. :p  I just put together a new computer for Windows, and have declared my old machine (1.4 GHz AMD Athlon) to be a Linux playground. And for my introduction into the world of Linux, I have chosen Ubuntu.

Now, I got it installed just fine. But I want to set it up such that I can proxy in through my Windows XP machine and work as if... well, there were no Windows machine. I can't use a hardware switch for this (nor do I want to) because I want to use the same keyboard, mouse, and monitor... So what I'm left wanting is a solution similar to Remote Administrator or UltraVNC.

Thing is, as you know, I'm a Windows dude. I don't know what to get nor how to set it up. I checked the Wiki here but it just didn't clear things up for me. This will have to be set up such that I can turn on my Ubuntu machine and use an app on my Windows machine to do everything, including get in through the login screen. That would mean this service would have to be running ALWAYS, even without my being logged in. Because once I drag it into my room and plug it into the router, the only way I'd be able to access it would be through the proxy software.

I guess that's a long way of asking, can anyone tell me how to set up a remote desktop service in Ubuntu so that I can get into it through a Windows machine? Thanks in advance!

---

### Post by ltmon on 2005-10-16
The easiest remote desktop is none at all... use "ssh" to deliver command line commands.  It's quick, easy and uses almost no bandwidth at all.

For a full desktop remotely the best solution (IMHO) is FreeNX: [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

L.

---

### Post by ComradeF on 2005-10-17
OK, sounds good... How do I do that? It says "add these" and "update your sources"... I am a -total- n00b and I don't know how I'd update my sources or anything.

---

### Post by Swab on 2005-10-17
[QUOTE=ComradeF]OK, sounds good... How do I do that? It says "add these" and "update your sources"... I am a -total- n00b and I don't know how I'd update my sources or anything.[/QUOTE]

Have a read of this: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by ComradeF on 2005-10-17
Alrighty, got all these bookmarked and will make a day of it sometime. Thanks very much!

---

### Post by ComradeF on 2005-10-20
Alright, I've been playing around with all this but it just isn't coming together.

The site in the Free NX guide is down or dead, so I couldn't install it the easy way. I've tried to get the tarball from SourceForge, but I don't know what to do with all this source code. When I said I'm a newbie, I meant *I am a NEWBIE*. I have no idea what to do, and these guides aren't helping.

What I'd like to know is how to get Free NX running on the machine. I downloaded the 0.4.2 tarball and have it extracted to the desktop... and I read the install notes, but that's really as far as I can take it. Right now I'm using the built-in Remote Desktop function, which is kinda laggy, and I can't use it to log in to the computer from a cold boot. Bah.

Help? =\

---

### Post by bugmenot on 2005-10-20
Go with the method proposed in the wiki. It's as easy as it gets.
Building from source in this case will be much more complicated because NX uses many components.
In the best case you get the packages from seveas' repository with synaptic/apt-get and are setup completely afterwards.

---

### Post by clueo8 on 2005-10-20
I'm in the same boat.  I've tried using the method on the wiki and some others posted in the forum.  My problem is, when I run:

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx

It says I dont have deb... I'm running kubuntu 5.10 with the latest kde breezy... Do I have to do anything different?

---

### Post by ComradeF on 2005-10-20
I was unable to connect to seveas, or something...

---

### Post by ComradeF on 2005-10-20
OK, got it working! The server was down, so that was hindering me...

---

### Post by GreyFox503 on 2005-10-21
[quote=clueo8]I'm in the same boat.  I've tried using the method on the wiki and some others posted in the forum.  My problem is, when I run:

```
 deb [http://seveas.ubuntulinux.nl/]("http://seveas.ubuntulinux.nl/") breezy-seveas freenx
``` 
It says I dont have deb... I'm running kubuntu 5.10 with the latest kde breezy... Do I have to do anything different?[/quote] 
I've never tried to do remote desktop with Ubuntu, but I can help you follow the instructions in the wiki.

When it says to add a line to your sources list (for apt-get) do this in a terminal:

```
sudo gedit /etc/apt/sources.list
``` 
This will bring up a text editor that contains a list of repositories (servers that apt uses to download packages)

Then scroll to the end and add whatever new sources you want on a new line (in this case, copy & paste this to the end of the file)

deb [http://seveas.ubuntulinux.nl/]("http://seveas.ubuntulinux.nl/") breezy-seveas freenx

[FONT=Verdana] Then, when it says "update your sources", run this command:

[/FONT]```
sudo apt-get update
``` 
and to install the program (freenx):

```
sudo apt-get install freenx
``` 
One last thing:  when you are all done installing this program, I would recommend going back into your sources.list file and removing the new repository you added.

---

### Post by ComradeF on 2005-10-21
Thanks! Yeah, that's exactly what I did. And I commented out the freenx line in my sources.list file, just in case I wanna go back over it or something.

The real problem was that their server was down, so I couldn't follow the Wiki properly! What an introduction to Linux huh?? Hehehe. It's working perfectly now, though. Blazing fast!!

---

### Post by GreyFox503 on 2005-10-21
Nice avatar :)

Funny, something similar happened to me.  One of my friends decided to try Ubuntu, and the day after he installed it, both the forums *and* ubuntuguide.org were down.  Some luck he has.

There's the occasional hiccup, but for the most part Ubuntu's online resources (forums, repo's, ubuntuguide) are pretty reliable.

---

### Post by bugmenot on 2005-10-22
You have to be aware that there's a difference between the official software repositories and the random rogue repo that someone is giving you the sources.list lines for.

It very much like the stack of floppies from the old days. You don't really know what's on them and they could be unreliable.

For the people that put up repos. They could be running on their main machine that get's switched off over night (linux makes running server easy, right?) or that simply doesn't have a UPS, or thats experimented on at the same time. They like experimenting after all.

The official repositories have a good uptime.

---

