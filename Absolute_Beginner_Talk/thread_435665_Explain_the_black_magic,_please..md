---
title: "Explain the black magic, please."
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Alex N on 2007-05-07
I'd like to discuss it in more details. It seems to me that many people here are using
Ubuntu. Currently I am going to delete it and forget this nightmare. But there's a lot
of curiosity. Can anybody explain me ?

I am following instructions found at Ubuntuguide.org carefully. Almost nothing works
properly. I am asking questions on forums. No answers. Well, my latest (and last)
attempt was to install something simple - yes - a game. I downloaded jDoom that
I am using on Windows and found out that it is distributed in src form. Great ! 
Someone told it's the best way to distribute programs. Again I followed the instructions
and - failed again. One important file controlling the make process is not there.
I downloaded the previous version - the needed file was there.

Look, people... I really do not understand. I am new to Linux, maybe I am doing 
something wrong, maybe... but no skill except black magic can place the file into
an archive if it is not there.

You are using Ubuntu - tell me please, HOW ? I clearly see it's impossible.
For me it is a very rare case when installed software just works.

---

### Post by Tomosaur on 2007-05-07
Well, first of all, compilation from source is **usually** a simple process, but not always. Generally, the correct way to do it is to change to the top-level directory (in the terminal) to wherever the source is, then type:
```

./configure
make
make install

```

The first command (./configure) should check that everything required is present. If not, it should inform you of what else you need to download and install before the compilation can continue. Now, some source packages really are unhelpful, and for those, you need to look for any documentation you can (usually in the form of a README or INSTALL text file included in the archive). 

In your case, it sounds like someone messed up archiving the files. You could send off an email to whoever is responsible and request a re-upload, or just to send you the necessary file. Alternatively, you can try just using the file from the older version, depending on how radical the difference between the two versions, the files may be identical.

Aside from that - best advice is to just stick to the repositories, in which case this kind of thing won't happen. However - it's not impossible to use Ubuntu - everything does 'just work' for me.

---

### Post by mikewhatever on 2007-05-07
Hi Alex N,
we have been over this before, I believe. :)

---

### Post by silkstone on 2007-05-07
I'm new to Ubuntu and still getting to know it - especially the terminal commands - but I date from DOS days so the concept isn't too strange. ;)

I agree that it can be difficult to get answers to questions - I've asked a few that haven't had replies - but I guess that's partly to do with the volume of traffic on these forums. A new message can disappear off the first page within a few minutes.

People's initial impressions of Ubuntu vary enormously, and it seems to depend partly on whether or not Ubuntu likes your hardware. We're trying to run Linux on machines designed for Windows, so compatibility can be an issue.

You ask how people are using Ubuntu. I installed Edgy on my desktop PC (P4 2.4GHz, 1.5GB RAM, on-board Intel graphics) and everything worked out of the box. I'm not into gaming, but everything I wanted to use - Firefox, Thunderbird, Open Office, Bibble, the GIMP, Rhythmbox, etc - just worked. It took a little while to get all the codecs (I used Automatix before reading that this was frowned upon in some quarters) but I got there.

When Feisty was officially released last month I tried it on my laptop (T2300, 1GB, Nvidia 7300) and that worked straight away too, including wireless networking. On Feisty the codecs were easier, as was the installation of 3D graphics drivers - it just invited me to install them. I've tried the Desktop Effects and they work, but personally I don't like the eye candy.

So the answer is that, for me, getting Ubuntu to do the things I wanted was really quite straightforward, especially with Feisty. The only limitation is that some software I need will only run under Windows, so I can't leave XP behind yet.

In contrast, I know of people who've tried Ubuntu and had no luck at all - especially with some ATI graphics cards - and have given up. Maybe if Dell and others do start producing machines designed specifically to run Ubuntu, and if the trend for easier codec/driver installation continues, some of the current problems will be solved.

---

### Post by LaRoza on 2007-05-07
You said some questions weren't answered. 

Here are a few tips for getting answers:

1. A good Descriptive title, "HELP!" is not good, "Help installing Codecs for mp3" is better.
2. State the problem first and then your system specs.
3. State what you did to cause the problem if the the problem occured after you changed or installed something.

Because of the volume on these forums, you can bump your question if it get pushed off screen.

---

### Post by forrestcupp on 2007-05-07
And you can't really blame Ubuntu for an unassociated software not working when you install it.  You wouldn't blame Windows if some obscure 3rd party software didn't install properly, would you?

---

### Post by croxi on 2007-05-07
ok, well, I had similar problems, but nothing quite so drastic as you're experiencing. In the end I decided that it was something to do with the original installation, so after a few partition problems, I ended up with the system I have loaded on my laptop now. 

UBUNTU has problems, and if you're expecting everything to "just work" then you're expecting to live in a perfect world. What advice I can give you is to reinstall ubuntu again and hopefully it will work better. 

I have proved this to be the case so why not try it. If you're dead set on deleting UBUNTU then maybe you could try a different version of Linux OS and maybe you will be happier. 

happy hunting...

---

### Post by justin whitaker on 2007-05-07
> **Alex N said:**
> I'd like to discuss it in more details. It seems to me that many people here are using
Ubuntu. Currently I am going to delete it and forget this nightmare. But there's a lot
of curiosity. Can anybody explain me ?

When you start out, you need to remind yourself that Linux is not Windows.

Once you get on the learning curve, you start to realize: there are good reasons why Linux and Unix does things this way, and they are actually quite a few elegant solutions. 

The whole apt (and others) package management thing: brilliant! Update the whole operating system, from apps to kernel, in one go. 

> I am following instructions found at Ubuntuguide.org carefully. Almost nothing works
properly. I am asking questions on forums. No answers. Well, my latest (and last)
attempt was to install something simple - yes - a game. I downloaded jDoom that
I am using on Windows and found out that it is distributed in src form. Great ! 
Someone told it's the best way to distribute programs. Again I followed the instructions
and - failed again. One important file controlling the make process is not there.
I downloaded the previous version - the needed file was there.

I have no experience with jDoom, so I cannot comment. Once you have build-essential on your system, Ubuntu can only compile what the jDoom team puts there. I hardly call that a strike against Ubuntu. Tell the jDoom group they missed a spot!

> Look, people... I really do not understand. I am new to Linux, maybe I am doing 
something wrong, maybe... but no skill except black magic can place the file into
an archive if it is not there.

Again, that's not Linux's fault: that is the application maintainer. Your issue on this piece of software is with them, not Ubuntu. If there is a critical file missing from the archive, one that jDoom needs to compile, then they screwed up. Pure and simple. 

> You are using Ubuntu - tell me please, HOW ? I clearly see it's impossible.
For me it is a very rare case when installed software just works.

I use it as my primary OS at home.

I have World of Warcraft running, Steam, a bunch of other applications. I've been doing some website authoring, audio mixing, and document production on my Desktop. I have compiled a bunch of apps that are not in the repositories.

Everything works, and if it does not, then finding help is easy.

I don't want to go on the offensive, or be offensive, so I will just say that targeted threads on specific problems are a much easier way to get help that histrionics.

---

### Post by Alex N on 2007-05-08
> **forrestcupp said:**
> And you can't really blame Ubuntu for an unassociated software not working when you install it.  You wouldn't blame Windows if some obscure 3rd party software didn't install properly, would you?

Certainly. I'm not blaming anyone, you see. But Ubuntu itself consists of several THOUSANDS
3rd party packages. What IS Ubuntu ? A particular combination of different software
written by different people.



[QUOTE=justin whitaker]The whole apt (and others) package management thing: brilliant! Update the whole operating system, from apps to kernel, in one go.[/QUOTE]

How can you call it brilliant ? It locked the software several times already on my computer.
Cannot deinstall, cannot reinstall. "package opera conflicts with package opera" - after deinstallation of opera I tried to install it again.

---

### Post by ramjet_1953 on 2007-05-08
One point that I'd like to make is that all of us need to crawl before we walk.

People often expect to load-up Linux and have it behave like Windows. It is not.

It has taken these same people years to feel comfortable with Windows and yet they complain after only a few days of Linux that something they are attempting doesn't work.

As a example, recently  a new user was attempting to compile a later version of an applicaion and posted that it wouldn't work. I asked him if he had installed build-essential , and his reply was "What's that?"

How many Windows users have ever used the command line in Windows and tried to compile software for themselves?

I would suggest that before anything is attempted beyond a standard install and using the Add-Remove menu, much reading, experimenting and asking questions is required.

If you are not prepared, or don't have the time to "go back to school", perhaps you are not ready for Linux yet.

Regards,
Roger :cool:

---

### Post by Alex N on 2007-05-08
2ramjet_1953:

What you're saying is correct, but it is not my case. Most people are somehow missed the
fact that I am using exactly the same software in Linux and Windows. Also I remember times
when the command line was the only way to work with computer. And even times when there
was no command line.

Of course I built a lot of software under Win - generally it is more hard to do, because
makefile -s are usually created for Unix.

I have several very clear and straightforward QA terms under which
I can almost always tell if the software is bad. Not so formal terms, however.

---

### Post by Terl on 2007-05-08
There is abig difference between open source and closed source too.  Windows shoves its standards down and everyone complies so stuff works (barring hardware issues).  Linux is open and some distros come with different packages than others.  Some things you do in one distro are a little different that others.  The "black magic" of it all is reading and research.  Sometimes just starting a program from the command line instead of trying its menu icon will reveal why it is not working.  Yes, sometimes one can get in dependency hell--especially when trying new programs and compiling yourself.  Nothing to do but find what is missing and get it.

The biggest thing has been said in this thread - Linux is not windows.  You may well find at some point that something you like that is available in windows just won't work in Linux without a great deal of effort and sometimes, it might not work at all.  But, one huge benefit of Linux is the community and the help available.

---

### Post by _Pieter_ on 2007-05-08
I agree with ramjet.. 
I can do a lot, and I mean A LOT.. with Windows. Installed Ubuntu 2 weeks ago, experienced a lot of crashes, errors etcetera but that's part of the learning process. I too have posted questions on this forum that remain unanswered, that's when I turn to IRC. Or I try to figure it out myself. It can be frustrating, but without errors you cannot learn.

---

### Post by zvacet on 2007-05-08
I´ll give you just one example.You ad that Opera conflicts with Opera.Explanation is simple.in repos you (all of us) have older version than one you want to install,and Ubuntu see it as conflict.In reality there is no conflict and you can install and run Opera as you wish.My advice(if I can give it to you) is to search,post,ask for help if something not going the way you think it should.At the end,if you decide not to use ubuntu it is O.K.I will not telling you how great distro it is and not using it is mistake,because I realy think that the best distro is the one you are most comfortable with.But,in the other hand I must say that I hope you will stay here.

---

### Post by Alex N on 2007-05-08
> **zvacet said:**
> I´ll give you just one example.
You ad that Opera conflicts with Opera.
Explanation is simple. In repos you (all of us) have older version than one you want to install,and Ubuntu see it as conflict.


Yes, but I deinstalled it. Some other software also has later or earlier versions on repos.
Synaptic just warns about it - no conflict. Moreover, when I tried to install THE SAME
opera package that was deleted - it did not work. When I downloaded the latest version
from Opera.com site - it worked. Both reported conflict.

another example :
First install of MySQL placed mysql script that could be used to start and stop mysqld daemon.
However it did not work. Any subsequent installations did not place it there, for unknown reason. 
The file is in the package, i checked.

---

### Post by onizu on 2007-05-08
New users will keep going back to MS-Windows (after facing difficulties, and especially after not being able to accomplish something on Linux that they could on MS-Windows). But the positive part is that the number of migrants going back to MS-Windows is decreasing with time, with the improvements in the alternatives, with the  improvements in the drivers, with new alternatives coming up.
Then there's a concern of the alternatives to be popularised as standards. Like the OpenOffice default document format isn't compatible with MS-Word. And saving some documents as .doc in OpenOffice doesn't save it in a very compatible form for MS-Word to open. Hm..
So hope one day the OpenOffice format will be more popular than MS-Word's. And the games on linux will have more realistic dynamism and graphics. And Mr. Alex N will return back to the free world ;-)
Until then, linux is very much fine for programmers. I, a graphic designer, use linux for my work. It isn't so easy as for a programmer using linux.

---

