---
title: "Not trying to start a flame war....."
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by ChinaCatJones on 2005-06-18
I am a newbie to Linux, but not to PCs.  I won't bore you with the leeters after my name in a business card.

I have an observation about Ubuntu.  It just works.  Amen.

I also have another observation.  While on on Freenode, #ubuntu seems to be the hot place.  #ubuntuforums seems pretty stagnate.  I would offer that #ubuntuforums  be used by us, meaning ubuntu users, more frequently in the spirit of this foum.  I am assuming the two are related, if not excuse my stupidity.

In regard to my first comment, since ubuntu seems to just work, and I wouldn't mind owning some linux knoweledge I made the jump to Gentoo.  My initial guess about it in my limited knowledge, is that it is high-octane.  However, the support and users seem to be a little bit "snobbish", let the flames begin, not!!!

It seems that most debates about the OS wars seem to stem from technical stuff.  I would put it to you that the Ubuntu culture is really what will win the war.  How many Windows users do you knowthat are evangelists?  How many Mac users?

To quote Jerry Garcia, "Not everyone likes licorice, but those people who like licorice,  really like licorice."

Chris

---

### Post by diebels on 2005-06-18
Ubuntu just works when your pc components has good linux drivers.

Gentoo has good init scripts, nice security hardening tools thats very easy to install. Is good for learning a few things about linux(Linux from scratch is better). But it is NOT faster than ubuntu(other than the init scripts). Install linux-i686/k7 and libc6-i686 on ubuntu and it's as fast as gentoo. Most gcc optimization flags users put in gentoo gets filtered out by the ebuild makers. The etc-update prosedure is a pain, but you get to see a lot of config files and could learn something. The compiling everything gets boring.

So you can have fun messing around with gentoo, but it rarely beats ubuntu for real world tasks.

I've used gentoo a couple of years before ubuntu, and I like the forums. Mostly nice people there and loads of detailed linux info.

Ubuntu is a nice packaging. But the just works **for everyone** relies on heavy improvements in the linux kernel drivers, xserver and the project utopia stuff. Both kernel and xserver are progressing quickly. So the future looks bright.

Hoary with backports is more stable(except debian), more up to date and has more packages than any other linux distro.
```
root@laptop:~# grep Package: /var/lib/apt/lists/*source* | wc -l
9668
```
Add 41 in hoary-extras backport repository to that, and you have quite a few uniqe packages to pick from. From what I've read on the wiki, breezy is planned to have lots more.

Ubuntu is much better than licorice :mrgreen:

---

### Post by Mr. Electric Wizard on 2005-06-19
First off, I'm pretty new to linux and have tried out many distros...
When it comes to "just working", Ubuntu pretty much has everybody beat, then there's wireless network access ](*,) 
(Slight joke there, I know that this isn't just a Ubuntu problem :) )

I know it's a heck of a lot better than Fedora!
The synaptic package manager rocks too!

---

### Post by christooss on 2005-06-19
[QUOTE=diebels]

```
root@laptop:~# grep Package: /var/lib/apt/lists/*source* | wc -l
9668
```
Add 41 in hoary-extras backport repository to that, and you have quite a few uniqe packages to pick from. From what I've read on the wiki, breezy is planned to have lots more.
[/QUOTE]

WHat does this comand do?

---

### Post by Kyral on 2005-06-19
It seems to count the lines (packages) in the package list

---

### Post by diebels on 2005-06-20
[QUOTE=christooss][QUOTE=diebels]root@laptop:~# grep Package: /var/lib/apt/lists/*source* | wc -l 9668

Add 41 in hoary-extras backport repository to that, and you have quite a few uniqe packages to pick from. From what I've read on the wiki, breezy is planned to have lots more.
[/QUOTE]WHat does this comand do?[/QUOTE]
It counts the number of source packages. The number of packages(around 15000) minus the metapackages like ubuntu-desktop. So you get a more correct package count.

---

