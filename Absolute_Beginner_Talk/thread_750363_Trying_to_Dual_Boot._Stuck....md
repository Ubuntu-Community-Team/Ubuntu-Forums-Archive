---
title: "Trying to Dual Boot. Stuck..."
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by BigFatso on 2008-04-09
Hi folks. I'm trying to dual boot Ubuntu 7.10 x64 alongside my current Windows XP install. So, I downloaded the image from ubuntu.com, burned it, popped it in and booted from it. It comes up to the screen where I can select to start and install ubuntu. I select that, and my screen goes off. After a few minutes, a small window pops up for graphic configuration. Everything in there seems ok, so I hit Continue. At this point, it brings me to what looks like a terminal with about 4 lines of text at the top. They say something along the lines of:

Something Something [OK]
Something Something [OK]
Checking Battery power [OK]
Loading Settings [OK] 

(or something similar to that...)  At this point I have a flashing cursor below those lines, and my hard disks aren't spinning, nor is my cd drive. It just sits there. What do I do?

---

### Post by jocheem67 on 2008-04-09
Well, it's a not so clear problem I'm afraid.

Two suggestions:

you can pass some more detailed options, at the screen where you start the live-desktop. I don't have to use them myself, but I do know that noacpi is one of them. Just take a look at them and try them out.

You're using the ubuntu 64 cd, maybe it's smart to go for 32....64bit is not that mature yet and it won't give you big perfomance drops using 32bit.

---

### Post by phidia on 2008-04-09
Presuming you checked the iso image you burned (md5sum) you could select the other boot options, 2) try the alternate cd 3) provide your system specs & 4) check out further install methods [here]("https://help.ubuntu.com/community/Installation").
The community docs at the above link have a lot of info-hope that this is useful to you.

Edit: As long as you have the correct processor for 64 bit the 64bit version works very well-I'm using it from a laptop and everything works.

---

### Post by ferdostar on 2008-04-09
Check you CD for errors. In fact when you're burning the CD, you should burn it at minimal speed (2-4). Then you can try the safe mode to see if there are any changes. Or just wait until ubuntu loads.

---

### Post by StRiFe10101 on 2008-04-09
I'm no expert but another thing to look at would be the hardware you are using.  I'm currently running a m2n-e motherboard and when I did a fresh install from dapper to gutsy 7.10 I had similar problems.  I ended up searching for specifics of my motherboard with the corresponding version of linux that you are trying to install. 

I ended up having to turn something off in the bios of it to work for me.  I can't remember what it was but regardless, things are working like a dream for me.

---

### Post by BigFatso on 2008-04-10
I've checked the burned cd, and its fine. I took the advice from earlier in this thread and burned off a 7.10 32 bit version, at 4x. It loads a little bit differently, but the first menu is the same. I can choose to "Start and Install Ubuntu", which to my knowledge is the way to do a dual boot on top of a current windows xp install. Ultimately, I get stuck at the same place. Here is the exact text I get:

*Starting deferred execution scheduler atd     [OK]
*Starting periodic command scheduler crond    [OK]
*Checking battery state...                                [OK]
*Running local boot scripts (/etc/rc.local)         [OK]
_


The underscore being the blinking cursor. This is where my screen stays. CD drive not spinning, HD's not spinning. My current setup is an Asus A8N-E motherboard, an Athlon 64 3700+, 2 x1024mb OCZ PC3200
sticks, GeForce 8800GT, 74gb SATA WD Raptor HD, and 3 other storage hd's (for programs and games). The Raptor is the HD that I will be installing Ubuntu on, which is also the HD I have my XP install on. 
I did notice that if I tried CTRL + ALT + DEL at this point, a lot of text blasted onto my screen, something about Gnome and GUI shutting down, then my monitor goes black, and stays black until I reset.

Does any of this extra information help?

---

### Post by Weidbrewer on 2008-04-10
I had the same problem with one of my boxes.   As someone mentioned above, try the alternate install CD.  This one goes totally by text, with no GUI.  It's no more difficult to set up, so there's no reason not to try it.

---

### Post by BigFatso on 2008-04-10
Is there a link to the alternate 7.10 CD on ubuntu.com ? I didn't see anything.

---

### Post by Weidbrewer on 2008-04-10
> **BigFatso said:**
> Is there a link to the alternate 7.10 CD on ubuntu.com ? I didn't see anything.

On this page:  [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

If you look right below the "Start Download" arrow, there is a check-box for the alternate CD.

---

### Post by barney385 on 2008-04-10
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by R6V2 on 2008-04-10
Hmm, I think is what happening is that Linux Ubuntu's kernal is not loading. But when you shutdown/restart it unloads the kernal, which is saying that it was loaded. My conclusion is that, try a different brand of CD's, try re-downloading the .iso, reburning it, and then booting again. If that doesn't work, then get the text based installer.

---

### Post by clarknova on 2008-04-10
And then there's wubi. Burn the 8.04 beta to cd or dvd, boot into windows, then run wubi. It installs ubuntu on a virtual disk inside your windows file system. It's not as independent as having ubuntu on it's own partition, but as long as you're looking for alternate installers...

Come to think of it, if you're not having luck with the 7.10 installer, but you already have a partition for ubuntu, you might just try installing the 8.04 beta. I've been really happy with it. In fact, I had more problems with 7.04 and 7.10 *after* they were released than I have had with the 8.04 beta.

db

---

### Post by R6V2 on 2008-04-10
OffTopic(Is the Ubuntu 8.04 better in your opinion?) I want to try it, but im not sure exactly how to remove 7.10, and leave my partitions (50Gb Windows: 50Gb Linux 1TB storage). I might actually make the switch! :)

---

### Post by BigFatso on 2008-04-10
I don't currently have a partition for ubuntu. Was gonna set that up on install. I did see 8.04 but didn't really wanna try a beta. I'm a gamer. So... I want my games to run in Linux as well as XP. I guess I want to know for sure that 8.04 seems better than 7.10  to more than 1 person. I'll look into it this evening.

---

