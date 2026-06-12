---
title: "A few questions."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by allllec on 2008-01-06
Erm.. just a few silly questions. thinking abotu switching to ubuntu from windows vista but i want to know a few things first..

64bit version.. ive got 4gig of ram so i will be using this.. is it "okay" as in i wont run into any problems that i wouldnt get on 32bit ? like applications will work etc.

i have x1950 pro.. will that work okay ? bearing in mind i will want to run a game (next questions)

counter strike source.. i found a guide to use wine to run it in linux.. will it work do you rekon ?




and a very trivial questions.. is there anywhere that explains what all the folders are on the filesystem drive? like in windows you've got users for user profile stuff.. windows for system files.. program files for well progrm files etc.. anyone care to explain breifly what things like lib, usr, home etc are in ubuntu. or is it documented anywhere?

also trivial questions. where is firefox profile stored ?

cheers

alec

---

### Post by TBerben on 2008-01-06
So far the only program that might be a hassle on 64-bit is Adobe's Flash Player (at least: it is the only program I know of that might be a problem) but I believe there is a workaround. Either Ubuntu's restricted driver managment app or  [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") should do the trick in configuring your graphics card. As far as wine goes, I haven't had any particular successes with it. In my experience its a pain to get something working in it.

To find out what the directories for I suggest you read the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) (a very nice read) which explains what everything is meant for. Another great source of information on how everything works in a Linux distribution is the e-book [Slackware Linux Essentials](http://www.slackbook.org), which inclues some Slackware specific stuff but is mostly generally applicable to any distro.

---

### Post by overdrank on 2008-01-06
> **allllec said:**
> Erm.. just a few silly questions. thinking abotu switching to ubuntu from windows vista but i want to know a few things first..

64bit version.. ive got 4gig of ram so i will be using this.. is it "okay" as in i wont run into any problems that i wouldnt get on 32bit ? like applications will work etc.

i have x1950 pro.. will that work okay ? bearing in mind i will want to run a game (next questions)

counter strike source.. i found a guide to use wine to run it in linux.. will it work do you rekon ?




and a very trivial questions.. is there anywhere that explains what all the folders are on the filesystem drive? like in windows you've got users for user profile stuff.. windows for system files.. program files for well progrm files etc.. anyone care to explain breifly what things like lib, usr, home etc are in ubuntu. or is it documented anywhere?

also trivial questions. where is firefox profile stored ?

cheers

alec

HI and as for the 64 bit you may look here
[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)
There is issues with ati graphics cards but some have them working and as for games I would say that if your dual booting then keep windows for games, that is my opinion of course.
For the file system maybe this link can help
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

### Post by Daveth on 2008-01-06
it is getting on a bit now, but this page is still quite useful for all steamy type games

[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

Half Life 2, Portal and Steam generally ran well under Feisty- just upgraded to Gutsy so may have to tinker a bit to return to where I was.

all of your configuration files live in home, but as they are . files, you need to do ctrl+h to reveal them.

this

[http://linuxreviews.org/beginner/index.html.en](http://linuxreviews.org/beginner/index.html.en)

for a quick skoot through the filesystem, and many other delights...

---

