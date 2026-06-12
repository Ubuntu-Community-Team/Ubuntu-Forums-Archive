---
title: "Manual installation, making an install CD, and info about packages."
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by imaginos on 2006-10-10
I posted this same message in Desktop forum, but now I think that this forum is better place for this topic.

-----------

I had installed (by using Add/Remove) several packages that I need for everyday use.
Ubuntu 6.06 stores backup of all those packages in:
/var/cache/apt/updates

Is it possible to put them in some other directory (or even CD) and make a script that will install them all. That would be very nice if I have to reinstall system or put those packeges on another computer. It will also save me a lot of time/money, and it would be nice to make a CD that will be recognized by Add/Remove program (or Synaptic?). BTW, is Add/Remove same as Synaptic, and if not so, what are the diferences?

What about dependecies? I see that a package installed vvie Add/Remove also brings some other .deb packages with itself. If I manually install a package like this:
dpkg package_name (assuming that package_name.deb file is present in current dir)

What will happen to dependencies if they are also in that directory? Is their installation going to be automatically invoked by installing package that is dependent of them, or I will have to start them one by one.


I would like to learn more about packages and installation procedure, in terms of what happens when an installation starts, structure and content od .deb files, etc?


Also, what Add/Remove actually does? Does it starts:
dpgk package
in the background? Where Ubuntu keeps information about installed programs?


Thank you.

---

### Post by imaginos on 2006-10-11
Ok, let me ask a shorter question:

I have packageA and packageB, and packageB is a dependency of packageA.

I downloaded packageA.deb and packageB.deb, and put them in the same directory.

I want to install packageA, but with only one command. In other words I need a program that will recongise all dependencies of packageA, search for them **in the same directory** (not on the internet!) and install them before installing packageA. 

How do I do that? app? app-get? aptitude?

Thanks!

---

