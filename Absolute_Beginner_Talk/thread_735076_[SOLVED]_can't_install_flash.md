---
title: "[SOLVED] can't install flash"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by faim2600 on 2008-03-24
I have a 2 part question.

Part 1: I've been looking online for how to troubleshoot, but I'm not sure if I should edit files when the advice is for another version of Ubuntu.  

Part 2: I am trying to install Flash on the newest version of Ubuntu I believe and I get the message 

"Could not download all repository indexes
...
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/source/Sources.gz:](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found
"

How can I fix this?  The flash I am trying to install is the .tar.gz file which is the first one on the list of Flash packages on the Adobe website.

By the way, I apologize if this was addressed in another post.

---

### Post by Sam Lars on 2008-03-24
That repository seems to be down for now... you can check again later.

---

### Post by faim2600 on 2008-03-24
Should I try to install a different version of flash?
Also I just realized this may be for Kopete, not flash, but I'm getting a similar message about missing repository indexes.  I'm not sure if it say 404 not found, but do you have any idea why this is happening?  As in, what determines when this will be fixed?

---

### Post by Hospadar on 2008-03-24
as for part one, older guides are probably fine, just be sure to make backups of important system files before you edit them.

The only thing you should watch for is when editing /etc/apt/sources.list, there are different repos for different distros, so if you guide has instructions that say "edgy" or some other distro, just be sure to change them to your distro, or leave them as they are.

---

### Post by faim2600 on 2008-03-24
ok sounds good! thanks!

---

### Post by faim2600 on 2008-03-25
I made a post yesterday and I have read similar threads, but I am a total noob and utterly confused.

I've read a few times that I need to create a new directory called plugins under mozilla.  How do I do this?

Can someone give me a thorough explanation of how to install flash on Gutsy?  It seems each article I read gives different information and as a noob, I'm having a hard time figuring out what's best.
I just really want to watch movies and listen to music online.

Thanks!

---

### Post by kellemes on 2008-03-25
```
sudo apt-get install flashplugin-nonfree
``` 

If this gives you some message about package not found you need to enable the multiverse repository in your package manager (Synaptic -> Settings -> Repositories)

---

### Post by oedha on 2008-03-25
AFAIK...you just open terminal then type :==> sudo apt-get install ubuntu-restricted-extras
or from system - administration-synaptic
search for flash...nonfree.....CMIIW :)

---

### Post by bumanie on 2008-03-25
Follow the post here
[http://ubuntuforums.org/showthread.php?p=4073291](http://ubuntuforums.org/showthread.php?p=4073291)
Alternatively install the open source version of flash
> sudo apt-get install mozilla-plugin-gnash
Gnash works OK for me.

---

### Post by ellalan on 2008-03-25
This link was very helpful to when I had similar problem.
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)
HTH.

---

### Post by gandaran on 2008-03-25
as you can see here, there are many ways to install flash, another way, just go to a web page that uses flash, when you get the flashplugin missing message just click to install on that message, but choose the flashplugin-nonfree, don't choose gnash, gnash doesn't work properly on youtube site.

---

### Post by aysiu on 2008-03-25
> **ellalan said:**
> This link was very helpful to when I had similar problem.
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)
HTH.
I now also recommend this link, at least until Ubuntu 8.04 is released.

I used to recommend installing *flashplugin-nonfree* or *ubuntu-restricted-extras* (which really just points to *flashplugin-nonfree*, among other proprietary software packages), but I've still seen people having problems with the MD5 error that popped up a few months ago.

Although some other methods *may* work, the manual installation, at least until the next version of Ubuntu is released, is the most reliable method to go with for now.

---

### Post by faim2600 on 2008-03-25
bumanie's link worked!  Thanks so much to everyone for the help!

---

