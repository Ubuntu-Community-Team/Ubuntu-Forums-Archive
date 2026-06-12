---
title: "Taking it form the top"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Hugh Jazz on 2006-02-02
Allright, so today I installed Ubuntu, because a friend of mine recommended it to me as a good first Linux distro to try.

But I am, in fact, a total noob. One of the first things I did was install Wine, as I was going to try and play some random game, just to feel safe that you actually can with Linux.

So I use the Synaptic Package Manager to get Wine into the system, but then I realized I have no idea what to do next. How do I start wine, how do I start any program with Linux?

I have no idea how to do anything, and no idea where to start looking for help. So if anyone could quickly point me in the direction of a nice little tutorial on how to get started, that would be really nice.

Thanks.

[EDIT] And it's supposed to be a "from", not "form". Damnit.

---

### Post by Lord Illidan on 2006-02-02
First off : Welcome to the forums ;)

I did a few searches on google on a simple Linux tutorial..

[http://www.linux-tutorial.info/link-360.html]("http://www.linux-tutorial.info/link-360.html")
[http://www.unixguide.net/linux/faq/]("http://www.unixguide.net/linux/faq/")
[http://www.unixguide.net/linux/linuxshortcuts.shtml]("http://www.unixguide.net/linux/linuxshortcuts.shtml")

If you come into difficulties while reading them, don't hesitate to ask or search... we were all new once, no need to feel ashamed.

---

### Post by Hugh Jazz on 2006-02-03
Well, I now know why I didn't find Wine anywhere. The package I installed was "wine_doc", which isn't what I was looking for, naturally. Now, I had a look at what went on when I reloaded all the repositories, and the [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ and [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
 both failed. So that's why I can't find Wine anywhere in the package installer. I don't suppose it has anything to do with amd64 not being supported, does it? It seems highly unlikely, to me..

Any help, muchly appreciated. Thanks.

---

### Post by steve.horsley on 2006-02-03
[QUOTE=Hugh Jazz]Well, I now know why I didn't find Wine anywhere. The package I installed was "wine_doc", which isn't what I was looking for, naturally. Now, I had a look at what went on when I reloaded all the repositories, and the [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ and [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
 both failed. So that's why I can't find Wine anywhere in the package installer. I don't suppose it has anything to do with amd64 not being supported, does it? It seems highly unlikely, to me..

Any help, muchly appreciated. Thanks.[/QUOTE]

wine is there in the universe repository, along with wine-doc. Search for wine and you should see them both, along with wine-dev (not needed).

---

### Post by Hugh Jazz on 2006-02-03
Hmm, well, it isn't there. When I type in "wine", there's only one choice available to me: wine_doc.

---

### Post by carlosqueso on 2006-02-03
Does your sources.list (type sudo gedit /etc/sources.list) look like this: ```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
``` If not, it should.  Then you should be able to get wine.

---

### Post by Hugh Jazz on 2006-02-03
Still no dice. I pasted all of that into it, reloaded the Package Manager, and still no Wine. I'll go have a look at the repositories again..

---

### Post by carlosqueso on 2006-02-03
Looking in the packages site, your first thought was right.  There isn't an AMD64 package for wine.  The i386 package  and source package can be found here: [http://packages.ubuntu.com/breezy/otherosfs/wine](http://packages.ubuntu.com/breezy/otherosfs/wine)  but I'm not sure about your results.

---

