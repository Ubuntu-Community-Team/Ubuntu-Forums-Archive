---
title: "Hello ubuntu  (10 unbelievably longwinded questions)"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by glassgloss on 2006-01-23
Awesome! you guys are so helpful.

Hey, a couple more questions that have cropped up...

When people just start telling me to type these crazy commands into the command line (which doesn't scare me toooo badly-- from my dos days) specifically about wine and automatix...

1. Don't I need to be connected to the internet to get those to work?

I am having difficulty understanding why nobody is telling me to, "go download such and such"

2. also:  ubuntu pronunciation?  heheh...  Do you refer to your operating system as ubuntu or as linux?

last question:
3. I am going to ask this question in the music forum I frequent ([www.harmony-central.com](www.harmony-central.com))  but do you know of any good recording software for linux?

---

### Post by glassgloss on 2006-01-23
So windows crashed on me for the last time.  I downloaded, burned, and installed the ubuntu iso.  

I have always been very interested in linux, and am glad that I am finally trying it.  I have spent the last 3 or 4 days reading up on linux and ubuntu, and, like everyone else, am left with a bazillion questions.  

I am very presistant and trustful of what I have heard about linux, so don't worry about discouraging me-- but I would like a little more personal help since I am having difficulties swallowing the dry and otherworldly tutorials (though I will continue reading them despite frustrations...;) ).

So first off.  I want the windows games that I have left behind to run... if possible... with a linux os.  I have read up on wine, and--after searching for something called a repository in some sub menu under adminstrators--could not seem to find it.  So my questions are:
1. does wine come with ubuntu
2. will I need wine to run these games and are these games possible to run with ubuntu?
  a. Baldur's Gate I and II
  b. Hereos of Might and Magic III
  c. Starcraft
3. What is a backport, and do I need to backport wine to use it with ubuntu?


So then there are some other questions
4. Can I network ubuntu with a windows xp computer to play the games listed above with a friend?
5. Can I do it with his mac?


And some more:  I am a college english major, and have become tight nit with microsoft word.  I understand that I cannot use that with linux, and have scoped out the alternative.  The questions are these:
6. Eng prof's have strict formating requirements including margin's, header's and footers, text size, and font.  Will I be able to meet these requirements with the text editor that comes with ubuntu?
7.  If I need to take a document that I have worked on at home on my linux, to a windows computer lab, will I be able to access and use the document in microsoft word without terrible formatting and compatibility errors.

And my last questions (I am so sorry for this--it is probably torture for you) When I installed ubuntu I really had no idea what I was doing and I don't know if I partitioned my drive correctly.  I am deffinitly not opposed to repartitioning my drive because I previously backed up all of my important documents from windows onto a lacie external harddrive.  I cannot be sure of the partitions and size because I am typing this from a windows computer lab and my ubuntu is back at home, however, the way I understand it is-- I had a 20gig drive (laptop).  Apparently my free disk space is about 14 gigs.  I have a swap partition, and a root partition(I think), and possibly something else.  My questions are:

8.  does 14 gig free seem appropriate, or does it appear I have alot of wasted free space somewhere?

9.  is ubuntu installed on its own partition, and what partition is it installed on, so that I can revert back to a blank slate if needed.

10. what is swap, and what is root

I really appreciate any attempt at guidance--even if it is just a, "hey, read this link, then come back"  but if you could answer any number of my questions, I would love it!

I am really excited about ubuntu!
thanks.

---

### Post by the_it on 2006-01-23
> 1. Don't I need to be connected to the internet to get those to work?

I am having difficulty understanding why nobody is telling me to, "go download such and such"
When the commands generally have "apt" anywhere in them, yes, you need to be connected, however, if you set up your networking already, then you don't have to worry about it.

Secondly, ubuntu uses the debian apt package system, which places a lot of software in a repository for convenient dependency checking.  Basically, it makes the process of download-installing apps from the net easier when they're in the repo and our repos have thousands of stuff out there to look for.  When someone tells you to "apt" or "apt-get" something, he's prolly already talking about the command line, so you don't have to look for the package on the net anymore.

> 2. also: ubuntu pronunciation? heheh... Do you refer to your operating system as ubuntu or as linux?
This is actually a non-trivial question with some politics behind it.  Basically, there are a lot of linuxes out there, and if you just say linux someone may think that you are using something else.  Ubuntu is officially the name of this os, being a variant of the GNU/Linux OS, aka Linux.  I use either.  If I'm talking to windows users, I say Linux (coz that's about as much as they know), but if I'm talking to linux users I say ubuntu, with all u's having the same sound as put.

---

### Post by niviche on 2006-01-23
Hello,

[QUOTE=glassgloss]6. Eng prof's have strict formating requirements including margin's, header's and footers, text size, and font.  Will I be able to meet these requirements with the text editor that comes with ubuntu?[/quote]

Yes, the word editor from OpenOffice, which comes with Ubuntu, can do all this.

[QUOTE=glassgloss]7.  If I need to take a document that I have worked on at home on my linux, to a windows computer lab, will I be able to access and use the document in microsoft word without terrible formatting and compatibility errors.[/quote]

Microsoft word has trouble reading OpenOffice document, but you can save your OpenOffice documents as .doc files, so this is not a problem at all.

[QUOTE=glassgloss]8.  does 14 gig free seem appropriate, or does it appear I have alot of wasted free space somewhere?[/quote]

I have Kubuntu installed on a 19 gig partition, and this is more than enough to run the programs I use.

[QUOTE=glassgloss]9.  is ubuntu installed on its own partition, and what partition is it installed on, so that I can revert back to a blank slate if needed.[/quote]

Ubuntu is installed on its own partition, which is not formatted like the Windows partition. So either you wiped out the Windows partition, or you created a new partition with Ubuntu on it.

[QUOTE=glassgloss]10. what is swap, and what is root[/quote]

AFAIK, the swap partition is a partition used by programs in Linux to put temporary files. The root one is where you have all the "real" stuff (Ubuntu, programs, home folder...).

Good luck, and have fun with Ubuntu. :)

---

### Post by glassgloss on 2006-01-23
Thanks a bunch!

---

### Post by dueY on 2006-01-23
[QUOTE=glassgloss]

1. does wine come with ubuntu
2. will I need wine to run these games and are these games possible to run with ubuntu?
  a. Baldur's Gate I and II
  b. Hereos of Might and Magic III
  c. Starcraft
3. What is a backport, and do I need to backport wine to use it with ubuntu?
4. Can I network ubuntu with a windows xp computer to play the games listed above with a friend?
5. Can I do it with his mac?
6. Eng prof's have strict formating requirements including margin's, header's and footers, text size, and font.  Will I be able to meet these requirements with the text editor that comes with ubuntu?
7.  If I need to take a document that I have worked on at home on my linux, to a windows computer lab, will I be able to access and use the document in microsoft word without terrible formatting and compatibility errors.

8.  does 14 gig free seem appropriate, or does it appear I have alot of wasted free space somewhere?

9.  is ubuntu installed on its own partition, and what partition is it installed on, so that I can revert back to a blank slate if needed.

10. what is swap, and what is root
[/QUOTE]


1. No
2. You will probably need Cedega.  From what I hear it is pretty tough to set up.
3. A backport is a repository not run by the official Ubuntu team which may include updated (possibly unstable) binaries not in the official repositories.
4. You should be able to.
5. You should be able to.
6. Open Office should.  Play around with it and find out.
7. You can save documents in Microsoft Word format (.doc) but I have no experience with that yet.
8. It does seem a bit low for some reason?
9. Yes it has it's own partition. ```
sudo fdisk -l
``` to find out which
10. Swap isn't a Linux thing, Windows has it too.  Think of it as extra RAM, but it's on your harddrive so it's slower than RAM.  Root can be thought of as the admin account.

---

### Post by BobSongs on 2006-01-23
[QUOTE=glassgloss]1. does wine come with ubuntu[/quote]No. But it's not difficult to install it. Open up a command prompt (terminal = Applications > Accessories > Terminal) and do the following:```
sudo apt-get install wine
```Keep the command prompt open. After Wine is finished installing enter the following command:```
winecfg
``` and set your parameters. If you've got some DOS games that need a simple enough DOS environment, install DOSBox:```
sudo apt-get install dosbox
```Then run it:```
doxbox
```
> 3. What is a backport, and do I need to backport wine to use it with ubuntu?Just run the wine configuration. But if you ask me, I suggest you download and install [Automatix]("http://ubuntuforums.org/showthread.php?t=66563"). Wine is one of the many listed items it will download and install for you. You've still got to run 'winecfg' once it's done. But it'll tell you that. ;)

Automatix will also update the default OpenOffice.org's 1.9 to 2.0 final release. Recommended. I'll leave the other questions to others to bravely answer as I'm not a gamer.

Bob

------

Kudos on the Ubuntu install. I've used Windows since 3.0 and help many people with their machines. Since I've switched I sleep better at night. Honestly.

---

### Post by jasay on 2006-01-23
[QUOTE=glassgloss]1. does wine come with ubuntu[/QUOTE]No.  Wine is not included by default.  You can install it easily by using synaptic (System > Admininstration > synaptic package manger) and running a search from there.
[QUOTE=glassgloss]3. What is a backport, and do I need to backport wine to use it with ubuntu?[/QUOTE]Ubuntu makes a new release every 6 months, but the software is not updated during the interim (except for security updates.)  For those who want newer software, packages can be "backported" from the next version of Ubuntu that has not yet been released.  It's an easy way to get the newest software without compiling it yourself.  

For the most part it is best to have the newest version of wine and there have been some major steps in wine development since Breezy was released.  The best way to get the newest wine is from their own website rather than the backports.  Read up on how to that [here]("http://www.winehq.com/site/download-deb").
[QUOTE=glassgloss]So then there are some other questions
4. Can I network ubuntu with a windows xp computer to play the games listed above with a friend?
5. Can I do it with his mac?[/QUOTE]If you can get the games running on your computer and he can on his, you should be able to play online/networked.  Run a search or two on the games you listed in the Gaming section of the forum and then ask a few questions there.  I want to say that some of those games have been made to work, but I don't have them so I can't say for sure.

EDIT: Bwahaha.  Good thing I don't try to enter speed typing competitions.

---

### Post by mohapi on 2006-01-23
Hi. I'm also new to Ubuntu and Linux in general, and since I had a lot of the same questions you do, I can save you a little time looking for answers. ... :)

[QUOTE=glassgloss]1. does wine come with ubuntu[/QUOTE]
No, but it's easy enough to install. I **strongly** recommend the [Automatix installer script]("http://ubuntuforums.org/showthread.php?t=66563") for that, because it will install Wine, plus a lot of other things you'll probably want ... like Acrobat Reader, Java, media plugins for Firefox, etc. That installer was the best thing I ever found for Ubuntu.

[QUOTE=glassgloss]2. will I need wine to run these games and are these games possible to run with ubuntu?
  a. Baldur's Gate I and II
  b. Hereos of Might and Magic III
  c. Starcraft[/QUOTE]
Probably, but if you need to know for sure, there's a [site for Wine]("http://www.winehq.com/") that will tell you what works and what doesn't. It seems to me that the older games work better, while newer, flashier games are still touchy. I keep a dual boot system just for games, although I find I spend 99 percent of my time in Ubuntu.

[QUOTE=glassgloss]3. What is a backport, and do I need to backport wine to use it with ubuntu?[/QUOTE]
You can get lots of information about backports [here]("http://www.ubuntuforums.org/showthread.php?t=40291"). 

[QUOTE=glassgloss]4. Can I network ubuntu with a windows xp computer to play the games listed above with a friend?
5. Can I do it with his mac?[/QUOTE]
Networking is not my strong point, so I'll leave that to others to help you with.

It looks like most of your other questions have been touched on. Good luck!

---

### Post by halfvolle melk on 2006-01-23
On the topic of gaming:
[http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)
[http://frankscorner.org/index.php?p=rpg](http://frankscorner.org/index.php?p=rpg)

And maybe these are of help:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://wiki.linuxquestions.org/wiki/Gaming_via_Wine_or_WineX](http://wiki.linuxquestions.org/wiki/Gaming_via_Wine_or_WineX)

I might add that I found [Crossover Office](http://www.codeweavers.com/) usefull. Crossover Office is not free.

---

