---
title: "http://theli.free.fr  (what's this??)"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-23
Reading package lists... Done
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

This comes up now when i want to install stuff. apt-get update doesn't resove it. Someone know what theli.fr packages are? i don't know how this broke but can i fix it? 

thanks!

---

### Post by Perfect Storm on 2006-05-23
It's PLF (Penguin Liberation Front).
It's where you can get the non-GPL stuff like the codecs and dvdcss2.

How's your source list looks like?

---

### Post by dmizer on 2006-05-23
did you use automatix to install a bunch of different things?  if so, that will probably be your cause.  dunno why they're there, but i'm starting to like automatix less and less.

what version of ubuntu are you using?

---

### Post by sophtpaw on 2006-05-23
Okay, okay...

I'm sorry. Sould have given more relevant details. I am still in Breezy, and here's the sources list:
[http://paste.ubuntu-nl.org/14535](http://paste.ubuntu-nl.org/14535)

not too many days ago there was something else that went which i was told was not important and to simply disable:
#deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
#deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
which as you can see i've done. Probably not related. But maybe what caused that to break is the source of my current problem as well. Why would it all work and suddenly not? i.e first the koti.mbnet and then, now, theli.free.fr

By the way, no, i did not use Automatix to install. I did it all pretty much the old-fashioned way. Remember the ubuntuguide? :eek: 
just sudo apt-get all my codecs etc manually that way one by one. As i say worked too for quite a while until this week

Thanks for your help!

---

### Post by Perfect Storm on 2006-05-23
Try exchange

theli.free.fr 

with

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
#deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

---

### Post by sophtpaw on 2006-05-23
[QUOTE=Artificial Intelligence]Try exchange

theli.free.fr 

with

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
#deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free[/QUOTE]

Thx, A.I

Like this?
[http://paste.ubuntu-nl.org/14536](http://paste.ubuntu-nl.org/14536)

Just noticed: ## created by arniewinechanged - right at the bottom of my list. What is that about? is it right?

Thx!

---

### Post by Perfect Storm on 2006-05-23
```
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
```

my mistake

Also check out Ubuntu Source generator as another option: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by sophtpaw on 2006-05-23
[QUOTE=Artificial Intelligence]```
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
```

my mistake

Also check out Ubuntu Source generator as another option: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)[/QUOTE]


Thx, A.I


P.S

I've seen the source list before. Never felt too confident using it. Is it just a matter of ticking all the boxes where, in my case, Breeze is, and finally clicking on get sources list and then copying it over to ones /etc/apt/sources.lit ?
I've found going through Synaptic pretty simple. I basically like having all repositories (to the max) available so that i can as much as possible install any application i want from Synaptic(apt-get) 

I was just about to report another page of it not working, but you already noticed the wrong line. And now it works! So, it looks to be fixed again.
Yea, i'll check out the source generator

Thanks again,

--
sophtpaw

---

### Post by Perfect Storm on 2006-05-23
Well, if you don't use KDE you don't need the specific KDE source, other than that go for it.

---

### Post by sophtpaw on 2006-05-23
[QUOTE=Artificial Intelligence]Well, if you don't use KDE you don't need the specific KDE source, other than that go for it.[/QUOTE]

Cool,

I will try that on my next install, next month, when i hop over to Dapper:D

---

### Post by dmizer on 2006-05-23
[QUOTE=sophtpaw]Just noticed: ## created by arniewinechanged - right at the bottom of my list. What is that about? is it right?[/QUOTE]
arnie is the author of automatix.  so, as i suspected, your sources was modified by automatix.

---

### Post by sophtpaw on 2006-05-23
[QUOTE=dmizer]arnie is the author of automatix.  so, as i suspected, your sources was modified by automatix.[/QUOTE]
Yes, it would seem so. Although, i don't recall ever using automatix. I only recently heard about it at all. And as i say i used the old ubuntuguide to install

strange...

---

### Post by Perfect Storm on 2006-05-23
The only problem is if someone follows a guide which isn't the same version of their Ubuntu OS, it can be troublesome. Namely if the add the wrong repo stuff.

---

### Post by arnieboy on 2006-05-23
theli.free.fr is the repository for "listen media manager" . The author for listen no longer supports Breezy and hence the repository has been taken down.
Please delete the relevant lines from your sources.list and do an apt-get update

Automatix itself does not install these repositories any more.
They were removed a long time back.

The repositories can also be removed by using an up-to-date version of automatix and sticking to the sources.list provided by Automatix.

---

