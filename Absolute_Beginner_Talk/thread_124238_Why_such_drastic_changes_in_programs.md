---
title: "Why such drastic changes in programs?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by jimw on 2006-02-01
First off, please understand that I am not really dissing the distro.  

However, I am a writer, and OpenOffice is my program of choice.  There seem to be difficulties with installing things on Ubuntu (and Debian) though.  Several times on the OpenOffice list I've seen people write in about this or that problem they're having with the Debian version of the program, and the people on the list (all volunteers)  usually say something to the effect of "take it up with the Debian people, because we have no idea of what they might or might not have done to the program."

Just recently I've seen it mentioned that the Ubuntu version of OpenOffice 2.0.1 lacks a Thesaurus.  I'd been wondering if it was just me not being able to make things work right, but apparently not.

I can't understand why such drastic changes would be made.

I've just gone through the process of running the "official" OpenOffice RPMs through alien.  Seems like an easy procedure.

Of course, I'm nothing like an expert, and I'm not sure what problems this might cause.  However, I have to ask, since it's so simple, why don't they just do that, and put them in the repository?  What is the necessity for a procedure that can change the program so drastically?

JimW

---

### Post by MartinG on 2006-02-01
It is possible to install the Debian version of the en_us thesaurus into Ubuntu, but you have to fiddle with the control file (as far as I recall from when I did it), because Ubuntu still call the app openoffice.org2 while with the release of v2 Debian has renamed everything to openoffice.org, so without the fiddling you get all sorts of dependency messages.

---

### Post by jimw on 2006-02-01
[QUOTE=MartinG]It is possible to install the Debian version of the en_us thesaurus into Ubuntu, but you have to fiddle with the control file (as far as I recall from when I did it), because Ubuntu still call the app openoffice.org2 while with the release of v2 Debian has renamed everything to openoffice.org, so without the fiddling you get all sorts of dependency messages.[/QUOTE]

As I mentioned, I used alien to install the version from the OpenOffice site.  

My question was, why do such drastic changes get made in readying programs for Ubuntu, or Debian?

If I, simply by following the instructions here:

[http://doc.gwos.org/index.php/Install_Ooo2](http://doc.gwos.org/index.php/Install_Ooo2)

could install the program, with the thesaurus, why was it necessary to make such drastic changes to it?

I don't believe that someone said, "It's too much trouble to put in the Thesaurus, forget it,"  but more likely that someone forgot to put in a connection.

If it was necessary to fix up a "Debian/Ubuntu version, why not just run the official version through alien, and put that up?

Again, I know little about programming, and I'm willing to listen to an explanation.

JimW

---

### Post by MartinG on 2006-02-01
[QUOTE=jimw]As I mentioned, I used alien to install the version from the OpenOffice site.  

My question was, why do such drastic changes get made in readying programs for Ubuntu, or Debian?

Again, I know little about programming, and I'm willing to listen to an explanation.

JimW[/QUOTE]Sorry, I misread your first post; I thought the use of alien was something you'd wondered about, not something you'd done.

As to the question itself, I don't know directly. I *do* know that with some earlier versions of OOo the alien way of doing it caused problems and needed some tweaking.  Apart from this, I *think* you'll find that the files are all installed somewhere different from the (K)Ubuntu standard.  This may not be a problem in itself, but any other program that interacts in any way with OOo will not find the files where it expects them, and therefore fail.

---

### Post by TeeAhr1 on 2006-02-01
*this post is a placeholder*

So that when I get home I will remember to post the (custom) repository address containing the fully functional version of OOo.

As to why this is so, I haven't the faintest idea.

EDIT: Here it is, just tack it to the bottom of /etc/apt/sources.list and refresh in Synaptic.  Whoever maintains this is great, s/he had the 2.0.1 version up within a week of release.

> ## Openoffcice.org 2.0
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by jimw on 2006-02-03
[QUOTE=TeeAhr1]*this post is a placeholder*

So that when I get home I will remember to post the (custom) repository address containing the fully functional version of OOo.

As to why this is so, I haven't the faintest idea.

EDIT: Here it is, just tack it to the bottom of /etc/apt/sources.list and refresh in Synaptic.  Whoever maintains this is great, s/he had the 2.0.1 version up within a week of release.[/QUOTE]

The problem has already been solved, as I mentioned.  I got OpenOffice 2.01 from the OO site, put it through alien, and away I went.

The _question_ was, why do they have to do such drastic changes to a program that they leave out a whole important section?

And in addition, on the OpenOffice site, a part of the desktop-configure file includes a method to install it to Debian.  That being so, I doubt that alien is going to do anything too strange to it.

I realize that any time now, someone is going to tell me to go back to Mandrake; I won't.  Ubuntu is too nice and simple for me.

But I'd certainly like more of an explanation for the situation than "because that's how we do it."

I can get that from Microsoft. :) 

JimW

---

### Post by eyeprotocol on 2006-02-21
[QUOTE=TeeAhr1]*this post is a placeholder*

So that when I get home I will remember to post the (custom) repository address containing the fully functional version of OOo.

As to why this is so, I haven't the faintest idea.

EDIT: Here it is, just tack it to the bottom of /etc/apt/sources.list and refresh in Synaptic.  Whoever maintains this is great, s/he had the 2.0.1 version up within a week of release.[/QUOTE]


Hello. This repository (?) does not add itself (!!!). Obviously i am an ubuntu newbie. I added the lines, i opened the synaptic manager and i get this error:

[I]W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)[/I]

Could you please help?

Regards

---

### Post by cwaldbieser on 2006-02-21
[QUOTE=jimw]
The _question_ was, why do they have to do such drastic changes to a program that they leave out a whole important section?
JimW[/QUOTE]
Every distro is a little different, and most apps are **very** configurable.  So my guess would be that the Thesaurus may have been overlooked.  There are a whole lot of packages, so it may have been easy to overlook a feature in one.

I don't think you can generalize that because one application had something different about it that there are lots of *drastic* changes to programs in Ubuntu compared to another distro.

---

### Post by jimw on 2006-02-23
[QUOTE=cwaldbieser]Every distro is a little different, and most apps are **very** configurable.  So my guess would be that the Thesaurus may have been overlooked.  There are a whole lot of packages, so it may have been easy to overlook a feature in one.

I don't think you can generalize that because one application had something different about it that there are lots of *drastic* changes to programs in Ubuntu compared to another distro.[/QUOTE]

I won't argue this one, at least not about the generalization.

However, I am a writer.  A fully-functioning Wordprocessor, with all features intact, is not just a nice thing to have, it's a necessity.

I believe I have mentioned before that, when asking about OpenOffice problems on their users group, people running Debian have reported certain crashes and malfunctions.

The standard answer is, "Take it up on the Debian list, because we have no idea what they might have done to it in preparing it for Debian."

This has not come up just once or twice, but many times.

So, with several different tries under their belt, why can't the Debian people "get it right"?

This then holds for the Ubuntu people.

We can't just put together something, call it OpenOffice, or whatever, and toss it out onto the net and call it good.

If the OpenOffice people, all volunteers, can put together a program that works on Linux and Windows (yes, different OSs) and can be run on Debian if one takes the trouble (as I did myself, using alien on the RPMs, what's the problem?

No, I'm not going to go back to Mandriva or anything like that.  But if people just suck it up and accept software with bugs specially put in, even if done by accident, nothing improves.

Thanks,

JimW

---

### Post by az on 2006-02-23
[QUOTE=jimw]If the OpenOffice people, all volunteers, can put together a program that works on Linux and Windows (yes, different OSs) and can be run on Debian if one takes the trouble (as I did myself, using alien on the RPMs, what's the problem?

No, I'm not going to go back to Mandriva or anything like that.  But if people just suck it up and accept software with bugs specially put in, even if done by accident, nothing improves.

Thanks,

JimW[/QUOTE]

I am not completely sure, but I think the problem lies in the fact that java is proprietary.

It's a little complicated....

Java's licencing is such that if you chose to distribute Sun's Java, you are prohibited from distributing any other implementation of java.  This is evil.


There are free implementations of java that are getting better, but do not run all java code.  

Java is used in the build process of OpenOffice.org.  Although it is open source and licenced in a free-libre way, you cannot always build it if you are running the 100 per cent free-libre java implementations.  You need the Sun Java for some of the building of Oo.org.  Debian does not do that.  

Some say Debian have a stick up their ***.  Some say Sun are the problem.  It's your choice....  I, personally agree with debian.

Again, I am not sure that this is the issue with the thesaurus, specifically....

---

### Post by jimw on 2006-02-23
[QUOTE=azz]I am not completely sure, but I think the problem lies in the fact that java is proprietary.

It's a little complicated....

Java's licencing is such that if you chose to distribute Sun's Java, you are prohibited from distributing any other implementation of java.  This is evil.


There are free implementations of java that are getting better, but do not run all java code.  

Java is used in the build process of OpenOffice.org.  Although it is open source and licenced in a free-libre way, you cannot always build it if you are running the 100 per cent free-libre java implementations.  You need the Sun Java for some of the building of Oo.org.  Debian does not do that.  

Some say Debian have a stick up their ***.  Some say Sun are the problem.  It's your choice....  I, personally agree with debian.

Again, I am not sure that this is the issue with the thesaurus, specifically....[/QUOTE]


As you say, it may not have anything to do with the Thesaurus.  Probably doesn't, since I've been able to use the Thesaurus in other formulations of OO without having the JRE.

As I recall it, one of the few things you need to have the JRE for is to run the Database function, something which I continually plan to get around to, so I see to it that I have the JRE.

I suppose what I'd like to see is one of the Ubuntu "backporters" happen to look at this and send out a note indicating what did happen.  I understand that it was fixed later on, but by that time I'd already gone back to the version straight from the OO home site.

JimW

---

