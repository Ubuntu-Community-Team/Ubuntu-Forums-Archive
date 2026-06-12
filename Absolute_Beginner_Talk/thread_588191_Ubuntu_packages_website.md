---
title: "Ubuntu packages website"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by mhdbnoimi on 2007-10-23
Hi   ;-)  ,

Is there any way to download a package with its full depends by single click?

For example:
I want to download Inkscape ([http://packages.ubuntu.com/feisty/graphics/inkscape](http://packages.ubuntu.com/feisty/graphics/inkscape)), so i need to download 39 depends, this is bad to me!

Note:
I've dial-up connection so I must go the internet cafe (they using Windows OS) to make all my downloads then install them offline to my ubuntu.

---

### Post by az on 2007-10-23
[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

---

### Post by forestpixie on 2007-10-23
I don't think that'll help - they're looking to download an app and all it's dependencies at the same time from somewhere else - without access to linux - aptoncd is ok if you've already got everything on your install.

At least that's how I read the post :)

---

### Post by justinmiller87 on 2007-10-23
I have pretty much the same issues you do, but if you download the DVD instead of the CD it has inkscape and all of its dependencies already on it.

---

### Post by az on 2007-10-23
You can run aptoncd from the live cd.

---

### Post by forestpixie on 2007-10-23
aah didn't know that - must be being thick though still can't see how it'd help the op - could you explain what you mean for next time :)

---

### Post by justinmiller87 on 2007-10-23
> **forestpixie said:**
> aah didn't know that - must be being thick though still can't see how it'd help the op - could you explain what you mean for next time :)
I'm guessing that (and I don't know, because I've not tried) if one were to take an Ubuntu live CD and boot into that on the public Internet Cafe computer, APTONCD could be run and then the data saved to a flash drive or some other form of media. I think that's what az is getting at. If one is on a public computer though, they would probably frown upon the usage of something like a Live CD, even if the thing leaves no data behind.

---

### Post by mhdbnoimi on 2007-10-23
[quote="az"]http://aptoncd.sourceforge.net[/quote]

i can't use APTonCD in the internet cafe cuz they've Windows OS only

I said before that i can't use the internet cuz I've dial-up connection

---

### Post by mhdbnoimi on 2007-10-23
[quote="justin"], but if you download the DVD instead of the CD it has inkscape and all of its dependencies already on it.[/quote]

where i can get link of DVD?, i tried to look for it but i get on links for CD only!

---

### Post by mhdbnoimi on 2007-10-23
[quote="justin"]If one is on a public computer though, they would probably frown upon the usage of something like a Live CD, even if the thing leaves no data behind.[/quote]
yep, that's right

using live CD isn't the the solution. i tried to download opensuse (8 CDs), it's working well and it's suitable to me, but i want ubuntu not opensuse, so i think if can get link of ubuntu DVD all the problems will be done.

---

### Post by justinmiller87 on 2007-10-23
> **mhdbnoimi said:**
> where i can get link of DVD?, i tried to look for it but i get on links for CD only!
I have two copies actually, one I bought, the other came in the Officail Ubuntu Book. It's version 7.04. 
But the ISO is there in the lists. You just have to find the huge one. :) I was actually considering OpenSuse myself, but I'm happy with Ubuntu. There's still a lot of stuff I couldn't install without manually downloading myself, so the DVD isn't an end-all solution to the download problems.

But here's the links to the downloads:
[Hardy](http://cdimages.ubuntu.com/releases/8.04/release/) (Just kidding!)
[Gutsy](http://cdimages.ubuntu.com/releases/7.10/release/)
[Feisty](http://cdimages.ubuntu.com/releases/7.04/release/)
[Edgy](http://cdimages.ubuntu.com/releases/6.10/release/)
[Dapper](http://cdimages.ubuntu.com/releases/6.06/release/)

---

### Post by mhdbnoimi on 2007-10-24
[quote="justin"]But here's the links to the downloads:[/quote]
i tried to download [Gutsy](http://cdimages.ubuntu.com/releases/7.10/release/) but download managers shaw me that the size of DVD is about 280MB although the list shows 4.2GB, so i stopped downloading process.

do you know any mirror for the DVD?

sorry for my stupid disscusion, but I'm still newbie on ubuntu world.

---

### Post by mhdbnoimi on 2007-10-24
finally i found DVDs [mirrors](https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive#head-ff608fd62775a095e4f87b6a9354ec944d238e27), thanks all :lolflag:.

---

### Post by forestpixie on 2007-10-24
I found this  just now perhaps that might help with you original problem - have no idea if it works now though. It's a script - nonetdebs

[http://ubuntuforums.org/showthread.php?p=3614383](http://ubuntuforums.org/showthread.php?p=3614383)

---

### Post by ruibernardo on 2007-10-27
> **forestpixie said:**
> I found this  just now perhaps that might help with you original problem - have no idea if it works now though. It's a script - nonetdebs

[http://ubuntuforums.org/showthread.php?p=3614383](http://ubuntuforums.org/showthread.php?p=3614383)

I've made that script (nonetdebs), but it needs a liveCD and a media (USB memory) to work, so it is not usable from school or library or from workplace if you can't boot from a CD.

I am now adapting that script to work from a website, so that people just have to upload a file (/var/lib/dpkg/status) from the ubuntu without internet and get the list of all the packages upgrades to update their ubuntu without network or to install a new package(s) they want.

Virtually, this website could give people the chance to update and/or install new packages on their Ubuntu without internet from any browser and from any operating system, just by downloading the packages from the list on the webpage to a media and installing them on the target (the internetless Ubuntu).

l'll edit this post as soon as I've got it working (I hope it will be very soon, working on it now :)).

EDIT: [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net)

---

### Post by Irihapeti on 2007-10-27
It's possible to use synaptic to select the program you want to install, and all its dependencies, and then to generate a download script. The option to do this is in the File menu. At least, it is in Feisty - can't be sure about other versions.

The script is a series of wget commands, and it's quite easy to edit it so that it's a set of urls instead. These can then be given to any download manager you like.

I'm on a dialup myself, and I often prefer to do my downloads at night (and get the machine to hangup when I've finished), so another way of downloading the files is useful.

I'd be interested in epimeteo's script, too.

HTH

Irihapeti

---

### Post by AnRa on 2007-10-28
You may try [Wubdepends](http://wubdepends.sourceforge.net/).

---

### Post by shankhs on 2007-10-28
Hey wat is **"wubdepends"**?
is it for win stuffs made to use in ubuntu? or ????????/:confused:

---

### Post by shankhs on 2007-10-28
ooops!!!!**sorrrry**
Wubdepends can prove really useful tool to download dependencies.

---

### Post by zvacet on 2007-10-28
Just go to this link

[http://www.ubuntu-hr.org/proba.php]("http://www.ubuntu-hr.org/proba.php")

you will get URL of packages you need,and only that ones you don´t have on CD.This way you don´t have to worry about dependencies.Give it the try and tell me if it work for you.

---

### Post by mhdbnoimi on 2007-10-29
This is what i need, thanks :)

but it's freezing, it didn't work on Windows !

i tried to use the default input values but it didn't work!!!, any suggestion?

---

### Post by mhdbnoimi on 2007-10-29
> I am now adapting that script to work from a website

cool dude :guitar:, this is good idea I'm waiting for u.

note:
if u've personal website u can host your code in it, so any body can use it for downloading need packages

---

### Post by ruibernardo on 2007-10-29
> **mhdbnoimi said:**
> cool dude :guitar:, this is good idea I'm waiting for u.

note:
if u've personal website u can host your code in it, so any body can use it for downloading need packages

I'm glad this as some interest. And this thread gave me the idea for this (thank you).

The code of the script is available in [http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs](http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs) for some weeks now, and as I've said, you can even run it from a LiveCD, with a USB memory and the status file from the target. More info about it at [this thread]("http://ubuntuforums.org/showthread.php?t=572819").

The website is for those who can't boot a LiveCD on the connected computer (cybercafes, libraries, workplace, etc). 

From my testing, it is working fine here, but I still have to prepare some things here (some limits), as this will be running on my computer, with my internet connection, and the debootstrap/chroot/apt-get requests and operations are very heavy and loads my computer.

I hope to get it up and online (for more tests, to be sure it really works for all) very soon, in one day or two.

---

### Post by zvacet on 2007-10-30
It is very odd that link doesn´t work.it is for people with slow or no internet connection at home,so they can download from other comps.Anyway you can try this one

[http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet]("http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet")

---

### Post by ruibernardo on 2007-10-30
Ok, the site is up. It is still very fresh and it might broke, but if anybody want to test it: [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net).

When you register, all the fields are about the target (the Ubuntu without Internet):

- select the repositories you want;
- the ubuntu release;
- check if you want to do an upgrade;
- type any the new packages you want to install;
- select the locale;
- upload the status file;
- click "List Packages" and wait for about 1 minute.

---

### Post by ruibernardo on 2007-11-10
Detailed instructions how to use [http://nonedebs.homeip.net]("http://nonedebs.homeip.net/") can be found [here]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11").

---

