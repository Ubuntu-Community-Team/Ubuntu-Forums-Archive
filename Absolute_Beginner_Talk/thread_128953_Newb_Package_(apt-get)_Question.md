---
title: "Newb Package (apt-get) Question"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by mmoo9154 on 2006-02-12
I'm sure this is a simple problem, but I haven't been able to find any docs on the subject.

I've just installed a fresh instance of Breezy Badger 5.10 with the standard server install.  FYI, I'm a longtime Windows user, and fairly longtime Gentoo user.

I'm trying to install some fairly standard packages, but apt-get reports it can't find them.

For instance, Ethereal is extremely mainstream, and the Ubuntu packages database shows it's available.[1]

But, when I enter "sudo apt-get install ethereal", it reports "E: Couldn't find package ethereal".

What's the deal.  What do I have to set to allow apt-get to see the larger set of available packages?

-Mark

[1] [http://packages.ubuntu.com/breezy/net/ethereal](http://packages.ubuntu.com/breezy/net/ethereal)

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=mmoo9154]I'm sure this is a simple problem, but I haven't been able to find any docs on the subject.

I've just installed a fresh instance of Breezy Badger 5.10 with the standard server install.  FYI, I'm a longtime Windows user, and fairly longtime Gentoo user.

I'm trying to install some fairly standard packages, but apt-get reports it can't find them.

For instance, Ethereal is extremely mainstream, and the Ubuntu packages database shows it's available.[1]

But, when I enter "sudo apt-get install ethereal", it reports "E: Couldn't find package ethereal".

What's the deal.  What do I have to set to allow apt-get to see the larger set of available packages?

-Mark

[1] [http://packages.ubuntu.com/breezy/net/ethereal](http://packages.ubuntu.com/breezy/net/ethereal)[/QUOTE]
At the top of the page, do you see the part that says "[universe]"?  That means that it is part of the universe repository.  You probably just don't have that one enabled in your sources.list.

Here is a link to source-o-matic in case you want it to generate some new sources for you:
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by cjm5229 on 2006-02-12
Visit Ubuntu Repository Support. There is a lot of good advice in there on using Apt-get. and setting up repositories.

---

### Post by mmoo9154 on 2006-02-12
cwaldbieser, that was just the ticket.  I was too newb to realize I needed to uncomment the lines in /etc/apt/sources.list.

Did that, and now I'm working great.

Thx!

---

