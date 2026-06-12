---
title: "linux 10 - me 0"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2007-10-19
i have tried to install and run ubuntu on 10 occasions, each followed by a format and back to winders. how/where do i find all the commands i need to install software and arrange it the way I want it not the way tors linvald(sic) wants it,,,he seems to be nothing more than a scandanavian bill gates. here are a few facts...i finally got ubuntu to install with features like video, networking and other "misc" stuff, but i went to d/l and install a firewall, cause that is what i always install 2nd on my machines...well linux wouldnt let me copy anything from the dir i  d/l to...i found 2 places to change my permissions and i gave myself root, still no go,,,i need to install prob 90-100 programs and i want em arranged in a "master directory" and i DO NOT WANT TO USE THAT SYNAPTIC program, i want to be a ble to do research on a product then go find a real copy not some lame thing in synaptic. but noooooo linux wont let me do this. i copies my bookmarks (from a current b/u of them)and got the same message about i dont have permissions to copy from A to B.ok, see why i am sp po'd? i want to go to linux and have been tryin for almost 3 uears! if its so darn easy, why cant someone with over 35yrs experience in the data processing indystry, get real lucid nfo about how do do stuff under linux??? i liked kubintu but it doesnt come with firefox and if it wont let me install it so i gotta stay with ubuntu

---

### Post by hyper_ch on 2007-10-19
Have a read here:  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Then think about what you have written above.

---

### Post by 001100 on 2007-10-19
the problem with not accessing the files is because you need to be logged in as root. and second if your trying to use the synapic manager to download anything the servers still might be very busy.

---

### Post by lazyart on 2007-10-19
35 years in data processing = roughly 0 years in linux.
Everything in synaptic is there for convenience.  Most entries even tell you the home page so you can research if you wish.  If you choose to download directly from the site you may have to compile and install.  If you're still getting your feet wet in linux you probably don't want to even think about compiling anything.  Use synaptic, all that is done for you and you can easily remove it later.  And it's already been tested and won't do anything malicious to your system.
You're asking for help, but you don't want the help that's offered (synaptic).  That's a no win situation.
Don't be terribly concerned with installing the firewall.  Presuming you're behind a router and this is for home use, you're exponentially safer than you are with a Windows machine in the same situation.

Ninety to One Hundred programs?  That's a lot.  Your executables are generally all installed into /usr/bin.  There is your master directory.  

Welcome to our linux community, but you do need to learn our ways and customs.  Permissions (so you don't accidentally break your installation) and synaptic (so you can easily add and remove software) is how it's done.

---

### Post by chili555 on 2007-10-19
> find a real copy not some lame thing in synaptic.What's lame about an application in Synaptic, and therefor in the Ubuntu repositories? Please enlighten this seven year user of Linux.

On the other hand, if you search these forums for "compile," you will see dozens of posts where the poster has great difficulty compiling a .tar.gz, or tarball, written generically for any Linux ditribution.

I go out of my way to NOT use any package I can otherwise find in Synaptic.

---

### Post by scrooge_74 on 2007-10-19
[http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102)

It smells like Troll around here, one post every couple of weeks about starting to install, no more replies and again the same a few weeks latter.

---

### Post by SonicSteve on 2007-10-19
> **Jbirdie1 said:**
> i have tried to install and run ubuntu on 10 occasions, each followed by a format and back to winders. how/where do i find all the commands i need to install software and arrange it the way I want it not the way tors linvald(sic) wants it,,,he seems to be nothing more than a scandanavian bill gates. here are a few facts...i finally got ubuntu to install with features like video, networking and other "misc" stuff, but i went to d/l and install a firewall, cause that is what i always install 2nd on my machines...well linux wouldnt let me copy anything from the dir i  d/l to...i found 2 places to change my permissions and i gave myself root, still no go,,,i need to install prob 90-100 programs and i want em arranged in a "master directory" and i DO NOT WANT TO USE THAT SYNAPTIC program, i want to be a ble to do research on a product then go find a real copy not some lame thing in synaptic. but noooooo linux wont let me do this. i copies my bookmarks (from a current b/u of them)and got the same message about i dont have permissions to copy from A to B.ok, see why i am sp po'd? i want to go to linux and have been tryin for almost 3 uears! if its so darn easy, why cant someone with over 35yrs experience in the data processing indystry, get real lucid nfo about how do do stuff under linux??? i liked kubintu but it doesnt come with firefox and if it wont let me install it so i gotta stay with ubuntu

I say this as a windows user who recently blew the windows partition off my computer and now I completely use Ubuntu Linux. 
I also say this in the most sincere, humble and helpful way;
It sounds like you are needlessly beating your head against an imaginary wall. Synaptic is great it does things for you to save you much needless effort. In windows yes you could choose the directory to install to, heck even the windows\system32 folder if your whim desires. Linux gives you a home folder. There isn't really any reason I've found to put downloaded files anywhere else. If you want to learn Linux it has to be more of you going with the flow and adopting a new way of doing the same old things you did before. Not bad new ways, just different. You either embrace the change or needlessly beat your head against that imaginary wall.

The linux differences are not bad, there just not what you are used to.

---

### Post by Steveway on 2007-10-19
So if you don't want to use the features Linux has to offer that are not present in Windows, I mean real security and the package-manager, the I don't see why you want to use Linux.
Go and use Windows if you want to do it the "Windows-way" or else: adapt.

---

### Post by dasunst3r on 2007-10-19
As many have beat me to saying, Synaptic is a wonderful program you should familiarize yourself with.  A few benefits include:[LIST]
[*]Being able to install everything in gone go
[*]Dependencies are solved in one go
[*]There is no need to go Next -> Yes, I agree to sell my soul -> Next -> ...[/LIST]Indeed, it's a far cry from having to scrounge around CNet.

As to your permissions issue, it looks like you are just copying things to the wrong places.  As a few people have said, /usr is your "master directory."  Here are a few more I'd like to help you familiarize yourself with:[LIST]
[*]/home: User preferences, user data.  If you need to reformat, this is practically the only directory you will need to back up.
[*]/etc: Configuration files.[/LIST]I understand your frustration, and it clearly reflects how I felt about Linux several years ago.  It's going to take patience, but calm down and start asking questions.  Also, look around at the programs you already have.  You'll be surprised to see a bunch of programs ready to go right out of the box (Firefox included).

---

### Post by BrendanM on 2007-10-19
Yeah, wow. Synaptic is fantastic. Having one system to manage all the software on my computer (and keep it automatically updated!) is awesome and one of the key advantages over Windows/OS X. I get irritated when I can't use a repository and have to go find a program elsewhere. Maybe if you explained what it is that bothers you about synaptic, we could help you find an answer. Or maybe you should try Gentoo. I hear you have to compile every last program from source there.

---

### Post by SonicSteve on 2007-10-19
I really should add as encouragement that for the first few times I began the learning process it felt like banging my head against a wall. I was frustrated, but then I found this forum, started asking questions, searched the daylights out it to find answers without posting new threads and now I feel quite at home with ubuntu. Give it a chance, it's like hair, it grows on you! At least for most people.

---

### Post by amlucent23 on 2007-10-19
guys... truthfully, I think you are wasting your time with this. Some people dont actually want help and some people dont believe that software is good unless you have to pay for it... I think this guy is both. 

and I know this is a waste of breathe but the OS comes with a firewall. if you would like a easy gui program to control it try firestarter. I would tell you how to install it, but it sounds like you want to compile it. - good luck, have fun.

---

### Post by Chuck58 on 2007-10-19
Hey, I'm totally illiterate with Linux. Tried Red Hat 6 many years ago and promptly went into nervous prostration. It all reminded me too much of DOS, with commands for this and that, none of which seemed to work. I returned to Windows and have been there ever since, until Ubuntu 7.04 appeared and I burned a live CD. It's as friendly and almost as easy to used as that overpriced alternative from Redmond Washington.

As somebody old enough to fondly remember, and still use, a manual typewriter more than the computer, I don't buy into the original posters complaints about Ubuntu. I'm bordering on old age and find Ubuntu and a couple of other flavors of linux very to use. Even setting up my printer, which I absolutely can't live without, was easy. I've used the command line once, and then it was a simple copy the command and paste it into the command line.

Since reading this forum for the past few weeks, I think M$ trolls occasionally invade the place.

---

### Post by nchase on 2007-10-19
Has anyone seen this user's [posting history]("http://ubuntuforums.org/search.php?do=finduser&u=80273")? Something is clearly not clicking.

 I wonder where the disconnect is?

Jbirdie1, I think you should give the "Linux is NOT Windows" article posted earlier in this thread a thorough reading.

---

### Post by scrooge_74 on 2007-10-19
He post once and never comes back to that same thread, all his post are OP, at least if he replied with the same level of energy as his last OP you could put him in a category

[http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102)

---

