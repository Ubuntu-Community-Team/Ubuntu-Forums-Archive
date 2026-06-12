---
title: "aMSN... Yeah, Again !!!"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Megadeth on 2006-07-20
Hey,

Well I bet this is coming back alot of time but, I searched and didn't found an answer. So, I'm really new to Linux and quite frankly, I'm a kind of impatient too LOL... 

There is an HowTO here that proposes a method of installing TCL/TK and aMSN without compiling anything (all .deb files). The problem is, TCL/TK are installed successfully but I'm not able to install aMSN (older or new versions). It says the dependencies is not satisfiable: tcltls.

Where did I've gone wrong ???


Thank you for your help and Ubuntu is just crazy :)

---

### Post by bluecherry on 2006-07-20
Have you tried Automatix?

This tool does all the hard work for you..

[www.getautomatix.com](www.getautomatix.com)

---

### Post by lzfy on 2006-07-20
Maybe a stupid question but have you installed Java? :-k Because I followed the same guide and it works perfect.

---

### Post by Skia_42 on 2006-07-20
Or you can simply install Kopete, it handles all of the main IM programs and it is easy to use. (AIM, Yahoo!, MSN)

---

### Post by ironfistchamp on 2006-07-20
isnt there an aMSN version in Synaptic. Thats where I got my old version from. What is the problem with installing from source. I managed to get the bleeding edge version working and it is amazing. I found this is the only IM client worth having.

Ironfistchamp

---

### Post by lepipir on 2006-07-20
or use gaim that has encryption ;-) as well. for encryption download the plugin.

---

### Post by AirRaven on 2006-07-20
I'll have to second the Kopete comment. 

I can't reccomend it enough. The newest 0.12.0 version (Newer than the one in the repos) is superb. Full MSN webcam support, for starters.

Although past all the cruft, I'd say Gaim's a better rounded client. But only if you don't want MSN webcam and themeing.

---

### Post by Megadeth on 2006-07-20
Thanks for suggesting Gaim, and I hate Kopete, but I just want aMSN ;)

I just need to know what is wrong. If I already installed the stuff, why does the installation says tcltls isn't installed...

---

### Post by ironfistchamp on 2006-07-20
Have you looked through Synaptic. That has a tcltls package on there.

---

### Post by Megadeth on 2006-07-20
> **ironfistchamp said:**
> Have you looked through Synaptic. That has a tcltls package on there.

Theres only the TCL and TK packages. No TCLTLS. Both TCL and TK packages are already installed.

---

### Post by ironfistchamp on 2006-07-20
I am on Dapper and I did a search for "tls" and it was near the bottom of the list. That is how I installed mine.

---

### Post by Megadeth on 2006-07-20
> **ironfistchamp said:**
> I am on Dapper and I did a search for "tls" and it was near the bottom of the list. That is how I installed mine.

If you could give me the exact name, that would be really appreciate :)

---

### Post by ironfistchamp on 2006-07-20
Open Synaptic, hit search and type "tls" no quotes. It is called tcltls down near the bottom. If I remember correctly when I did aMSN from source it installed tls itself if I was on my I386 one.

Why can't you do it that way its not too hard if u follow this guide 

[http://www.ubuntuforums.org/showthread.php?t=84765](http://www.ubuntuforums.org/showthread.php?t=84765)


Ironfistchamp

EDIT: That might not work anymore because the aMSN website has changed but the TCL TK bit would work. You can download the latest one from the site

---

### Post by Megadeth on 2006-07-20
> **ironfistchamp said:**
> Open Synaptic, hit search and type "tls" no quotes. **It is called tcltls down near the bottom**. If I remember correctly when I did aMSN from source it installed tls itself if I was on my I386 one.

Why can't you do it that way its not too hard if u follow this guide 

[http://www.ubuntuforums.org/showthread.php?t=84765](http://www.ubuntuforums.org/showthread.php?t=84765)


Ironfistchamp

EDIT: That might not work anymore because the aMSN website has changed but the TCL TK bit would work. You can download the latest one from the site

No such thing in my Synaptic...

---

### Post by ironfistchamp on 2006-07-20
Have you enabled all the repos? Here is what I have in my /etc/apt/sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb [http://www.fbriere.net/debian/dists/etch](http://www.fbriere.net/debian/dists/etch) misc/

It's there for me.

EDIT: Failing that is this what you want?  [http://sourceforge.net/project/showfiles.php?group_id=13248](http://sourceforge.net/project/showfiles.php?group_id=13248)

---

### Post by Megadeth on 2006-07-20
[[IMG]http://img109.imageshack.us/img109/2727/captureiw0.th.png[/IMG]](http://img109.imageshack.us/my.php?image=captureiw0.png)

---

### Post by ironfistchamp on 2006-07-20
Thats an awful lot shorter than my list
[IMG]http://www.freewebs.com/daniel_stamp/Screenshot%2DSynaptic%20Package%20Manager%20.png[/IMG]

---

### Post by Megadeth on 2006-07-20
Here's my source:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by ironfistchamp on 2006-07-20
Your universse and multiverse look to be commented out. Could eb the problem.

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

remove the # for each one and it should work. I think

---

### Post by Megadeth on 2006-07-20
It says I can't save because I don't have the right permissions (rights).

---

### Post by blitzd on 2006-07-20
Looks like you may need to add some repositories.

Try uncommenting these lines. Then run synaptic, hit reload and search again.
> **Megadeth said:**
> 
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

The tcltls package seems to be in the universe repo.

If that fails, I know that Automatix will install aMSN.

---

### Post by ironfistchamp on 2006-07-20
at the terminal type 

sudo gedit /etc/apt/sources.list

you will need to enter your password after that

EDIT: haha beat blitzd to it :p  sorry ill shut up now

---

### Post by blitzd on 2006-07-20
> **Megadeth said:**
> It says I can't save because I don't have the right permissions (rights).
Don't forget that you have to sudo to edit files that only root has write access to.

Something like this from a terminal window:

sudo gedit /etc/apt/sources.list

---

### Post by Megadeth on 2006-07-20
It worked :)

Thank you guys very much, I really appreciated the help :)

---

### Post by Megadeth on 2006-07-20
Now there's another problem. When I start aMSN, it just says it loads and then it dissapear...

---

### Post by ironfistchamp on 2006-07-20
Hehe np. Glad someone else is on aMSN now. 

Just say no to gaim. Na it's cool just not my cup of tea. 

I still haven't got webcam support both ways in aMSN though. I think I have found a driver for my webcam but the documentation is close to nil. Oh well such is life.

---

### Post by ironfistchamp on 2006-07-20
Yeh I had the same problem. Let me just access long term storage for an answer.


Hmm this is interesting. I can't really remember how I solved this. Maybe I didn't I can't exactly remember why I switched to compiling it myself. that could have been the reason. Maybe you should try that. And yes I am going to keep suggesting that :p

EDIT: What TCL and TK version are you running. Just out of curiosity

---

### Post by Megadeth on 2006-07-20
Well if I can't found out, I won't bust my butt for a software and just stick with Gaim...

---

### Post by ironfistchamp on 2006-07-20
I may write a little guide on how to get aMSN woking from CVS download. I found it remarkably easy even when I was totally green.

---

### Post by blitzd on 2006-07-20
You could try starting it from a console, it will probably give more details if there is an error.

---

### Post by ironfistchamp on 2006-07-20
Good point well made. Why didn't I think of that.

---

### Post by Megadeth on 2006-07-20
It works now... ;)

---

### Post by ironfistchamp on 2006-07-20
How did you get it to work?

---

