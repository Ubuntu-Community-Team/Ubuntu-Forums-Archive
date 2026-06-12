---
title: "Quick Question about Flash"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Squeek on 2007-10-10
I have Ubuntu 7.04 64-bit.  I have Firefox 64-bit.  Is there a way to play streaming flash videos on my PC?

Also, no flash (.swf or .flv) videos will play on my PC.  I have tried Gnash, Movie Player, MPlayer, and VLC.

Any ideas?

---

### Post by AgentZ86 on 2007-10-10
I've read the 64bit flash stuff is still a bit behind, and could be buggy, I'm not sure if thats it, but I recall reading the forums about that subject, 

Search forum for 64 bit flash problems or something to that effect ?

---

### Post by Squeek on 2007-10-10
Ya I did, not much help beyond gnash and swfplayer.  I managed to get swfplayer installed, but I still have no idea how to use it (or get a FF plugin)...

Nice pic BTW...

---

### Post by Squeek on 2007-10-10
Crap I did something now no videos will play at all...

---

### Post by AgentZ86 on 2007-10-10
in the FF browser address bar check your plugins

type:
about:plugins

Then scroll thru to see if flash and java are installed

Thats the only thing I can think of, and with ubuntu I installed my plugins automatically just by visiting the site, and it asked me to install the stuff.

Post a site link so I can test what you mean by flash movies etc.

---

### Post by scruff on 2007-10-10
There are no official 64bit Flash builds. Last I knew, Macromedia (now adobe?) had no immediate plans to release any either. 

Are you sure you have a 64bit build of Firefox? I'm new to Ubuntu, but even in Gentoo where we compile our own applications, everyone sticks with 32bit firefox (using 32bit emulation libs) in order to use the true Flash plugin stuff. It seems unlikely that Ubuntu, easy distro that it is, would saddle you with a 64bit browser...

Anyone?

---

### Post by Squeek on 2007-10-20
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

And I mean no videos will play on my PC at all... :(

---

### Post by chalex on 2007-10-20
I just installed the amd64 version of Gutsy on a new machine and when I went to youtube it prompted me to install Flash, and clicked ok a couple of times and now everything works.

All it did is install the package called flashplugin-nonfree, I think.  Do you have that package installed? If yes, maybe you can try 'sudo dpkg-reconfigure flashplugin-nonfree'.

---

### Post by Billy_McBong on 2007-10-20
[COLOR="Blue"]flash works perfectly fine on 64-bit

```
sudo apt-get install flashplugin-nonfree
```
that will install flash

if you haven't already i think you have to have to enable universe and multiverse first though
go to system>administration>software sources[/COLOR]

---

