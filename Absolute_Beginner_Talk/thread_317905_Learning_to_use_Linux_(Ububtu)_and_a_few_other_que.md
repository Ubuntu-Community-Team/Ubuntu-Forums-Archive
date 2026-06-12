---
title: "Learning to use Linux (Ububtu) and a few other questions."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by nineteenfingers on 2006-12-13
I was going to post several treads as some of these issues aren't exactly connected, but I thought it would be easier to make a single one for most of them.

I'm making the switch to Linux after several years as a Windows user (or as I read in another thread on here - a W*ndows user - much to my amusement) - the last 2 years of which, using XP.

While I really like the feel of Ubuntu (which I ran 6.1 Edgy from a DVD to try it out and leave my HD intact to protect my work) I'm left short of an answer on a few issues. If anyone can either answer them, or point me to a resource that they can recommend it would be appreciated. That said, on with the show...

1> When it comes to updates and support, I understand there is an update release ever 6 months, and have been told that Edgy only gets "18 months of support" as compared to the "3 to 5 years" for  Dapper.
In practical terms, what would that mean to me?

I've been told (thanks taurus) that it means I'd get security updates and bug fixes for 18 months, but after that 18 months, am I likely to be encountering problems (security etc.) where that would be a serious issue?

Also, 18 months from when? From each update (if I install it) or from whenever it was Edgy was released?




2> Being a recent convert (i.e. the last 24 hours) I've really not had a chance to play with Linux much yet. I'm aware that there are some major fundamental differences between Linux and Windows, not only in security but also in general use.

The good thing about Windows is that I've just been able to get the basic set up done, install my software and I'm done. The OS updates itself, installs are a matter of clicking a file and it is done and that's about it.

I'm in no way opposed to learning to do a lot of that for myself, and when I first used computers I learned on an MS-DOS prompt, but I really don't know where to start with Linux. Even some of the code I've seen on here are beyond me, things like ```
sudo aptitude install kubuntu-desktop
``` are beyond me.

Is there somewhere to learn these basics. While I am a big fan of the "trial and error" route - with the amount of work I've got on at the moment, there's a bit too much "error" in the learning from scratch way for me to learn that way.



3> Are there any websites/books you can highly recommend?
I'm thinking mainly for the purpose of getting to grips with Linux as a user, and on from that using to customise it exactly to my needs as opposed to working around the OS like with "certain other mass-market ones" ;)



My main uses are:
CAD (I use AutoCAD and need to avoid switching packages as far as I possibly can)
Photography (Minor photo manipulation - I'm already a GIMP user though playing with the idea of getting Photoshop)
I'm also starting to play with video editing - but that's nothing more than an idle hobby I devote little or no time to at the moment.

I'm not particularly after specific advice about those uses, though if they might affect your answers to the above, please do take them into consideration.

Thanks a million folks.

---

### Post by rlozano on 2006-12-13
First, Welcome to Ubuntu LINUX! :-)

as for a starter, (particularly ubuntu) i'm not sure if you have visited this site [www.psychocats.net/ubuntu/](www.psychocats.net/ubuntu/).

[www.linux.org](www.linux.org)
[http://www.informit.com/guides/content.asp?g=linux&seqNum=3&rl=1](http://www.informit.com/guides/content.asp?g=linux&seqNum=3&rl=1)

lots of good things for those starting out with Ubuntu and linux.

hope this helps.

---

### Post by rich.bradshaw on 2006-12-13
sudo apt-get install "package name"

sudo = do this as superuser (also known as root user - you can change system settings as root only.)

apt-get = software that we use to install/remove software

install = install (could also be remove if you wanted to uninstall)

"package name" = name of what you want to install. So if you wanted to install htop, a process monitor you type

sudo apt-get install htop

to uninstall use

sudo apt-get remove htop

easy!

---

### Post by rich.bradshaw on 2006-12-13
oh, and about support - Linux is an on going process, so there are small updates almost every day.

Dapper was released with as much of it stable as possible, and there is an agreement that they provide support for a long time. If you are a company this is important as you don't want to roll out a whole operating system with no support!

For the average user, it doesn't make much difference. Edgy is newer but less stable (apparently - I can't tell!), Dapper is older but more stable.

Personally I like to use the newest of everything so I'm with Edgy for now.

---

### Post by A_608 on 2006-12-13
Here's a site to learn commands.

[linuxcommand.org]("http://linuxcommand.org")

I'm a beginner too. I have found this helpful.

---

### Post by nineteenfingers on 2006-12-13
Thankf for the links rlozano. I've not been on any of those sites yet.
I've been thinking about making a switch to linux or unix for a while, but on a whim yesterday decided to buy a magazine with a distro on the disk. Rant it, loved it, made my decidion to switch there and then.

As such this is the first site I've come across (if I rememer correctly, it was linked on the disk somewhere - that or I searched ubuntu forum on google - can't remember which but either way it got me here) so the amount of background reading and other sites amount to pretty much nothing.

I'll make a note of the URLs and have a look later on when I don't have work to do.


rich - thanks for the explanation of the code. Where exactly would one type that in though? Working on a command prompt it is rather easy to tell, you just type, but in a GUI I'm not entirely sure yet - though this evening's playtime should answer that now I'll be looking for it.

I take it you'd have to have the file installed on your system already right? Then browse to the directory it was in before running the command to install it. Or is it something different?


One of the things I like about Linux is the ongoing nature. There's noone saying "this is a fully working system" and then everyone finding hole after hole in it and it all being a bit silly. The fact Linux is a good system being constantly checked, updated and so on, is quite appealing to me.

From a work point of view - my work computer is my own computer. I work for myself so I won't be running any major systems on it. Just my work programs (AutoCAD and SuperBeam 4), printer drivers, pdf writing, and access to email and I'll have enough to be getting on with.
Stability, well I've seen a few people on here and the one or two other sites I've read briefly saying that "unstable" is a comparitive term and that mostly people have no problems with Edgy, I'm in the habit of regular saves of my work, so a crash, while inconvenient (or a big problem minutes from a tight deadline) a crash wouldn't be the end of the world.

My copy of XP is remarkably stable compared to how 95 and 98 treated me, but even then it does encounter the odd problem here and there. If Ubuntu is roughly as stable as XP I'd be happy - if it is more stable (and I've been told by various Linux users I've met in the past that it is) then I'm ahead.


EDIT
-----
A_608
I've noted that link down too. I'll read this evening. Thanks :)

---

### Post by lyceum on 2006-12-13
If you want some good books to refreance, here are my top picks:

Ubuntu Hacks - This is just facts, but they are rated as to how hard they are, which lets you know if you might need more help from the forum or can do it on your own.

The Ubuntu Guide - written by members of the comunity.

I have found that most of my questions can be answered in these 2 books. The second one is great for getting started, and the first is great for learning all the cool new things you can do. It takes you to the next level.

There is also a an online book to get you started:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

If you buy anything, go to amazon.com, they have the best prices I have found.

[http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942/sr=1-1/qid=1166017284/ref=pd_bbs_sr_1/104-9028656-6779965?ie=UTF8&s=books](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942/sr=1-1/qid=1166017284/ref=pd_bbs_sr_1/104-9028656-6779965?ie=UTF8&s=books)

[http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=1-4/qid=1166017305/ref=sr_1_4/104-9028656-6779965?ie=UTF8&s=books](http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=1-4/qid=1166017305/ref=sr_1_4/104-9028656-6779965?ie=UTF8&s=books)

Enjoy!

---

### Post by TooRight on 2006-12-13
Welcome to Ubuntu!! :D

I know seeing all the posts telling you sudo this and that seem daunting at first, but soon it will all be old hat to ya and you'll wonder how ya ever got on without the terminal. I have a duel boot going with xp and I absolutely deploreeeeeeeee having to boot into windows now. I do it so rarely now that I often find myself confused in it when I try to do stuff, lol!!

All the sudo this and that's are actually just what you copy and paste into your terminal, one line at a time, to get things done. Don't even worry about trying to remember them all. In time many will become second nature to you, but for now, just copy and paste, hit that Enter key, then sit back with a cup of coffee and big grin on your face and watch in wonder as Ubuntu does the work for you :D

---

### Post by Judicata on 2006-12-13
First, a terminal window can be accessed by default in Applications -> Accessories in the Menu.

Second, the packages *do not* have to be on your computer.  Ubuntu works with repositories of software.  You can actually browse some of them with the "Add/Remove" function of your Applications menu (just has some common packages listed) or through Synaptic in the "System -> Administration" menu.

A word of caution, though.  If you have work specific software, make sure there is a linux substitute, or it can somehow be run on linux.  Linux does not run Windows software by default (two programs - Wine and Crossover Office - do allow some common windows programs to run in linux).  Otherwise, you'll need to dual-boot (booo).

Sift through some of the basic guides people have pointed out and this will all be answered.

---

### Post by winvado on 2006-12-13
I would think very hard about swapping to linux if you have a stable working operating system. There really is no need, however,if you have time on your hands and a need for a nuts and bolts server solution then good luck, but the downfall of ubuntu linux is that it is incapable of easily communicating with windows an its networking ability - an ability to communicate with windows is very poor and is well,complex, try a simple example of logging into a windows VPN and then connecting to a windows desktop. What other "forum" leaves about (by my count) about 70% of questions not answered - or shovels you off to "phsycocats" for gods sake and countless other sites. It really is very poorly documented. Trust me stick with what is easy otherwise you will find yourself reading polls like " why did you come out learn to love linux". ie a right of passage ( the termianla) than actuall adopting anything better.

---

### Post by BarfBag on 2006-12-13
Welcome to the world of free software!

Linux for Dummies is pretty good (though, quite a few disagree with me).  Another one is Point and Click Linux, but that deals with another Linux distro called SimplyMepis.

Here are some links to get you started:

[http://www.getautomatix.com/](http://www.getautomatix.com/) (Install script, automatically installs things like DVD/MP3 support, graphics drivers, etc.)

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Looks like everybody else beat me to the rest.

---

### Post by psycosmyth on 2006-12-13
Windows is fine, most of us here dualboot with it. We just like to be different by having total control of our machines.

---

### Post by loyaleagle on 2006-12-13
Isn't that part of the fun, learning something new. A new way of doing things that is user friendly and easy.

Here is where I learned so much. I was passed on to me just a week or so ago.

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)


Good luck and don't give up!

---

### Post by Patrick-Ruff on 2006-12-14
umm, Linux has been very compatable with my windows network, as well as my school, I don't see your problem here, I don't know waht a VPN is, if I've ever used one it worked for me, if not, then I doubt very many people use VPN's anymore anyways.

so, such things are very much dependant upon what you actually use linux for.

---

### Post by swp6499 on 2006-12-14
ive been a ubuntu user for roughly 10 months now and also was wary of the dreaded command line...but my friend has been a long time linux user and helped me through some of my woes and without a doubt the ubuntu forums community is a great place..ive never posted one question and didnt get an answer on here..also another thing that helped me with command line was a gentoo install....it made me learn command line which significantly helped me in ubuntu...so if u have any questions do not hesitate to post..the folks on here are great...and thanks for all the help everyone

---

